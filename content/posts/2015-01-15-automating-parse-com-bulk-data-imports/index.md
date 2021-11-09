---
title: Automating Parse.com bulk data imports
author: Yanir Seroussi
type: post
date: 2015-01-15T04:41:16+00:00
url: /2015/01/15/automating-parse-com-bulk-data-imports/
cover:
  image: parse-hosting.jpg
tags:
  - DevOps
  - parse.com
  - PhantomJS
  - software engineering

---
<a href="http://parse.com" target="_blank" rel="noopener">Parse</a> is a great backend-as-a-service (BaaS) product. It removes much of the hassle involved in backend devops with its web hosting service, SDKs for all the major mobile platforms, and a generous free tier. Parse does have its share of flaws, including various reliability issues (which seem to be getting rarer), and limitations on what you can do (which is reasonable price to pay for working within a sandboxed environment). One such limitation is the lack of APIs to perform bulk data imports. This post introduces my workaround for this limitation (tl;dr: it's a <a href="https://gist.github.com/yanirs/eddedf152f42c1ee02b2" target="_blank" rel="noopener">PhantomJS script</a>).

**Update:** The script no longer works due to changes to Parse's website. I won't be fixing it since [I've migrated my projects off the platform][1]. If you fix it, let me know and I'll post a link to the updated script here.

I use Parse for two of my projects: <a title="Bandcamp recommendations based on your fan profile" href="http://www.bcrecommender.com" target="_blank" rel="noopener">BCRecommender</a> and Price Dingo. In both cases, some of the data is [generated outside Parse by a Python backend][2]. Doing all the data processing within Parse is not a viable option, so a solution for importing this data into Parse is required.

My original solution for data import was using the Parse REST API via <a href="https://github.com/dgrtwo/ParsePy" target="_blank" rel="noopener">ParsePy</a>. The problem with this solution is that Parse billing is done on a requests/second basis. The free tier includes 30 requests/second, so importing BCRecommender's ~million objects takes about nine hours when operating at maximum capacity. However, operating at maximum capacity causes other client requests to be dropped (i.e., real users suffer). Hence, some sort of rate limiting is required, which makes the sync process take even longer.

I thought that using <a href="https://parse.com/docs/rest#objects-batch" target="_blank" rel="noopener">batch requests</a> would speed up the process, but it actually slowed it down! This is because batch requests are billed according to the number of sub-requests, so making even one successful batch request per second with the maximum number of sub-requests (50) causes more requests to be dropped. I implemented some code to retry failed requests, but the whole process was just too brittle.

A few months ago I discovered that Parse supports <a href="https://parse.com/docs/data#data-import" target="_blank" rel="noopener">bulk data import via the web interface</a> (with no API support). This feature comes with the caveat that existing collections can't be updated: a new collection must be created. This is actually a good thing, as it essentially makes the collections immutable. And <a href="http://en.wikipedia.org/wiki/Immutable_object" target="_blank" rel="noopener">immutability makes many things easier</a>.

BCRecommender data gets updated once a month, so I was happy with manually importing the data via the web interface. As a price comparison engine, Price Dingo's data changes more frequently, so manual updates are out of the question. For Price Dingo to be hosted on Parse, I had to find a way to automate bulk imports. Some people suggest <a href="https://www.parse.com/questions/programmatically-create-classes-import-json" target="_blank" rel="noopener">emulating the requests made by the web interface</a>, but this requires relying on hardcoded cookie and CSRF token data, which may change at any time. A more robust solution would be to scriptify the manual actions, but how? <a href="http://phantomjs.org/" target="_blank" rel="noopener">PhantomJS</a>, that's how.

I ended up implementing a PhantomJS script that logs in as the user and uploads a dump to a given collection. This script is <a href="https://gist.github.com/yanirs/eddedf152f42c1ee02b2" target="_blank" rel="noopener">available on GitHub Gist</a>. To run it, simply install PhantomJS and run:

```bash
$ phantomjs --ssl-protocol any \
    import-parse-class.js <configFile> <dumpFile> <collectionName>
```

<a href="https://gist.github.com/yanirs/eddedf152f42c1ee02b2" target="_blank" rel="noopener">See the script's source</a> for a detailed explanation of the command-line arguments.

It is worth noting that the script doesn't do any post-upload verification on the collection. This is done by an extra bit of Python code that verifies that the collection has the expected number of objects, and tries to query the collection sorted by all the keys that are supposed to be indexed (for large collections, it takes Parse a while to index all the fields, which may result in timeouts). Once these conditions are fulfilled, the Parse hosting code is updated to point to the new collection. For security, I added a bot user that has access only to the Parse app that it needs to update. Unlike the root user, this bot user can't delete the app. As the config file contains the bot's password, it should be encrypted and stored in a safe place (<a href="https://parse.com/docs/data#security" target="_blank" rel="noopener">like the Parse master key</a>).

That's it! I hope that other people would find this solution useful. Any suggestions/comments/issues are very welcome.

<small><br /> Image source: <a href="http://blog.parse.com/2013/05/07/goodbye-web-servers-hello-parse-hosting/" target="_blank" rel="noopener">Parse Blog</a>.<br /> </small>

 [1]: https://yanirseroussi.com/2015/07/31/goodbye-parse-com/
 [2]: https://yanirseroussi.com/2014/09/07/building-a-recommender-system-on-a-shoestring-budget/ "Building a recommender system on a shoestring budget (or: BCRecommender part 2 – general system layout)"
