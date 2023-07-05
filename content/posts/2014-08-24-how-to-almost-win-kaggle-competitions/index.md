---
title: How to (almost) win Kaggle competitions
author: Yanir Seroussi
type: post
date: 2014-08-24T12:40:53+00:00
url: /2014/08/24/how-to-almost-win-kaggle-competitions/
summary: Summary of a talk I gave at the Data Science Sydney meetup with ten tips on almost-winning Kaggle competitions.
tags:
  - data science
  - Kaggle
  - Kaggle beginners
  - Kaggle competition
  - predictive modelling

---
Last week, I gave a talk at the <a href="http://www.meetup.com/Data-Science-Sydney/" target="_blank" rel="noopener">Data Science Sydney Meetup group</a> about some of the lessons I learned through almost winning five Kaggle competitions. The core of the talk was ten tips, which I think are worth putting in a post (the original slides are <a href="http://yanirs.github.io/talks/data-science-sydney-winning-kaggle/" target="_blank" rel="noopener">here</a>). Some of these tips were covered in my [beginner tips post][1] from a few months ago. Similar advice was also <a href="http://blog.kaggle.com/2014/08/01/learning-from-the-best/" target="_blank" rel="noopener">recently published on the Kaggle blog</a> – it's great to see that my tips are in line with the thoughts of other prolific kagglers.

### Tip 1: RTFM

It's surprising to see how many people miss out on important details, such as remembering the final date to make the first submission. Before jumping into building models, it's important to understand the competition timeline, be able to reproduce benchmarks, generate the correct submission format, etc.

### Tip 2: Know your measure

A key part of doing well in a competition is understanding how the measure works. It's often easy to obtain significant improvements in your score by using an optimisation approach that is suitable to the measure. A classic example is optimising the mean absolute error (MAE) versus the mean square error (MSE). It's easy to show that given no other data for a set of numbers, the predictor that minimises the MAE is the median, while the predictor that minimises the MSE is the mean. Indeed, in the <a href="https://www.kaggle.com/c/dsg-hackathon/forums/t/1821/general-approaches-to-partitioning-the-models/10631#post10631" target="_blank" rel="noopener">EMC Data Science Hackathon</a> we fell back to the median rather than the mean when there wasn't enough data, and that ended up working pretty well.

### Tip 3: Know your data

In Kaggle competitions, overspecialisation (without overfitting) is a good thing. This is unlike academic machine learning papers, where researchers often test their proposed method on many different datasets. This is also unlike more applied work, where you may care about data drifting and whether what you predict actually makes sense. Examples include the <a href="https://www.kaggle.com/c/dsg-hackathon/forums/t/1821/general-approaches-to-partitioning-the-models/10631#post10631" target="_blank" rel="noopener">Hackathon</a>, where the measures of pollutants in the air were repeated for consecutive hours (i.e., they weren't really measured); the <a title="Greek Media Monitoring Kaggle competition: My approach" href="https://yanirseroussi.com/2014/10/07/greek-media-monitoring-kaggle-competition-my-approach/" target="_blank" rel="noopener">multi-label Greek article competition</a>, where I found connected components of labels (doesn't generalise well to other datasets); and the <a href="http://blog.kaggle.com/2012/04/29/on-diffusion-kernels-histograms-and-arabic-writer-identification/" target="_blank" rel="noopener">Arabic writers competition</a>, where I used histogram kernels to deal with the features that we were given. The general lesson is that custom solutions win, and that's why the world needs data scientists (at least <a href="http://www.datarobot.com/" target="_blank" rel="noopener">until we are replaced by robots</a>).

### Tip 4: What before how

It's important to know _what_ you want to model before figuring out _how_ to model it. It seems like many beginners tend to worry too much about which tool to use (Python or R? Logistic regression or SVMs?), when they should be worrying about understanding the data and what useful patterns they want to capture. For example, when we worked on the [Yandex search personalisation competition][2], we spent a lot of time looking at the data and thinking what makes sense for users to be doing. In that case it was easy to come up with ideas, because we all use search engines. But the main message is that to be effective, you have to become one with the data.

### Tip 5: Do local validation

This is a point I covered in my [Kaggle beginner tips post][3]. Having a local validation environment allows you to move faster and produce more reliable results than when relying on the leaderboard. The main scenarios when you should skip local validation is when the data is too small (a problem I had in the <a href="http://blog.kaggle.com/2012/04/29/on-diffusion-kernels-histograms-and-arabic-writer-identification/" target="_blank" rel="noopener">Arabic writers competition</a>), or when you run out of time (towards the end of the competition).

### Tip 6: Make fewer submissions

In addition to making you look good, making few submissions reduces the likelihood of overfitting the leaderboard, which is a real problem. If your local validation is set up well and is consistent with the leaderboard (which you need to test by making one or two submissions), there's really no need to make many submissions. Further, if you're doing well, making submissions erodes your competitive advantage by showing your competitors what scores are obtainable and motivating them to work harder. Just resist the urge to submit, unless you have a really good reason.

### Tip 7: Do your research

For any given problem, it's likely that there are people dedicating their lives to its solution. These people (often academics) have probably published papers, benchmarks and code, which you can learn from. Unlike actually winning, which is not only dependent on you, gaining deeper knowledge and understanding is the only sure reward of a competition. This has worked well for me, as I've learned something new and applied it successfully in [nearly every competition I've worked on][4].

### Tip 8: Apply the basics rigorously

While playing with obscure methods can be a lot of fun, it's often the case that the basics will get you very far. Common algorithms have good implementations in most major languages, so there's really no reason not to try them. However, note that when you do try any methods, you _must_ do some minimal tuning of the main parameters (e.g., number of trees in a random forest or the regularisation of a linear model). **Running a method without minimal tuning is worse than not running it at all**, because you may get a false negative – giving up on a method that actually works very well.

An example of applying the basics rigorously is in the classic paper <a href="http://jmlr.org/papers/volume5/rifkin04a/rifkin04a.pdf" target="_blank" rel="noopener">In defense of one-vs-all classification</a>, where the authors showed that the simple one-vs-all (OVA) approach to multiclass classification is at least as good as approaches that are much more sophisticated. In their words: "What we find is that although a wide array of more sophisticated methods for multiclass classification exist, experimental evidence of the superiority of these methods over a simple OVA scheme is either lacking or improperly controlled or measured". If such a failure to perform proper experiments can happen to serious machine learning researchers, it can definitely happen to the average kaggler. Don't let it happen to you.

### Tip 9: The forum is your friend

It's very important to subscribe to the forum to receive notifications on issues with the data or the competition. In addition, it's worth trying to figure out what your competitors are doing. An extreme example is the recent trend of code sharing during the competition (<a href="http://www.kaggle.com/forums/t/5681/fed-up-with-beating-benchmark-code/30787#post30787" target="_blank" rel="noopener">which I don't really like</a>) – while it's not a good idea to rely on such code, it's important to be aware of its existence. Finally, reading the post-competition summaries on the forum is a valuable way of learning from the winners and improving over time.

### Tip 10: Ensemble all the things

Not to be confused with ensemble methods (which are also very important), the idea here is to combine models that were developed independently. In high-profile competitions, it is often the case that teams merge and gain a significant boost from combining their models. This is worth doing even when competing alone, because almost no competition is won by a single model.

 [1]: https://yanirseroussi.com/2014/01/19/kaggle-beginner-tips/
 [2]: https://www.kaggle.com/c/yandex-personalized-web-search-challenge/forums/t/6811/share-your-approach/37306#post37306
 [3]: https://yanirseroussi.com/2014/01/19/kaggle-beginner-tips/#validation
 [4]: https://yanirseroussi.com/2014/04/05/kaggle-competition-summaries/
