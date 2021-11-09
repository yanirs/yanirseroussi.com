---
title: The hardest parts of data science
author: Yanir Seroussi
type: post
date: 2015-11-23T04:14:21+00:00
url: /2015/11/23/the-hardest-parts-of-data-science/
cover:
  image: foggy-random-forest.jpg
tags:
  - climate change
  - data science
  - Kaggle
  - predictive modelling
  - science communication

---
Contrary to common belief, the hardest part of data science isn't building an accurate model or obtaining good, clean data. It is much harder to define feasible problems and come up with reasonable ways of measuring solutions. This post discusses some examples of these issues and how they can be addressed.

## The not-so-hard parts

Before discussing the hardest parts of data science, it's worth quickly addressing the two main contenders: model fitting and data collection/cleaning. 

**Model fitting** is seen by some as particularly hard, or as _real_ data science. This belief is fuelled in part by the success of <a href="https://www.kaggle.com/" target="_blank" rel="noopener">Kaggle</a>, that calls itself _the home of data science_. Most Kaggle competitions are focused on model fitting: Participants are given a well-defined problem, a dataset, and a measure to optimise, and they compete to produce the most accurate model. Coupling Kaggle's excellent marketing with their competition setup leads many people to believe that data science is all about fitting models. In reality, building reasonably-accurate models is not that hard, because many model-building phases can easily be automated. Indeed, there are many companies that offer model fitting as a service (e.g., Microsoft, Amazon, Google and <a href="http://www.shivonzilis.com/machineintelligence" target="_blank" rel="noopener">others</a>). Even Ben Hamner, CTO of Kaggle, has said that he is "surprised at the number of 'black box machine learning in the cloud' services emerging: model fitting is easy. Problem definition and data collection are not."

{{< figure src="ben-hamner-black-box-ml.png" link="https://twitter.com/benhamner/status/595850574999990274" alt="Ben Hamner tweet on black box ML in the cloud" >}}

**Data collection/cleaning** is the essential part that everyone loves to hate. DJ Patil (US Chief Data Scientist) is <a href="http://codingvc.com/talk-summary-building-great-data-products" target="_blank" rel="noopener">quoted as saying</a> that "the hardest part of data science is getting good, clean data. Cleaning data is often 80% of the work." While I agree that collecting data and cleaning it can be a lot of work, I don't think of this part as particularly hard. It's definitely important and may require careful planning, but in many cases it just isn't very challenging. In addition, it is often the case that the data is already given, or is collected using previously-developed methods.

## Problem definition is hard

There are many reasons why problem definition can be hard. It is sometimes due to stakeholders who don't know what they want, and [expect data scientists to solve all their data problems (either real or imagined)][1]. This type of situation is summarised by <a href="http://dilbert.com/strip/2012-07-29" target="_blank" rel="noopener">the following Dilbert strip</a>. It is best handled by cleverly managing stakeholder expectations, while stirring them towards better-defined problems.

{{< figure src="dilbert-big-data.jpg" alt="Dilbert big data" >}}

Well-defined problems are great, for the obvious reason that they can actually be addressed. Examples of such problems include:

  * Build a model to predict the sales of a marketing campaign
  * Create a system that runs campaigns that automatically adapt to customer feedback
  * Identify key objects in images
  * Improve click-through rates on search engine results, ads, or any other element
  * Detect whale calls from underwater recordings to prevent collisions

Often, it can be hard to get to the stage where the problem is agreed on, because this requires dealing with people who only have a fuzzy idea of what can be done with data science. Dilbertian situations aside, these people often have real problems that they care about, so exploring the core issues with them is time well-spent.

## Solution measurement is often harder than problem definition

Many problems that actually matter have solutions that are really hard to measure. For example, improving the well-being of the population (e.g., a company's customers or a country's citizens) is an overarching problem that arises in many situations. However, this problem gives rise to the hard question of how well-being can be measured and aggregated. The following paragraphs discuss issues that occur in solution measurement, often making it the hardest part of data science.

Ideally, we would always be able to run <a href="https://en.wikipedia.org/wiki/Randomized_controlled_trial" target="_blank" rel="noopener">randomised controlled trials</a> to measure treatment effects. However, the reality is that <a href="https://en.wikipedia.org/wiki/Censoring_%28statistics%29" target="_blank" rel="noopener">experimental data is often censored</a>, there many constraints on running experiments (ethics, practicality, budget, etc.), and <a href="https://en.wikipedia.org/wiki/Confounding" target="_blank" rel="noopener">confounding factors</a> may make it impossible to identify the true causal impact of interventions. These issues seriously influence many aspects of our lives. I've [written a post on how these issues manifest themselves in research on the connection between nutrition and our health][2]. Here, I'll discuss another major example: the health effects of smoking and anthropogenic climate change.

While smoking and anthropogenic climate change may seem unrelated, they actually have a lot in common. In both cases it is hard (or impossible) to perform experiments to determine causality, and in both cases <a href="https://en.wikipedia.org/wiki/Merchants_of_Doubt" target="_blank" rel="noopener">this fact has been used to mislead the public by parties with commercial and ideological interests</a>. In the case of smoking, due to ethical reasons, one can't perform an experiment where a random control group is forced not to smoke, while a treatment group is forced to smoke. Further, since it can take many years for smoking-caused diseases to develop, it'd take a long time to obtain the results of such an experiment. Tobacco companies have exploited this fact for years, claiming that there may be some genetic factor that causes both smoking and a higher susceptibility to smoking-related diseases. Fortunately, we live in a world where these claims have been widely discredited, and it is now clear to most people that smoking is harmful. However, similar doubt-casting techniques are used by polluters and their supporters in the debate on anthropogenic climate change. While no serious climate scientist doubts the fact that human activities are causing climate change, this can't be proved through experimentation on another Earth. In both cases, the answers should be clear when looking at the evidence and the mechanisms at play without an ideological bias. It doesn't take a scientist to figure out that pumping your lungs full of smoke on a regular basis is likely to be harmful, as is pumping the atmosphere full of greenhouse gases that have been sequestered for millions of years. However, as said by Upton Sinclair, "it is difficult to get a man to understand something, when his salary depends upon his not understanding it."

Assuming that we have addressed the issues raised so far, there is the matter of choosing a measure or metric of success. How do we know that our solution works well? A common approach is to choose a single metric to focus on, such as increasing conversion rates. However, all metrics have their flaws, and there are quite a few problems with metric selection and its maintenance over time.

First, **focusing on a single metric can be harmful**, because no metric is perfect. A classic example of this issue is the focus on growing the economy, as measured by <a href="https://en.wikipedia.org/wiki/Gross_domestic_product" target="_blank" rel="noopener">gross domestic product (GDP)</a>. The article <a href="https://mises.org/library/what-gdp" target="_blank" rel="noopener">What is up with the GDP?</a> by Frank Shostak summarises some of the problems with GDP:

> The GDP framework cannot tell us whether final goods and services that were produced during a particular period of time are a reflection of real wealth expansion, or a reflection of capital consumption.
>
> For instance, if a government embarks on the building of a pyramid, which adds absolutely nothing to the well-being of individuals, the GDP framework will regard this as economic growth. In reality, however, the building of the pyramid will divert real funding from wealth-generating activities, thereby stifling the production of wealth.
>
> [...]
>
> The whole idea of GDP gives the impression that there is such a thing as the national output. In the real world, however, wealth is produced by someone and belongs to somebody. In other words, goods and services are not produced in totality and supervised by one supreme leader. This in turn means that the entire concept of GDP is devoid of any basis in reality. It is an empty concept.

Shostak's criticism comes from a right-winged viewpoint &ndash; his argument is that the GDP is used as an excuse for unnecessary government intervention with the market. However, the focus on GDP growth is also heavily-criticised by the left due to the fact that it doesn't consider environmental effects and inequalities in the distribution of wealth. It is a bit odd that GDP growth is still considered a worthwhile goal by many people, given that it can easily be skewed by a few powerful individuals who choose to build unnecessary pyramids (though perhaps this is the real reason why the GDP persists &ndash; wealthy individuals have an interest in keeping it this way).

Even if we decide to use **multiple metrics** to evaluate our solution, our troubles aren't over yet. Using multiple metrics often means that there are trade-offs between the different metrics. For example, with the <a href="https://en.wikipedia.org/wiki/Precision_and_recall" target="_blank" rel="noopener">precision and recall</a> measures that are commonly used to evaluate the performance of search engines, it is rare to be able to increase both precision and recall at the same time. _Precision_ is the percentage of relevant items out of those that have been returned, while _recall_ is the percentage of relevant items that have been returned out of the overall number of relevant items. Hence, it is easy to artificially increase recall to 100% by always returning all the items in the database, but this would mean settling for near-zero precision. Similarly, one can increase precision by always returning a single item that the algorithm is very confident about, but this means that recall would suffer. Ultimately, the best balance between precision and recall depends on the application.

Another issue with choosing metrics is the impossibility of reliably evaluating our choices. This is summarised well by Scott Berkun in his book <a href="http://scottberkun.com/yearwithoutpants/" target="_blank" rel="noopener">The Year Without Pants</a>:

> All metrics create temptations. Even with great intentions and smart minds, data runs you faster and faster into a stupid self-destructive circle. Data can't decide things for you. It can help you see things more clearly if captured carefully, but that's not the same as deciding. Just as there is an advice paradox, there is a data paradox: no matter how much data you have, you still depend on your intuition for deciding how to interpret and then apply the data.
>
> Put another way, there is no good KPI for measuring KPIs. There are no good metrics for evaluating metrics (or for evaluating metrics for evaluating metrics for evaluating metrics, and on it goes).

OK, so we've picked some flawed measures that we can't really evaluate, and we've accepted the imperfections of the evaluation process. Are we done yet? No. There's still the small matter of <a href="https://en.wikipedia.org/wiki/Goodhart's_law" target="_blank" rel="noopener">Goodhart's Law</a>, which states that "when a measure becomes a target, it ceases to be a good measure." This is often the case because people will tend to manipulate results and game the system (not necessarily maliciously) in order to hit measured goals. However, even without manipulation and gaming, we often deal with moving targets. Just because the measure we've chosen is suitable today, it doesn't mean it will still be relevant in a few months or years because reality changes. For example, in the 1990s, the number of page views was a good measure of interaction with websites, but nowadays it is a pretty weak measure because many websites are single-page applications. Reality changes and so should our problems, solutions, measures, and goals.

## Embracing ambiguity and uncertainty

Personally, I find the complexities of measurement and problem definition quite interesting. However, many people aren't that interested in this stuff &ndash; they just want working solutions and simple stories. As demonstrated by the examples throughout this article, over-simplification of complicated matters is a pervasive issue that goes beyond what's commonly considered "data science". This is why storytelling is seen as a key skill that data scientists should possess. I believe it's also important to maintain one's integrity and not just make up stories that people would buy, but it'd be naive to assume that this never happens. Either way, good data scientists embrace uncertainty and ambiguity, but can still tell a simple story if needed. 

<small><b>Note:</b> The ideas in this post were first presented at <a href="http://www.meetup.com/The-Sydney-Data-Science-Breakfast-Meetup-Group/" target="_blank" rel="noopener">The Sydney Data Science Breakfast Meetup Group</a>. The slides for that talk are available <a href="http://yanirs.github.io/talks/the-hardest-part-of-data-science" target="_blank" rel="noopener">here</a>.</small>

 [1]: http://yanirseroussi.com/2015/08/24/you-dont-need-a-data-scientist-yet/
 [2]: http://yanirseroussi.com/2015/10/19/nutritionism-and-the-need-for-complex-models-to-explain-complex-phenomena/
