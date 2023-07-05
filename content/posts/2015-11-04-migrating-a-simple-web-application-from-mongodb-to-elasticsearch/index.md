---
title: Migrating a simple web application from MongoDB to Elasticsearch
author: Yanir Seroussi
type: post
date: 2015-11-04T03:53:18+00:00
url: /2015/11/04/migrating-a-simple-web-application-from-mongodb-to-elasticsearch/
cover:
  image: mongodb-to-elasticsearch.png
  responsiveImages: false
summary: Migrating BCRecommender from MongoDB to Elasticsearch made it possible to offer a richer search experience to users at a similar cost, among other benefits.
tags:
  - BCRecommender
  - DevOps
  - Elasticsearch
  - MongoDB
  - software engineering

---
<a href="http://www.bcrecommender.com" target="_blank" rel="noopener">Bandcamp Recommender (BCRecommender)</a> is a web application that serves music recommendations from <a href="http://bandcamp.com" target="_blank" rel="noopener">Bandcamp</a>. I recently switched BCRecommender's data store from <a href="https://www.mongodb.com/" target="_blank" rel="noopener">MongoDB</a> to <a href="https://www.elastic.co/products/elasticsearch" target="_blank" rel="noopener">Elasticsearch</a>. This has made it possible to offer a richer search experience to users at a similar cost. This post describes the migration process and discusses some of the advantages and disadvantages of using Elasticsearch instead of MongoDB.

## Motivation: Why swap MongoDB for Elasticsearch?

I've written a few posts in the past on BCRecommender's design and implementation. It is a fairly [simple application with two main components][1]: the backend worker that crawls data and generates recommendations in batch, and the webapp that serves the recommendations. Importantly, each of these components has its own data store, with the recommendations synced up from the worker to the webapp, and data like events and subscriptions synced down from the webapp to the worker. Recently, I [migrated the webapp component from Parse to DigitalOcean][2], replacing Parse's data store with MongoDB. Choosing MongoDB was meant to simplify the transition &ndash; Parse uses MongoDB behind the scenes, as does the backend worker. However, moving out of Parse's sandboxed environment freed me to choose any data store, and Elasticsearch seemed like a good candidate that would make it possible to expose advanced search capabilities to end users.

Advanced search means different things to different people. In BCRecommender's case what I had in mind was rather modest, at least for the initial stages. BCRecommender presents recommendations for two types of entities: fans and tralbums (tracks/albums). In both cases, the recommended items are tralbums. [When the key is a fan, the recommendations are tralbums that they may like, and when the key is a tralbum, the recommendations are similar tralbums][3]. Each tralbum has a title, an artist name, and a list of tags. Each fan has its Bandcamp username as a primary key, and a list of tags that is derived from the tralbums in the fan's collection. Originally, "searching" required users to either enter the exact username of a Bandcamp fan, or the exact Bandcamp link of a tralbum &ndash; not the best user experience! Indeed, I was tracking the search terms and found that many people were unsuccessfully trying to use unstructured queries. My idea of advanced search was to move away from the original key-value approach to full-text search that considers tags, titles, artists, and other fields that may get added later.

It was clear that while it may be possible to provide advanced search with MongoDB, it <a href="http://beletsky.net/2014/05/got-tired-of-mongodb-full-text.html" target="_blank" rel="noopener">wouldn't be a smooth ride</a>. While recent versions of MongoDB include support for full-text search, it isn't as feature-rich as Elasticsearch. For example, <a href="https://docs.mongodb.org/manual/core/index-text/#storage-requirements-and-performance-costs" target="_blank" rel="noopener">MongoDB text indices do not store phrases or information about the proximity of words in the documents</a>, making phrase queries run slowly unless the entire collection fits in memory. The names really say it all: MongoDB is a database with some search capabilities, and Elasticsearch is a search engine with some database capabilities. It <a href="https://www.compose.io/articles/mongoosastic-the-power-of-mongodb-and-elasticsearch-together/" target="_blank" rel="noopener">seems pretty common</a> to use MongoDB (or another database) as a data store and supply search through Elasticsearch, so I figured it isn't a bad idea to apply this pattern to BCRecommender.

It is worth noting that if BCRecommender were a for-profit project, I would probably use <a href="https://www.algolia.com" target="_blank" rel="noopener">Algolia</a> rather than Elasticsearch. My experience with Algolia on a different project has been excellent &ndash; they make it easy for you to get started, have great customer service, and deliver good and fast results with minimal development and operational effort. The two main disadvantages of Algolia are its price and the fact that it's a closed-source solution (<a href="https://www.quora.com/How-does-Elasticsearch-relate-and-or-compare-to-Algolias-Search-as-a-Service" target="_blank" rel="noopener">see further discussion on Quora</a>). At over two million records, the monthly cost of running Algolia for BCRecommender would be around US$649, which is more than what I'm willing to spend on this project. However, for a business this may be a reasonable cost because deploying and maintaining an Elasticsearch cluster may end up costing more. Nonetheless, many businesses use Elasticsearch successfully, which is why I have no doubt that it's a great choice for my use case &ndash; it just requires more work than Algolia to get up and running.

## Executing the migration plan

The plan for migrating the webapp from MongoDB to Elasticsearch was pretty simple:

  1. Read the <a href="https://www.elastic.co/guide/en/elasticsearch/guide/current/index.html" target="_blank" rel="noopener">Elasticsearch manual</a> to ensure it suits my needs
  2. Replace MongoDB with Elasticsearch without making any user-facing changes
  3. Expose full-text search to BCRecommender users
  4. Improve search performance based on user behaviour
  5. Implement more search features

**Reading the manual** is not something I do for every piece of technology I use (there are just too many tools out there these days), but for Elasticsearch it seemed to be worth the effort. I'm not done reading yet, but covering the material in the _Getting Started_ and _Search in Depth_ sections gave me enough information to complete steps 2 & 3. The main things I was worried about was Elasticsearch's performance as a database and how memory-hungry it'd be. Reading the manual allowed me to avoid some memory-use pitfalls and gave me insights on the way MongoDB and Elasticsearch compare ([see details below](#es-vs-mongo)).

**Switching from MongoDB to Elasticsearch as a simple database** was pretty straightforward. Both are document-based, so there were no changes required to the data models, but I did use the opportunity to fix some issues. For example, I changed the sitemap generation process from dynamic to static to avoid having to scroll through the entire dataset to fetch deep sitemap pages. To support BCRecommender's feature of browsing through random fans, I replaced <a href="http://bdadam.com/blog/finding-a-random-document-in-mongodb.html" target="_blank" rel="noopener">MongoDB's somewhat-hacky approach of returning random results</a> with <a href="https://www.elastic.co/guide/en/elasticsearch/guide/current/random-scoring.html" target="_blank" rel="noopener">Elasticsearch's cleaner method</a>. As the webapp is implemented in Python, I originally used the <a href="http://elasticsearch-dsl.readthedocs.org/en/latest/" target="_blank" rel="noopener">elasticsearch-dsl package</a>, but found it too hard to debug queries (e.g., figuring out how to rank results randomly was a bit of a nightmare). Instead, I ended up using the <a href="http://elasticsearch-py.readthedocs.org/en/latest/" target="_blank" rel="noopener">elasticsearch-py package</a>, which is only a thin wrapper around the Elasticsearch API. This approach yields code that doesn't look very Pythonic &ndash; rather than following the <a href="https://www.python.org/dev/peps/pep-0020/" target="_blank" rel="noopener">Zen of Python's</a> _flat is better than nested_ aphorism, the API follows the more Java-esque belief of _you can never have enough nesting_ (see image below for example). However, I prefer overly-nested structures that I can debug to flat code that doesn't work. I may try using the DSL again in the future, once I've gained more experience with Elasticsearch.

{{< figure src="elasticsearch-is-nesty.png" alt="elasticsearch is nesty" >}}

As mentioned, one of my worries was that I would have to increase the amount of memory allocated to the machine where Elasticsearch runs. Since BCRecommender is a fairly low-budget project, I'm willing to sacrifice high availability to save a bit on operational costs. Therefore, the webapp and its data store run on the same DigitalOcean instance, which is enough to happily serve the current amount of traffic (around one request per second). By default, Elasticsearch indexes all the fields, and even includes an extra indexed _all field that is a concatenation of all string fields in a document. While indexing everything may be convenient, it wasn't necessary for the first stage. Choosing the minimal index settings allowed me to keep using the same instance size as before (1GB RAM and 30GB SSD). In fact, due to the switch to static sitemaps and the removal of MongoDB's random attribute hack, fewer indexes were required after the change.

Once I had all the code converted and working on my local Vagrant environment, it was time to deploy. The deployment was fairly straightforward and required no downtime, as I simply provisioned a new instance and switched over the floating IP once it was all tested and ready to go. I monitored response time and memory use closely and everything seemed to be working just fine &ndash; similarly to MongoDB. After a week of monitoring, it was time to take the next step and enable advanced search.

**Enabling full-text search** is where things got interesting. This phase required adding a search result page (previously users were redirected to the queried page if it was found), and reindexing the data. For this phase, I tried to keep things as simple as possible, and just indexed the string fields (tags, artist, and title) using the standard analyser. I did some manual testing of search results based on common queries, and played a bit with improving <a href="https://en.wikipedia.org/wiki/Precision_and_recall" target="_blank" rel="noopener">precision and recall</a>. Perhaps the most important tweak was allowing an item's activity level to influence the ranking. For each tralbum, the activity level is the number of fans that have the tralbum in their collection, and for each fan, it is the size of the collection. For example, <a href="http://www.bcrecommender.com/search?q=amanda" target="_blank" rel="noopener">when searching for <em>amanda</em></a>, the top result is the fan with username _amanda_, followed by tralbums by the popular Amanda Palmer. Before I added the consideration of activity level, all tralbums and fans that contained the word _amanda_ had the same ranking.

{{< figure src="bcrecommender-search-amanda.png" alt="bcrecommender search for amanda" >}}

I deployed full-text search earlier this week, and so far it's looking pretty good. Elasticsearch seems to be coping well with having the same level of resources allocated as before, but it's still too early to tell if this is sustainable over time. Most importantly, users are finally seeing results when they enter unstructured queries, which increases their engagement and retention. Woohoo!

**Improving search performance based on user behaviour** is expected to be an ongoing effort. Despite having many ideas, I resisted the temptation of endless offline tinkering and opted to release a working search page quickly. With <a href="https://support.google.com/analytics/answer/1012264?hl=en" target="_blank" rel="noopener">Google Analytics now set up to track site search</a>, the plan is keep identifying gaps and tweak the search settings continuously. This will take a while, as the number of daily users is currently 200-300, and they don't all use site search.

**Implementing more search features** is another set of items on my to-do list that will be addressed over time. For example, it'd be great to have search auto-completion and a prettier result page. However, I have more ideas than time to implement them, and I'm not working on BCRecommender full-time. For now, I'm pretty happy with finally having the search function.

## Elasticsearch versus MongoDB: Key findings {#es-vs-mongo}

Comparisons between tools should always be taken with a grain of salt. General comparisons may not address features that are important for your specific use case, or may overemphasise aspects that you don't care about. In addition, actively developed tools are moving targets. Since I started the transition to Elasticsearch, version 2.0 has been released, and MongoDB 3.2 is expected very soon. The following list is derived from my experience and may not apply to you. You have been warned!

With the disclaimer out of the way, here are some of the advantages of Elasticsearch over MongoDB:

  * Better full-text search support (duh!).
  * Enforceable schemas and type validation (_note:_ some form of optional schema is expected in MongoDB 3.2).
  * All fields are indexed by default, making it easy to explore unstructured data without worrying about adding indices.
  * It appears that indexing is <a href="https://www.elastic.co/guide/en/elasticsearch/guide/current/translog.html" target="_blank" rel="noopener">implemented in a more efficient way that doesn't block the node</a>. Slowness due to indexing operations seems to be a common issue with MongoDB, even with background index creation.
  * It's possible to query multiple indices and types (same as MongoDB databases & collections, respectively) in the same query. This is a huge advantage in my case as it makes it possible to efficiently search both fans and tralbums in a single query.
  * <a href="https://www.elastic.co/guide/en/elasticsearch/reference/current/indices-aliases.html" target="_blank" rel="noopener">Index aliases</a> make it easy to change the indices without changing the application.
  * Multi-get by IDs returns results in the order they were requested. This is not the case with MongoDB, <a href="http://stackoverflow.com/questions/22797768/does-mongodbs-in-clause-guarantee-order/22800784#22800784" target="_blank" rel="noopener">where using $in doesn't have any guarantees on the returned documents' order</a>. It's easy to work around this issue, but it can be the source of subtle bugs. In my case, recommendations were unintentionally sorted in random order until I added an additional step to sort them correctly.
  * Built-in support for <a href="https://www.elastic.co/guide/en/elasticsearch/guide/current/random-scoring.html" target="_blank" rel="noopener">random scoring</a> (_note:_ random sampling will finally be available in MondoDB 3.2 &ndash; <a href="https://jira.mongodb.org/browse/SERVER-533" target="_blank" rel="noopener">the ticket for this has been open for 5 years</a>).
  * Built-in support for <a href="https://www.elastic.co/guide/en/elasticsearch/guide/current/most-fields.html" target="_blank" rel="noopener">multiple types of analysis on the same field</a>.

Some disadvantages of Elasticsearch in comparison to MongoDB are:

  * All fields are indexed by default, making it easy to run into memory issues. Adjusting these default settings is strongly recommended if you know how you're going to query the data.
  * Documents are immutable, so every update requires deleting the original document and re-inserting it (in practice, it seems like this isn't much of an issue).
  * Sorting results by a field requires reading all the field's values and sorting them in memory. The sorted results are cached, but this may cause issues if memory is too limited.

In conclusion, my experience with Elasticsearch has been mostly positive so far and I'm glad I've made the switch. I'm looking forward to taking further advantage of advanced search features to improve user experience on BCRecommender. New posts on the topic may be published in the future, so please subscribe to be notified when this happens. As always, I'm happy to receive feedback through the comments or [privately][4].

 [1]: https://yanirseroussi.com/2014/09/07/building-a-recommender-system-on-a-shoestring-budget/
 [2]: https://yanirseroussi.com/2015/07/31/goodbye-parse-com/
 [3]: https://yanirseroussi.com/2014/09/19/bandcamp-recommendation-and-discovery-algorithms/
 [4]: https://yanirseroussi.com/about/
