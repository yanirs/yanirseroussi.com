---
title: Bandcamp recommendation and discovery algorithms
author: Yanir Seroussi
type: post
date: 2014-09-19T14:26:55+00:00
url: /2014/09/19/bandcamp-recommendation-and-discovery-algorithms/
categories:
  - BCRecommender
tags:
  - bandcamp
  - data science
  - music
  - predictive modelling
  - recommender systems

---
<p class="intro-note">
This is the third part of a series of posts on my <a href="http://www.bcrecommender.com" target="_blank" rel="noopener">Bandcamp recommendations (BCRecommender)</a> project. Check out <a href="http://yanirseroussi.com/2014/08/30/building-a-bandcamp-recommender-system-part-1-motivation/">the first part</a> for the general motivation behind this project and <a href="http://yanirseroussi.com/2014/09/07/building-a-recommender-system-on-a-shoestring-budget/">the second part</a> for the system architecture.
</p>

The main goal of the BCRecommender project is to help me find music I like. This post discusses the algorithmic approaches I took towards that goal. I've kept the descriptions at a fairly high-level, without getting too much into the maths, as all recommendation algorithms essentially try to model simple intuition. Please leave a comment if you feel like something needs to be explained further. 

### Data & evaluation approach

The data was collected from publicly-indexable Bandcamp fan and track/album (aka tralbum) pages. For each fan, it consists of the tralbum IDs they bought or wishlisted. For each tralbum, the saved data includes the type (track/album), URL, title, artist name, and the tags (as assigned by the artist). 

At the moment, I have data for about 160K fans, 335K albums and 170K tracks. These fans have expressed their preference for tralbums through purchasing or wishlisting about 3.4M times. There are about 210K unique tags across the 505K tralbums, with the mean number of tags per tralbum being 7. These figures represent a fairly sparse dataset, which makes recommendation somewhat challenging. Perhaps this is why Bandcamp doesn't do much algorithmic recommendation. 

Before moving on to describe the recommendation approaches I played with, it is worth noting that at this stage, my way of evaluating the recommendations isn't very rigorous. If I can easily find new music that I like, I'm happy. As such, offline evaluation approaches (e.g., some form of cross-validation) are unlikely to correlate well with my goal, so I just didn't bother with them. Having more data would allow me to perform more rigorous online evaluation to see what makes other people happy with the recommendations. 

### Personalised recommendations with preferences (collaborative filtering)

My first crack at recommendation generation was using <a href="https://en.wikipedia.org/wiki/Collaborative_filtering" target="_blank" rel="noopener">collaborative filtering</a>. The broad idea behind collaborative filtering is using only the preference matrix to find patterns in the data, and generate recommendations accordingly. The preference matrix is defined to have a row for each user and a column for each item. Each matrix element value indicates the level of preference by the user for the item. To keep things simple, I used unary preference values, where the element that corresponds to user/fan _u_ and item/tralbum _i_ is set to 1 if the fan purchased or wishlisted the tralbum, or set to _missing_ otherwise. 

A simple example for collaborative filtering is in the following image, which was taken from the <a href="https://en.wikipedia.org/wiki/Collaborative_filtering" target="_blank" rel="noopener">Wikipedia article on the topic</a>. 

{{< figure src="collaborative-filtering.gif" alt="A simple collaborative filtering example" link="https://en.wikipedia.org/wiki/Collaborative_filtering" >}}

I used matrix factorisation as the collaborative filtering algorithm. This algorithm was a key part of <a href="https://datajobs.com/data-science-repo/Recommender-Systems-%5BNetflix%5D.pdf" target="_blank" rel="noopener">the winning team's solution to the Netflix competition</a>. Unsurprisingly, it didn't work that well. The key issue is that there are 160K * (335K + 170K) = 80.8B possible preferences in the dataset, but only 3.4M (0.004%) preferences are given. What matrix factorisation tries to do is to predict the remaining 99.996% of preferences based on the tiny percentage of given data. This just didn't yield any music recommendations I liked, even when I made the matrix denser by dropping fans and tralbums with few preferences. Therefore, I moved on to employing an algorithm that can use more data &ndash; the tags. 

### Personalised recommendations with tags and preferences (collaborative filtering and content-based hybrid)

Using data about the items is referred to as <a href="https://en.wikipedia.org/wiki/Recommender_system#Content-based_filtering" target="_blank" rel="noopener">content-based recommendation</a> in the literature. In the Bandcamp recommender case, the content data that is most easy to use is the tags that artists assign to their work. The idea is to build a profile for each fan based on tags for their tralbums, and recommend tralbums with tags that match the fan's profile. 

As mentioned above, the dataset contains 210K unique tags for 505K tralbums, which means that this representation of the dataset is also rather sparse. One obvious way of making it denser is by dropping rare tags. I also "tagged" each tralbum with a fan's username if that fan purchased or wishlisted the tralbum. In addition to yielding a richer tralbum representation, this approach makes the recommendations likely to be less obvious than those based only on tags. For example, all tralbums tagged with _rock_ are likely to be rock albums, but tralbums tagged with _yanir_ are <a href="https://bandcamp.com/yanir" target="_blank" rel="noopener">somewhat more varied</a>. 

To make the tralbum representation denser I used the <a href="http://radimrehurek.com/gensim/wiki.html#latent-dirichlet-allocation" target="_blank" rel="noopener">latent Dirichlet allocation (LDA) implementation from the excellent gensim library</a>. LDA assumes that there's a fixed number of _topics_ (distributions over tags, i.e., weighted lists of tags), and that every tralbum's tags are generated from its topics. In practice, this _magically_ yields clusters of tags and tralbums that can be used to generate recommendations. For example, the following word cloud presents the top tags in one cluster, which is focused on psychedelic-progressive rock. Each tralbum is assigned a probability of being generated from this cluster. This means that each tralbum is now represented as a probability distribution over a fixed number of topics &ndash; much denser than the raw tag data. 

{{< figure src="psychedelic-progressive-rock-tag-cloud.png" alt="psychedelic-progressive-rock tag cloud" >}}

Using LDA for generating recommendations is straightforward, as each fan can be represented as the concatenation of the tags assigned to their tralbums, together with their own user tag. This representation is then converted to a topic distribution, which is compared to all the tralbums to yield the most similar ones. 

This approach yielded much better results than collaborative filtering. I actually found albums I like and made some purchases, more than just the three that are annotated on <a href="https://bandcamp.com/yanir" target="_blank" rel="noopener">my fan page</a> (I didn't want to be too spammy). Woohoo! 

However, the problem with this approach is that it doesn't take my mood into account, as it is based on my entire profile. To address this, I introduced similar music and cluster-based discovery. 

### Beyond static personalisation: similar music and cluster-based discovery

It is easy to see that the LDA-based tralbum representation makes it straightforward to calculate similarity between tralbums, and also explore tralbums that belong to the same topic/cluster. Adding this functionality to BCRecommender means that users can explore similar tralbums to a tralbum or a cluster in the style that they are interested in _right now_ &ndash; based on their mood. Implementing these features helped me find more music I like, so again, I'm happy. 

Tweaking the similarity algorithms is still a work in progress, as is finding a scalable way to generate useful <a href="http://www.bcrecommender.com/spotlights" target="_blank" rel="noopener">cluster/spotlight pages</a>. However, my focus now (in the time that I can allocate to working on this project) is on getting some people using it and iterate following their feedback. 

### Future extensions

It would be awesome to make BCRecommender's discovery process smoother. For example, it'd be fairly straightforward to just stream all the recommendations rather than making users click album by album (like Pandora, Spotify, etc.). Iterating on the above approaches to improve the user experience is also likely to yield good results. 

However, as mentioned above, my current focus is on getting more people to use BCRecommender. While the target audience is rather small, it doesn't matter because I'm not trying to make money from this project. I am certain that many fans would discover new music using the website. At this stage, I just need to get them to visit, which is something that I will write about in future posts.
