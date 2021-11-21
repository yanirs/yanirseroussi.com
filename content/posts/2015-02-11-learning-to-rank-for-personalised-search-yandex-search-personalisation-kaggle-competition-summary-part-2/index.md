---
title: Learning to rank for personalised search (Yandex Search Personalisation – Kaggle Competition Summary – Part 2)
author: Yanir Seroussi
type: post
date: 2015-02-11T06:34:17+00:00
url: /2015/02/11/learning-to-rank-for-personalised-search-yandex-search-personalisation-kaggle-competition-summary-part-2/
cover:
  image: rating.png
  responsiveImages: false
tags:
  - data science
  - gradient boosting
  - Kaggle
  - Kaggle competition
  - machine learning
  - predictive modelling
  - search engine optimisation

---
This is the second and last post summarising my team's solution for the <a href="https://www.kaggle.com/c/yandex-personalized-web-search-challenge" target="_blank" rel="noopener">Yandex search personalisation Kaggle competition</a>. [See the first post][1] for a summary of the dataset, evaluation approach, and some thoughts about search engine optimisation and privacy. This post discusses the algorithms and features we used.

To quickly recap the [first post][1], Yandex released a 16GB dataset of query & click logs. The goal of the competition was to use this data to rerank query results such that the more relevant results appear before less relevant results. Relevance is determined by time spent on each clicked result (non-clicked results are deemed irrelevant), and overall performance is scored using the <a href="https://en.wikipedia.org/wiki/Discounted_cumulative_gain" target="_blank" rel="noopener">normalised discounted cumulative gain (NDCG) measure</a>. No data about the content of sites or queries was given &ndash; each query in the dataset is a list of token IDs and each result is a (url ID, domain ID) pair.

### First steps: memory-based heuristics

My initial approach wasn't very exciting: it involved iterating through the data, summarising it in one way or another, and assigning new relevance scores to each (user, session, query) combination. In this early stage I also implemented an offline validation framework, [which is an important part of every Kaggle competition][2]: in this case I simply set aside the last three days of data for local testing, because the test dataset that was used for the leaderboard consisted of three days of log data.

Somewhat surprisingly, my heuristics worked quite well and put me in a top-10 position on the leaderboard. It seems like the barrier of entry for this competition was higher than for other Kaggle competitions due to the size of the data and the fact that it wasn't given as preprocessed feature vectors. This was evident from questions on the forum, where people noted that they were having trouble downloading and looking at the data.

The heuristic models that worked well included:

  * Reranking based on mean relevance (this just swapped positions 9 & 10, probably because users are more likely to click the last result)
  * Reranking based on mean relevance for (query, url) and (query, domain) pairs (non-personalised improvements)
  * Downranking urls observed previously in a session

Each one of the heuristic models was set to output relevance scores. The models were then ensembled by simply summing the relevance scores.

Then, I started playing with a <a href="https://en.wikipedia.org/wiki/Collaborative_filtering" target="_blank" rel="noopener">collaborative-filtering</a>-inspired matrix factorisation model for predicting relevance, which didn't work too well. At around that time, I got too busy with other stuff and decided to quit while I'm ahead.

### Getting more serious with some team work and LambdaMART

A few weeks after quitting, I somehow volunteered to organise Kaggle teams for newbies at the <a href="http://www.meetup.com/Data-Science-Sydney/" target="_blank" rel="noopener">Sydney Data Science Meetup group</a>. At that point I was joined by my teammates, which served as a good motivation to do more stuff.

The first thing we tried was another heuristic model I read about in one of the <a href="https://www.kaggle.com/c/yandex-personalized-web-search-challenge/details/related-papers" target="_blank" rel="noopener">papers suggested by the organisers</a>: just reranking based on the fact that people often repeat queries as a navigational aid (e.g., search for Facebook and click Facebook). Combined in a simple linear model with the other heuristics, this put us at #4. Too easy 🙂

With all the new motivation, it was time to read more papers and start doing things properly. We ended up using <a href="http://sourceforge.net/p/lemur/wiki/RankLib/" target="_blank" rel="noopener">Ranklib's LambdaMART implementation</a> as one of our main models, and also used LambdaMART to combine the various models (the old heuristics still helped the overall score, as did the matrix factorisation model).

Using LambdaMART made it possible to directly optimise the NDCG measure, turning the key problem into feature engineering, i.e., finding good features to feed into the model. Explaining how LambdaMART works is beyond the scope of this post (<a href="http://research.microsoft.com/pubs/132652/MSR-TR-2010-82.pdf" target="_blank" rel="noopener">see this paper for an in-depth discussion</a>), but the basic idea (which is also shared by other <a href="https://en.wikipedia.org/wiki/Learning_to_rank" target="_blank" rel="noopener">learning to rank</a> algorithms) is that rather than trying to solve the hard problem of predicting relevance (i.e., a regression problem), the algorithm tries to predict the ranking that yields the best results according to a user-chosen measure.

We tried many features for the LambdaMART model, but after feature selection (using a method learned from <a href="http://anotherdataminingblog.blogspot.com.au/2013/10/techniques-to-improve-accuracy-of-your_17.html" target="_blank" rel="noopener">Phil Brierley's talk</a>) the best features turned out to be:

  * percentage\_recurrent\_term_ids: percentage of term IDs from the test query that appeared previously in the session &#8212; indicates if this query refines previous queries
  * query\_mean\_ndcg: historical NDCG for this query &#8212; indicates how satisfied people are with the results of this query. Interestingly, we also tried query click entropy, but it performed worse. Probably because we're optimising the NDCG rather than click-through rate.
  * query\_num\_unique_serps: how many different result pages were shown for this query
  * query\_mean\_result\_dwell\_time: how much time on average people spend per result for this query
  * user\_mean\_ndcg: like query\_mean\_ndcg, but for users &#8212; a low NDCG indicates that this user is likely to be dissatisfied with the results. As for query\_mean\_ndcg, adding this feature yielded better results than using the user's click entropy.
  * user\_num\_click\_actions\_with\_relevance\_0: over the history of this user, how many of their clicks had relevance 0 (i.e., short dwell time). Interestingly, user\_num\_click\_actions\_with\_relevance\_1 and user\_num\_click\_actions\_with\_relevance\_2 were found to be less useful.
  * user\_num\_query_actions: number of queries performed by the user
  * rank: the original rank, as assigned by Yandex
  * previous\_query\_url\_relevance\_in_session: modelling repeated results within a session, e.g., if a (query, url) pair was already found irrelevant in this session, the user may not want to see it again
  * previous\_url\_relevance\_in\_session: the same as previous\_query\_url\_relevance\_in_session, but for a url regardless of the query
  * user\_query\_url\_relevance\_sum: over the entire history of the user, not just the session
  * user\_normalised\_rank_relevance: how relevant does the user usually find this rank? The idea is that some people are more likely to go through all the results than others
  * query\_url\_click\_probability: estimated simply as num\_query\_url\_clicks / num\_query\_url_occurrences (across all the users)
  * average\_time\_on_page: how much time people spend on this url on average

Our best submission ended up placing us at the 9th place (out of 194 teams), which is respectable. Things got a bit more interesting towards the end of the competition &ndash; if we had used the original heuristic model that put at #4 early on, we would have finished 18th.

### Conclusion

I really enjoyed this competition. The data was well-organised and well-defined, which is not something you get in every competition (or in "real life"). Its size did present some challenges, but we stuck to using flat files and some preprocessing and other tricks to speed things up (e.g., I got to use <a href="http://cython.org/" target="_blank" rel="noopener">Cython</a> for the first time). It was good to learn how learning to rank algorithms work and get some insights on search personalisation. As is often the case with Kaggle competitions, this was time well spent.

 [1]: https://yanirseroussi.com/2015/01/29/is-thinking-like-a-search-engine-possible-yandex-search-personalisation-kaggle-competition-summary-part-1/ "Is thinking like a search engine possible? (Yandex search personalisation – Kaggle competition summary – part 1)"
 [2]: https://yanirseroussi.com/2014/08/24/how-to-almost-win-kaggle-competitions/ "How to (almost) win Kaggle competitions"
