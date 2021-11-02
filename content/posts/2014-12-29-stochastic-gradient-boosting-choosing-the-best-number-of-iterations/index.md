---
title: 'Stochastic Gradient Boosting: Choosing the Best Number of Iterations'
author: Yanir Seroussi
type: post
date: 2014-12-29T02:30:06+00:00
url: /2014/12/29/stochastic-gradient-boosting-choosing-the-best-number-of-iterations/
categories:
  - Data science
tags:
  - data science
  - gradient boosting
  - machine learning
  - predictive modelling
  - scikit-learn

---
In my [summary of the Kaggle bulldozer price forecasting competition][1], I mentioned that part of my solution was based on stochastic gradient boosting. To reduce runtime, the number of boosting iterations was set by minimising the loss on the out-of-bag (OOB) samples, skipping trees where samples are in-bag. This approach was motivated <a href="https://github.com/scikit-learn/scikit-learn/issues/1802" target="_blank" rel="noopener">by a bug in scikit-learn</a>, where the OOB loss estimate was calculated on the in-bag samples, meaning that it always improved (and thus was useless for the purpose of setting the number of iterations).

The bug in scikit-learn was <a href="https://github.com/scikit-learn/scikit-learn/pull/2188" target="_blank" rel="noopener">fixed</a> by porting the solution used in <a href="http://cran.r-project.org/web/packages/gbm/index.html" target="_blank" rel="noopener">R's GBM package</a>, where the number of iterations is estimated by minimising the improvement on the OOB samples in each boosting iteration. This approach is known to <a href="http://cran.open-source-solution.org/web/packages/gbm/vignettes/gbm.pdf" target="_blank" rel="noopener">underestimate the number of required iterations</a>, which means that it's not very useful in practice. This underestimation may be due to the fact that the GBM method is partly estimated on in-bag samples, as the OOB samples for the Nth iteration are likely to have been in-bag in previous iterations.

I was curious about how my approach compares to the GBM method. Preliminary results on the <a href="http://scikit-learn.org/stable/auto_examples/ensemble/plot_gradient_boosting_oob.html" target="_blank" rel="noopener">toy dataset from scikit-learn's documentation</a> looked promising:

{{< figure src="gradient-boosting-out-of-bag-experiment-toy-dataset.png" alt="Gradient Boosting out of bag experiment (toy dataset)" >}}

My approach (TSO) beat both 5-fold cross-validation (CV) and the GBM/scikit-learn method (SKO), as TSO obtains its minimum at the closest number of iterations to the test set's (T) optimal value.

The next step in testing TSO's viability was to rerun <a href="http://cran.open-source-solution.org/web/packages/gbm/vignettes/gbm.pdf" target="_blank" rel="noopener">Ridgeway's experiments from Section 3.3 of the GBM documentation</a> (<a href="https://github.com/harrysouthworth/gbm/blob/master/demo/OOB-reps.R" target="_blank" rel="noopener">R code here</a>). I used the same 12 UCI datasets that Ridgeway used, running 5&#215;2 cross-validation on each one. For each dataset, the score was obtained by dividing the mean loss of the best method on the dataset by the loss of each method. Hence, all scores are between 0.0 and 1.0, with the best score being 1.0. The following figure summarises the results on the 12 datasets. 

{{< figure src="gradient-boosting-out-of-bag-experiments-uci-datasets" alt="Gradient Boosting out of bag experiment (UCI datasets)" >}}

The following table shows the raw data that was used to produce the figure. 

Dataset        | CV     | SKO    | TSO
---------------|--------|--------|--------
creditrating   | 0.9962 | 0.9771 | 1
breastcancer   | 1      | 0.6675 | 0.4869
mushrooms      | 0.9588 | 0.9963 | 1
abalone        | 1      | 0.9754 | 0.9963
ionosphere     | 0.9919 | 1      | 0.8129
diabetes       | 1      | 0.9869 | 0.9985
autoprices     | 1      | 0.9565 | 0.5839
autompg        | 1      | 0.8753 | 0.9948
bostonhousing  | 1      | 0.8299 | 0.5412
haberman       | 1      | 0.9793 | 0.9266
cpuperformance | 0.9934 | 0.9160 | 1
adult          | 1      | 0.9824 | 0.9991

The main finding is that CV remains the most reliable approach. Even when CV is not the best-performing method, it's not much worse than the best method (this is in line with Ridgeway's findings). TSO yielded the best results on 3/12 of the datasets, and beat SKO 7/12 times. However, TSO's results are the most variant of the three methods: when it fails, it often yields very poor results.

In conclusion, stick to cross-validation for the best results. It's more computationally intensive than SKO and TSO, but can be parallelised. I still think that there may be a way to avoid cross-validation, perhaps by extending SKO/TSO in more intelligent ways (see some interesting ideas by Eugene Dubossarsky <a href="http://cavemoosum.blogspot.com.au/2014/02/cross-validation-is-over-long-live.html" target="_blank" rel="noopener">here</a> and <a href="http://cavemoosum.blogspot.com.au/2014/03/cross-validation-is-not-quite-kaput-but.html" target="_blank" rel="noopener">here</a>). Any comments/ideas are very welcome.

 [1]: http://yanirseroussi.com/2014/11/19/fitting-noise-forecasting-the-sale-price-of-bulldozers-kaggle-competition-summary/ "Fitting noise: Forecasting the sale price of bulldozers (Kaggle competition summary)"
