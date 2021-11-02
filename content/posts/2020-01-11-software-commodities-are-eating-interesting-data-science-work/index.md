---
title: Software commodities are eating interesting data science work
author: Yanir Seroussi
type: post
date: 2020-01-11T09:22:35+00:00
url: /2020/01/11/software-commodities-are-eating-interesting-data-science-work/
cover:
 image: pacman.png
timeline_notification:
  - 1578734558
categories:
  - Data science
tags:
  - business
  - career
  - data science
  - software engineering

---
{{< blockquote author="Rob Reid" link="https://after-on.com/after-on-novel" title="After On" >}}
The passage of time makes wizards of us all. Today, any dullard can make bells ring across the ocean by tapping out phone numbers, cause inanimate toys to march by barking an order, or activate remote devices by touching a wireless screen. Thomas Edison couldn't have managed any of this at his peak&mdash;and shortly before his time, such powers would have been considered the unique realm of God.
{{< /blockquote >}}

Being a data scientist can sometimes feel like a race against software innovations. Every interesting and useful problem is bound to become a software commodity. My story seems to reflect that: From my first steps in sentiment analysis and topic modelling, through building recommender systems while dabbling in Kaggle competitions and deep learning a few years ago, and to [my present-day interest in causal inference][1]. What can one do to remain relevant in such an environment? Read this post to find out.

## Highlights from my past

When I started my PhD in 2009, [the plan was to work on sentiment analysis of opinion polls][2]. This got me into applied machine learning using Java and [Weka][3], with which I made some modest contributions to the field. Today, researching sentiment analysis would feel somewhat pointless, given the plethora of sentiment analysis services. Sentiment analysis is a commodity &ndash; using it in practice is a software engineering problem.

Moving forward in my PhD, I got into topic modelling. I learned about Bayesian statistics and conjugate priors. I went through the arduous process of solving integrals by hand and coding a custom Gibbs sampler for [the models I specified][4]. Today, I probably wouldn't bother with the maths. Instead, I'd specify the model and let a probabilistic programming tool like [pymc3][5] or [Stan][6] handle the rest. Bayesian inference is now a commodity that's [accessible to any hacker][7].

{{< figure src="thesis-maths.png" caption="A part of [my PhD thesis](https://figshare.com/articles/Text_mining_and_rating_prediction_with_topical_user_models/4664473) that can probably be replaced by a probabilistic programming tool" >}}

Towards the end of my PhD in 2012, [I got into Kaggle competitions][10]. Back then, it seemed like "real" data science consisted of building and tuning machine learning models &ndash; that's what Kaggle was all about. While [I've done quite well in those competitions][11], I've come to realise that the utility of fine-tuning machine learning algorithms is quite limited. In reality, [problem definition and solution measurement][12] are more challenging and important. Using machine learning in practice is typically an engineering problem: We can use an existing [service][13] or [package][14], follow best practices, and have a great solution for most use cases. No research or custom data work is required beyond turning data into features, which is essentially a data engineering problem. In short, **solid machine learning solutions are delivered by solid engineers who glue together solid commodity components**. Quoting [Google's Rules of Machine Learning][15]:

> To make great products: do machine learning like the great engineer you are, not like the great machine learning expert you aren't.
> 
> Most of the problems you will face are, in fact, engineering problems. Even with all the resources of a great machine learning expert, most of the gains come from great features, not great machine learning algorithms. So, the basic approach is:
> 
>   1. Make sure your pipeline is solid end to end.
>   2. Start with a reasonable objective.
>   3. Add common-sense features in a simple way.
>   4. Make sure that your pipeline stays solid.

{{< figure src="science-versus-engineering.png" alt="Information flow in science and engineering" caption="Many problems in data &ldquo;science&rdquo; are actually engineering problems &ndash; described best by the flow on the right ([source](https://fs.blog/2013/07/the-difference-between-science-and-engineering/))" >}}

Some of my first jobs as a data scientist in industry involved building [recommender systems][18]. With recommender systems, much of the work is on the system around the recommendation algorithm. That is, building a recommender system was always mostly an engineering problem. However, these days we have services like [AWS Personalize][19], which does most of the heavy lifting around recommendation. This makes the deployment of recommender systems a pure engineering problem. Like many other problems, recommender systems have been commodified.

[I have not done much with deep learning][20], but there the general trend is even more apparent: Useful innovations quickly turn into tools. Examples include library evolution from Theano to TensorFlow, and commodified prediction services from companies like Google, Amazon, and Microsoft. If you want to use a deep learning service in your application, you probably don't need a data scientist or even a machine learning engineer. A solid software engineer who can pick the right tools should be enough.

## How to remain relevant?

So where does this leave us? It seems to be a more general phenomenon. Essentially every problem that requires specialised knowledge and is valuable ends up attracting repeatable solutions that obviate the need for deep thinking and manual work. These solutions are software commodities. Deploying them is a matter of writing some glue code and fitting them into the overall system &ndash; an engineering problem. Implementing data science components to compete with commodities may be interesting and fun, but it's usually a waste of time when there's a generic solution that is [good enough][21].

As an individual data scientist, **what can you do when your speciality becomes a software commodity?** I see a few options:

  1. **Embrace the engineering angle**. Become good (or better) at engineering solutions. Be pragmatic. Do what it takes to get the job done. This is probably easier for data scientists like me, who have an engineering background, than for more research/analysis-oriented data scientists. Such data scientists sometimes sneer at engineering work, claiming it's "fake" data science. Fake or not, solid engineering tools can easily make stubborn data scientists obsolete.
  2. **Keep building custom solutions even when viable commodities exist**. While this may be more fun for the individual, I believe it isn't a sustainable approach. The cost of building and maintaining custom solutions will typically be higher than the cost of commodity solutions. Insisting on custom solutions seems like a recipe for becoming irrelevant.
  3. **Keep adapting and moving to non-commodity areas**. Some things are easier to automate than others. For example, building a machine learning pipeline when the problem is well-defined is relatively easy, but deciding what features to create typically requires some domain expertise. In addition, new research keeps coming out in areas that are less hot than machine learning. One such area is [causal inference][22], where there are still solutions that are yet to be commodified.
  4. **Move to the cutting edge**. If you want to research novel methods, a "standard" data scientist position may not be for you. Many industry positions are focused on applying proven solutions to a specific organisation. If that doesn't sound like fun, you're better off moving to academia or joining a commercial research group.

Are there any other options I don't see? Let me know in the comments!

 [1]: https://yanirseroussi.com/causal-inference-reading-list/
 [2]: https://yanirseroussi.com/2015/05/02/first-steps-in-data-science-author-aware-sentiment-analysis/
 [3]: https://www.cs.waikato.ac.nz/ml/weka/
 [4]: https://yanirseroussi.com/phd-work/
 [5]: https://docs.pymc.io/
 [6]: https://mc-stan.org/
 [7]: http://camdavidsonpilon.github.io/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/
 [9]: https://figshare.com/articles/Text_mining_and_rating_prediction_with_topical_user_models/4664473
 [10]: https://yanirseroussi.com/2014/04/05/kaggle-competition-summaries/
 [11]: https://yanirseroussi.com/2014/08/24/how-to-almost-win-kaggle-competitions/
 [12]: https://yanirseroussi.com/2015/11/23/the-hardest-parts-of-data-science/
 [13]: https://aws.amazon.com/sagemaker/
 [14]: https://scikit-learn.org/stable/
 [15]: https://developers.google.com/machine-learning/guides/rules-of-ml/
 [17]: https://fs.blog/2013/07/the-difference-between-science-and-engineering/
 [18]: https://yanirseroussi.com/2015/10/02/the-wonderful-world-of-recommender-systems/
 [19]: https://aws.amazon.com/personalize/
 [20]: https://yanirseroussi.com/2015/07/06/learning-about-deep-learning-through-album-cover-classification/
 [21]: https://data.blog/2017/06/12/timeseries-analysis/
 [22]: https://yanirseroussi.com/2016/02/14/why-you-should-stop-worrying-about-deep-learning-and-deepen-your-understanding-of-causality-instead/