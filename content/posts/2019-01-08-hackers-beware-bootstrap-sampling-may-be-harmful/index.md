---
title: 'Hackers beware: Bootstrap sampling may be harmful'
author: Yanir Seroussi
type: post
date: 2019-01-07T21:07:56+00:00
url: /2019/01/08/hackers-beware-bootstrap-sampling-may-be-harmful/
cover:
  relative: true
  image: warning-signs.jpg
summary: Bootstrap sampling has been promoted as an easy way of modelling uncertainty to hackers without much statistical knowledge. But things aren't that simple.
tags:
  - bootstrapping
  - data science
  - hackers
  - software engineering
  - statistics

---
[Bootstrap sampling techniques][1] are very appealing, as they don't require knowing much about statistics and opaque formulas. Instead, all one needs to do is resample the given data many times, and calculate the desired statistics. Therefore, bootstrapping has been promoted as an easy way of modelling uncertainty to hackers who don't have much statistical knowledge. For example, the main thesis of the excellent [_Statistics for Hackers_][2] talk by Jake VanderPlas is: _"If you can write a for-loop, you can do statistics"_. Similar ground was covered by Erik Bernhardsson in [_The Hacker's Guide to Uncertainty Estimates_][3], which provides more use cases for bootstrapping (with code examples). However, I've learned in the past few weeks that there are quite a few pitfalls in bootstrapping. Much of what I've learned is summarised in a paper titled [_What Teachers Should Know about the Bootstrap: Resampling in the Undergraduate Statistics Curriculum_][4] by Tim Hesterberg. I doubt that many hackers would be motivated to read a paper with such a title, so my goal with this post is to make some of my discoveries more accessible to a wider audience. To learn more about the issues raised in this post, it's worth reading Hesterberg's paper and other linked resources.

For quick reference, here's a summary of the advice in this post:

  * Use an accurate method for estimating confidence intervals
  * Use enough resamples &ndash; at least 10-15K
  * Don't compare confidence intervals visually
  * Ensure that the basic assumptions apply to your situation

## Pitfall #1: Inaccurate confidence intervals

[Confidence intervals][5] are a common way of quantifying the uncertainty in an estimate of a population parameter. The percentile method is one of the simplest bootstrapping approaches for generating confidence intervals. For example, let's say we have a data sample of size `n` and we want to estimate a 95% confidence interval for the population mean. We take `r` bootstrap _resamples_ from the original data sample, where each resample is a sample with replacement of size `n`. We calculate the mean of each resample and store the means in a sorted array. We then return the 95% confidence interval as the values that fall at the `0.025r` and `0.975r` indices of the sorted array (i.e., the 2.5% and 97.5% percentiles). The following table shows what the first two resamples may look like for a data sample of size `n=5`.

|            | Original sample | Resample #1 | Resample #2 | ...       |
| ---------- | --------------- | ----------- | ----------- | --------- |
| **Values** | 10              | 30          | 20          | ...       |
|            | 12              | 20          | 20          |           |
|            | 20              | 12          | 30          |           |
|            | 30              | 12          | 30          |           |
|            | 45              | 45          | 30          |           |
|            |                 |             |             |           |
| **Mean**   | _23.4_          | _23.8_      | _26_        | _..._     |

The percentile method is nice and simple. Any programmer should be able to easily implement it in their favourite programming language, assuming [they can actually program][6]. Unfortunately, **this method is just not accurate enough for small sample sizes**. Quoting Hesterberg (emphasis mine):

> The sample sizes needed for different intervals to satisfy the "reasonably accurate" (off by no more than 10% on each side) criterion are: n ≥ 101 for the bootstrap t, 220 for the skewness-adjusted t statistic, 2,235 for expanded percentile, <b style="font-weight:700;">2,383 for percentile</b>, 4,815 for ordinary t (which I have rounded up to 5,000 above), 5,063 for t with bootstrap standard errors and something over 8,000 for the reverse percentile method. 

In [a shorter version of the paper cited above][7], Hesterberg concludes that:

> In practice, implementing some of the more accurate bootstrap methods is difficult (especially those not described here), and people should use a package rather than attempt this themselves. 

In short, **make sure you're using an accurate method for estimating confidence intervals when dealing with sample sizes of less than a few thousand values**. Using a package is a great idea, but unfortunately I don't know of any Python bootstrapping package that is feature-complete: [ARCH][8] and [scikits-bootstrap][9] support advanced confidence interval methods but don't support analysis of two samples of uneven sizes, while [bootstrapped][10] works with samples of uneven sizes but only supports the percentile and the reverse percentile method (which Hesterberg found to be even less accurate). If you know of any better Python packages, please let me know! (I don't use R, but I suspect the situation is better there). **Update**: [ARCH now supports][11] analysis of samples of uneven sizes [following an issue I reported][12]. It seems to be the best Python bootstrapping package, so I recommend using it.

## Pitfall #2: Not enough resamples

Accurate bootstrap estimates require a large number of resamples. Many code snippets use 1,000 resamples, probably because it looks like a large number. However, _seeming_ large isn't enough. Quoting Hesterberg again:

> For both the bootstrap and permutation tests, the number of resamples needs to be 15,000 or more, for 95% probability that simulation-based one-sided levels fall within 10% of the true values, for 95% intervals and 5% tests. I recommend r = 10,000 for routine use, and more when accuracy matters.
> 
> [...]
> 
> We want decisions to depend on the data, not random variation in the Monte Carlo implementation. We used r = 500,000 in the Verizon project. 

That's right, half a million resamples! Accuracy mattered in the Verizon case, as the results of the analysis determined whether large penalties were paid or not. In short, **use at least 10-15,000 resamples to be safe**. Don't use 1,000.

## Pitfall #3: Comparison of single-sample confidence intervals

Confidence intervals are commonly used to decide if the difference between two samples is statistically significant. Bootstrapping provides a straightforward way of estimating confidence intervals without making assumptions about the way the data was generated. For example, given two samples, we can obtain confidence intervals for the mean of each sample and end up with a plot like this:

{{< figure src="overlapping-confidence-intervals.png" alt="Overlapping confidence intervals" >}}

When looking at this plot, some people may conclude that the difference between the groups isn't statistically significant because the confidence intervals overlap. However, **overlapping confidence intervals don't imply a lack of statistical significance** because it is possible for the confidence interval of the _difference_ between the sample means to not contain zero. Prasanna Parasurama explained why this happens in [this post][14]. While this issue isn't unique to bootstrapping, it's worth remembering that when comparing two groups, we need to obtain the confidence interval for the difference in the parameter we're comparing, not compare single-sample confidence intervals.

For a concrete example, consider a case where we're looking at a binary outcomes (yes/no or 1/0), which occur in coin flips or online A/B tests. Sample A consists of 2,150 zeroes and 350 ones, while sample B consists of 2,250 zeroes and 440 ones. As these are fairly large samples, we can use the bootstrap percentile method to obtain 95% confidence intervals for the mean of each sample. As the following figure shows, these intervals overlap. If we use the same method to also obtain a 95% confidence interval for the difference in means between B and A, we see that it doesn't include zero. Therefore, we can say that the difference between B and A is statistically significant, despite the overlap between the single-sample confidence intervals.

{{< figure src="overlapping-confidence-intervals-significant-difference.png" alt="Overlapping significance intervals with a statistically significant difference" >}}

It's worth noting that when analysing binary outcomes, we can make stronger assumptions about the data rather than use bootstrapping to obtain confidence intervals. [Erik Bernhardsson suggests using the Beta distribution to obtain single-sample confidence intervals][3], but as we've seen, they don't tell us enough about the differences between samples. [I suggested using a Bayesian approach in the past][16], which makes explicit modelling assumptions that allow us to encode our prior knowledge on the specific environment where the data was generated. For example, when running online A/B tests, we often have a ballpark figure for reasonable results, which can be used in [the Bayesian A/B testing calculator I built][17].

## Pitfall #4: Unrepresentative and dependent samples

While the basic bootstrap makes no assumption about the underlying distribution of the data, it is not assumption-free. For example, when dealing with correlated data points from a time series, using the basic bootstrapping approach is wrong because it assumes that the data points are independent. Instead, a [block bootstrap][18] should be used &ndash; see [the ARCH package][19] for some implementation examples. In addition, bootstrapping doesn't solve problems with the underlying sampling approach. For example, the data sample may not be representative of the population because of its small size, or there may be selection biases and measurement errors. No amount of bootstrapping is going to help with such issues. In general, it always helps to be aware of the data's generation process, e.g., different considerations apply when [dealing with data from online experiments][20] versus [observational studies][21].

## Conclusion and next steps

While bootstrapping is a powerful method, its initial impression of simplicity is misleading. To draw valid conclusions, it's a good idea to use a package and be aware of considerations that are specific to the analysed data sample. However, if you're already increasing your awareness of the data and its generation process, it may make sense to explicitly encode your assumptions in the model. This is where another hacker resource would come in handy: [_Probabilistic Programming & Bayesian Methods for Hackers_][22] by Cam Davidson-Pilon. Admittedly, it's a bit longer than the average blog post or conference talk, but it is worth reading.

Going down the bootstrapping rabbit hole has reminded me of an important lesson: Blog posts and talks &ndash; especially ones with the word _hacker_ in the title &ndash; may be a good starting point, but they shouldn't be relied on for serious work. Instead, it is better to consult peer-reviewed resources and textbooks, such as the [references listed in ARCH's documentation][23]. In my future explorations of bootstrapping and other methods, I will heed Abraham Lincoln's timeless advice to not trust everything I read on the internet.

{{< figure src="dont-believe-everything-you-read-on-the-internet-lincoln.jpg" alt="Abraham Lincoln internet quote" >}}

**Update (Oct 2019)**: I published [a post][25] summarising a talk I gave on the topic, complete with [simulation code][26] that illustrates the issues with some bootstrapping algorithms.

 [1]: https://en.wikipedia.org/wiki/Bootstrapping_(statistics)
 [2]: https://speakerdeck.com/jakevdp/statistics-for-hackers
 [3]: https://erikbern.com/2018/10/08/the-hackers-guide-to-uncertainty-estimates.html
 [4]: https://arxiv.org/abs/1411.5279
 [5]: https://en.wikipedia.org/wiki/Confidence_interval
 [6]: https://blog.codinghorror.com/why-cant-programmers-program/
 [7]: https://storage.googleapis.com/pub-tools-public-publication-data/pdf/44859.pdf
 [8]: https://github.com/bashtage/arch/
 [9]: https://github.com/cgevans/scikits-bootstrap/
 [10]: https://github.com/facebookincubator/bootstrapped/
 [11]: https://github.com/bashtage/arch/releases/tag/4.8.0
 [12]: https://github.com/bashtage/arch/issues/260
 [14]: https://towardsdatascience.com/why-overlapping-confidence-intervals-mean-nothing-about-statistical-significance-48360559900a
 [16]: https://yanirseroussi.com/2016/06/19/making-bayesian-ab-testing-more-accessible/
 [17]: https://yanirs.github.io/tools/split-test-calculator/
 [18]: https://en.wikipedia.org/wiki/Bootstrapping_(statistics)#Block_bootstrap
 [19]: https://arch.readthedocs.io/en/latest/bootstrap/timeseries-bootstraps.html
 [20]: https://yanirseroussi.com/2016/06/19/making-bayesian-ab-testing-more-accessible/
 [21]: https://yanirseroussi.com/2018/12/24/the-most-practical-causal-inference-book-ive-read-is-still-a-draft/
 [22]: http://camdavidsonpilon.github.io/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/
 [23]: https://arch.readthedocs.io/en/latest/bootstrap/background.html
 [25]: https://yanirseroussi.com/2019/10/06/bootstrapping-the-right-way/
 [26]: https://github.com/yanirs/yanirs.github.io/blob/master/talks/bootstrapping-the-right-way/notebook.ipynb
