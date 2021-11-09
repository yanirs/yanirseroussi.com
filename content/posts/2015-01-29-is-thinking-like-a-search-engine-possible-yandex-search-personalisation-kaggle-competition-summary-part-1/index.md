---
title: Is thinking like a search engine possible? (Yandex search personalisation – Kaggle competition summary – part 1)
author: Yanir Seroussi
type: post
date: 2015-01-29T10:37:39+00:00
url: /2015/01/29/is-thinking-like-a-search-engine-possible-yandex-search-personalisation-kaggle-competition-summary-part-1/
cover:
  image: artificial-intelligence.jpg
tags:
  - data science
  - Kaggle
  - Kaggle competition
  - machine learning
  - predictive modelling
  - search engine optimisation
 
---
About a year ago, I participated in the <a href="https://www.kaggle.com/c/yandex-personalized-web-search-challenge" target="_blank" rel="noopener">Yandex search personalisation Kaggle competition</a>. I started off as a solo competitor, and then added a few Kaggle newbies to the team as part of a program I was running for the <a href="http://www.meetup.com/Data-Science-Sydney/" target="_blank" rel="noopener">Sydney Data Science Meetup</a>. My team hasn't done too badly, finishing 9th out of 194 teams. As is usually the case with Kaggle competitions, the most valuable part was the lessons learned from the experience. In this case, the lessons go beyond the usual data science skills, and include some insights that are relevant to search engine optimisation (SEO) and privacy. This post describes the competition setup and covers the more general insights. A follow-up post will cover the technical side of our approach.

### The data

Yandex is the leading search engine in Russia. For the competition, they <a href="https://www.kaggle.com/c/yandex-personalized-web-search-challenge/data" target="_blank" rel="noopener">supplied a dataset</a> that consists of log data of search activity from a single large city, which represents one month of search activity (excluding popular queries). In total, the dataset contains about 21M unique queries, 700M unique urls, 6M unique users, and 35M search sessions. This is a relatively-big dataset for a Kaggle competition (the training file is about 16GB uncompressed), but it's really rather small in comparison to Yandex's overall search volume and tiny compared to what Google handles.

The data was anonymised, so a sample looks like this (see <a href="https://www.kaggle.com/c/yandex-personalized-web-search-challenge/details/logs-format" target="_blank" rel="noopener">full description of the data format</a> &#8211; the example and its description are taken from there):

> ```text
> 744899 M 23 123123123
> 744899 0 Q 0 192902 4857,3847,2939 632428,2384 309585,28374 319567,38724 6547,28744 20264,2332 3094446,34535 90,21 841,231 8344,2342 119571,45767
> 744899 1403 C 0 632428
> ```
>
> These records describe the session (<code>SessionID</code> = 744899) of the user with <code>USERID</code> 123123123, performed on the 23rd day of the dataset. The user submitted the query with <code>QUERYID</code> 192902, which contains terms with <code>TermIDs</code> 4857,3847,2939. The URL with <code>URLID</code> 632428 placed on the domain <code>DomainID</code> 2384 is the top result on the corresponding SERP. 1403 units of time after beginning of the session the user clicked on the result with <code>URLID</code> 632428 (ranked first in the list).

While this may seem daunting at first, the data is actually quite simple. For each search session, we know the user, the queries they've made, which URLs and domains were returned in the SERP (search engine result page), which results they've clicked, and at what point in time the queries and clicks happened.

### Goal and evaluation

The goal of the competition is to rerank the results in each SERP such that the highest-ranking documents are those that the user would find most relevant. As the name of the competition suggests, personalising the results is key, but non-personalised approaches were also welcome (and actually worked quite well).

One question that arises is how to tell from this data which results the user finds relevant. In this competition, the results were labelled as either irrelevant (0), relevant (1), or highly relevant (2). Relevance is a function of clicks and dwell time, where dwell time is the time spent on the result (determined by the time that passed until the next query or click). Irrelevant results are ones that weren't clicked, or those for which the dwell time is less than 50 (the time unit is left unspecified). Relevant results are those that were clicked and have dwell time of 50 to 399. Highly relevant results have dwell time of at least 400, or were clicked as the last action in the session (i.e., it is assumed the user finished the session satisfied with the results rather than left because they couldn't find what they were looking for).

This approach to determining relevance has some obvious flaws, but <a href="https://www.kaggle.com/c/yandex-personalized-web-search-challenge/details/evaluation" target="_blank" rel="noopener">it apparently correlates well with actual user satisfaction with search results</a>.

Given the above definition of relevance, one can quantify how well a reranking method improves the relevance of the results. For this competition, the organisers chose the <a href="https://en.wikipedia.org/wiki/Discounted_cumulative_gain" target="_blank" rel="noopener">normalised discounted cumulative gain (NDCG) measure</a>, which is a fancy name for a measure that, in the words of Wikipedia, encodes the assumptions that:

  * Highly relevant documents are more useful when appearing earlier in a search engine result list (have higher ranks)
  * Highly relevant documents are more useful than marginally relevant documents, which are in turn more useful than irrelevant documents.

### SEO insights and other thoughts

A key insight that is relevant to SEO and privacy, is that even without considering browser-based tracking and tools like Google Analytics (which may or may not be used by Google to rerank search results), search engines can infer a lot about user behaviour on other sites, just based on user interaction with the SERP. So if your users bounce quickly because your website is slow to load or ranks highly for irrelevant queries, the search engine can know that, and will probably penalise you accordingly.

This works both ways, though, and is evident even on <a href="http://donttrack.us/" target="_blank" rel="noopener">search engines that don't track personal information</a>. Just try searching for "f" or "fa" or "fac" using DuckDuckGo, Google, Bing, Yahoo, or even Yandex. Facebook will be one of the top results (most often the first one), probably just because people tend to search for or visit Facebook after searching for one of those terms by mistake. So if your website ranks poorly for a term for which it should rank well, and your users behave accordingly (because, for example, they're searching for your website specifically), you may magically end up with better ranking without any changes to inbound links or to your site.

Another thing that is demonstrated by this competition's dataset is just how much data search engines consider when determining ranking. The dataset is just a sample of logs for one city for one month. I don't like throwing the words "big data" around, but the full volume of data is pretty big. Too big for anyone to grasp and fully understand how exactly search engines work, and this includes the people who build them. What's worth keeping in mind is that for all major search engines, the user is the product that they sell to advertisers, so keeping the users happy is key. Any changes made to the underlying algorithms are usually done with the end-user in mind, because not making such changes may kill the search engine (remember AltaVista?). Further, personalisation means that <a href="http://dontbubble.us/" target="_blank" rel="noopener">different users see different results for the same query</a>. So my feeling is that it's somewhat futile to do any SEO beyond making the website understandable by search engines, acquiring legitimate links, and just building a website that people would want to visit.

### Next steps

With those thoughts out of the way, it's time to describe the way we addressed the challenge. This is covered in the next post, [Learning to rank for personalised search][1].

 [1]: http://yanirseroussi.com/2015/02/11/learning-to-rank-for-personalised-search-yandex-search-personalisation-kaggle-competition-summary-part-2/ "Learning to rank for personalised search (Yandex Search Personalisation – Kaggle Competition Summary – Part 2)"
