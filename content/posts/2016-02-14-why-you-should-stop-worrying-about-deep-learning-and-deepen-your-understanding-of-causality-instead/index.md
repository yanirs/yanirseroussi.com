---
title: Why you should stop worrying about deep learning and deepen your understanding of causality instead
author: Yanir Seroussi
type: post
date: 2016-02-14T11:04:11+00:00
url: /2016/02/14/why-you-should-stop-worrying-about-deep-learning-and-deepen-your-understanding-of-causality-instead/
cover:
  image: correlation-xkcd.png
  responsiveImages: false
tags:
  - analytics
  - causal inference
  - causality
  - data science
  - deep learning
  - insights
  - machine learning
  - predictive modelling

---
Everywhere you go these days, you hear about deep learning's impressive advancements. New deep learning libraries, tools, and products get announced on a regular basis, making the average data scientist feel like they're missing out if they don't <a href="https://yanirseroussi.com/2015/06/06/hopping-on-the-deep-learning-bandwagon/" target="_blank" rel="noopener">hop on the deep learning bandwagon</a>. However, as Kamil Bartocha put it in his post <a href="https://www.linkedin.com/pulse/inconvenient-truth-data-science-kamil-bartocha" target="_blank" rel="noopener">The Inconvenient Truth About Data Science</a>, _95% of tasks do not require deep learning_. This is obviously <a href="http://dilbert.com/strip/2008-05-08" target="_blank" rel="noopener">a made up number</a>, but it's probably an accurate representation of the everyday reality of many data scientists. This post discusses an often-overlooked area of study that is of much higher relevance to most data scientists than deep learning: **causality**.

## Causality is everywhere

An understanding of cause and effect is something that is not unique to humans. For example, the many videos of cats knocking things off tables appear to exemplify experimentation by animals. If you are not familiar with such videos, <a href="https://www.youtube.com/results?search_query=cat+knocking+stuff+off" target="_blank" rel="noopener">it can easily be fixed</a>. The thing to notice is that cats appear genuinely curious about what happens when they push an object. And they tend to repeat the experiment to verify that if you push something off, it falls to the ground.

<p>
  {{< youtube UoUEQYjYgf4 >}}
</p>

Humans rely on much more complex causal analysis than that done by cats &ndash; an understanding of the long-term effects of one's actions is crucial to survival. <a href="https://en.wikipedia.org/wiki/Science" target="_blank" rel="noopener">Science, as defined by Wikipedia</a>, _is a systematic enterprise that creates, builds and organizes knowledge in the form of testable explanations and predictions about the universe_. Causal analysis is key to producing explanations and predictions that are valid and sound, which is why understanding causality is so important to data scientists, traditional scientists, and all humans. 

## What is causality?

It is surprisingly hard to define causality. Just like cats, we all have an intuitive sense of what causality is, but things get complicated on deeper inspection. For example, few people would disagree with the statement that _smoking causes cancer_. But does it cause cancer immediately? Would smoking a few cigarettes today and never again cause cancer? Do all smokers develop cancer eventually? What about light smokers who live in areas with heavy air pollution?

Samantha Kleinberg summarises it very well in her book, <a href="http://www.skleinberg.org/why/" target="_blank" rel="noopener">Why: A Guide to Finding and Using Causes</a>:

> While most definitions of causality are based on <a href="https://en.wikipedia.org/wiki/David_Hume" target="_blank" rel="noopener">Hume's work</a>, none of the ones we can come up with cover all possible cases and each one has counterexamples another does not. For instance, a medication may lead to side effects in only a small fraction of users (so we can't assume that a cause will always produce an effect), and seat belts normally prevent death but can cause it in some car accidents (so we need to allow for factors that can have mixed producer/preventer roles depending on context).
> 
> The question often boils down to whether we should see causes as a fundamental building block or force of the world (that can't be further reduced to any other laws), or if this structure is something we impose. As with nearly every facet of causality, there is disagreement on this point (and even disagreement about whether particular theories are compatible with this notion, which is called causal realism). Some have felt that causes are so hard to find as for the search to be hopeless and, further, that once we have some physical laws, those are more useful than causes anyway. That is, "causes" may be a mere shorthand for things like triggers, pushes, repels, prevents, and so on, rather than a fundamental notion.
> 
> It is somewhat surprising, given how central the idea of causality is to our daily lives, but there is simply no unified philosophical theory of what causes are, and no single foolproof computational method for finding them with absolute certainty. What makes this even more challenging is that, depending on one’s definition of causality, different factors may be identified as causes in the same situation, and it may not be clear what the ground truth is. 

## Why study causality now?

While it's hard to conclusively prove, it seems to me like interest in formal causal analysis has increased in recent years. My hypothesis is that it's just a natural progression along the levels of [data's hierarchy of needs][1]. At the start of the big data boom, people were mostly concerned with storing and processing large amounts of data (e.g., using Hadoop, Elasticsearch, or your favourite NoSQL database). Just having your data flowing through pipelines is nice, but not very useful, so the focus switched to reporting and visualisation to extract insights about what happened (commonly known as business intelligence). While having a good picture of what happened is great, it isn't enough &ndash; you can make better decisions if you can predict what's going to happen, so the focus switched again to predictive analytics. Those who are familiar with predictive analytics know that models often end up relying on correlations between the features and the predicted labels. Using such models without considering the meaning of the variables can lead us to erroneous conclusions, and potentially harmful interventions. For example, based on the following graph we may make a recommendation that the US government decrease its spending on science to reduce the number of suicides by hanging.

{{< figure src="us-science-spending-versus-suicides.png" alt="US science spending versus suicides" caption="Source: <a href=\"http://www.tylervigen.com/spurious-correlations\" target=\"_blank\" rel=\"noopener\">Spurious Correlations by Tyler Vigen</a>" >}}

Causal analysis aims to identify factors that are independent of spurious correlations, allowing stakeholders to make well-informed decisions. It is all about [getting to the top of the DIKW (data-information-knowledge-wisdom) pyramid][2] by understanding **why** things happen and what we can do to change the world. However, finding true causes can be very hard, especially in cases where you can't perform experiments. <a href="http://ftp.cs.ucla.edu/pub/stat_ser/r391.pdf" target="_blank" rel="noopener">Judea Pearl explains it well</a>:

> We know, from first principles, that any causal conclusion drawn from observational studies must rest on untested causal assumptions. Cartwright (1989) named this principle &#8216;no causes in, no causes out,' which follows formally from the theory of equivalent models (Verma and Pearl, 1990); for any model yielding a conclusion C, one can construct a statistically equivalent model that refutes C and fits the data equally well. 

What this means in practice is that you can't, for example, conclusively prove that smoking causes cancer without making some reasonable assumptions about the mechanisms at play. For ethical reasons, we can't perform a randomly controlled trial where a test group is forced to smoke for years while a control group is forced not to smoke. Therefore, our conclusions about the causal link between smoking and cancer are drawn from observational studies and an understanding of the mechanisms by which various cancers develop (e.g., the effect of cigarette smoke on individual cells can be studied without forcing people to smoke). <del>Cancer</del> Tobacco companies have exploited this fact for years, making the claim that the probability of both cancer and smoking is raised by some mysterious genetic factors. Fossil fuel and food companies use similar arguments to sell their products and block attempts to regulate their industries (as discussed in previous posts on [the hardest parts of data science][3] and [nutritionism][4]). Fighting against such arguments is an uphill battle, as it is easy to sow doubt with a few simplistic catchphrases, while proving and communicating causality to laypeople is much harder (or <a href="http://www.sciencealert.com/new-study-links-climate-change-denials-with-conspiracy-theories" target="_blank" rel="noopener">impossible when it comes to deeply-held irrational beliefs</a>).

## My causality journey is just beginning

My interest in formal causal analysis was seeded a couple of years ago, with a reading group that was dedicated to Judea Pearl's work. We didn't get very far, as I was a bit disappointed with what causal calculus can and cannot do. This may have been because I didn't come in with the right expectations &ndash; I expected a black box that automatically finds causes. Recently reading Samantha Kleinberg's excellent book <a href="http://www.skleinberg.org/why/" target="_blank" rel="noopener">Why: A Guide to Finding and Using Causes</a> has made my expectations somewhat more realistic:

> Thousands of years after Aristotle's seminal work on causality, hundreds of years after Hume gave us two definitions of it, and decades after automated inference became a possibility through powerful new computers, causality is still an unsolved problem. Humans are prone to seeing causality where it does not exist and our algorithms aren't foolproof. Even worse, once we find a cause it's still hard to use this information to prevent or produce an outcome because of limits on what information we can collect and how we can understand it. After looking at all the cases where methods haven’t worked and researchers and policy makers have gotten causality really wrong, you might wonder why you should bother.
> 
> [...]
> 
> Rather than giving up on causality, what we need to give up on is the idea of having a black box that takes some data straight from its source and emits a stream of causes with no need for interpretation or human intervention. Causal inference is necessary and possible, but it is not perfect and, most importantly, it requires domain knowledge. 

Kleinberg's book is a great general intro to causality, but it intentionally omits the mathematical details behind the various methods. I am now ready to once again go deeper into causality, perhaps starting with Kleinberg's more technical book, <a href="http://www.skleinberg.org/causality_book/index.html" target="_blank" rel="noopener">Causality, Probability, and Time</a>. Other recommendations are very welcome!

<p style="font-size:80%;">
  <i>Cover image source: <a href="https://xkcd.com/552/" target="_blank" rel="noopener">xkcd: Correlation</a></i>
</p>

 [1]: https://yanirseroussi.com/2014/08/17/datas-hierarchy-of-needs/
 [2]: https://yanirseroussi.com/2015/12/08/this-holiday-season-give-me-real-insights/
 [3]: https://yanirseroussi.com/2015/11/23/the-hardest-parts-of-data-science/
 [4]: https://yanirseroussi.com/2015/10/19/nutritionism-and-the-need-for-complex-models-to-explain-complex-phenomena/
