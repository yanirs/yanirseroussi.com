---
title: Defining data science in 2018
author: Yanir Seroussi
type: post
date: 2018-07-22T08:27:43+00:00
url: /2018/07/22/defining-data-science-in-2018/
cover:
  image: what-would-you-say-you-do-here.jpg
summary: Updating my definition of data science to match changes in the field. It is now broader than before, but its ultimate goal is still to support decisions.
tags:
  - analytics
  - artificial intelligence
  - business
  - data science
  - machine learning
  - statistics

---
I got my first data science job in 2012, the year [Harvard Business Review announced data scientist to be the sexiest job of the 21st century][1]. Two years later, I published [a post on my then-favourite definition of data science][2], as the intersection between software engineering and statistics. Unfortunately, that definition became somewhat irrelevant as more and more people jumped on the data science bandwagon &ndash; possibly to the point of [making data scientist useless as a job title][3]. However, I still call myself a data scientist. Even better &ndash; [I still get paid for being a data scientist][4]. But what does it mean? What do I actually do here? This article is a short summary of my understanding of the definition of data science in 2018.

## It's not all about machine learning

As I was wrapping up my PhD in 2012, I started thinking about my next steps. I knew I wanted to get back to working in the tech industry, ideally with a small startup. But it wasn't clear to me how to market myself &ndash; my LinkedIn title at the time was _"software engineer with a research background"_, which is a bit of a mouthful. Around that time I heard about [Kaggle][5] and decided to try competing. [This went pretty well][6], and exposed me to the data science community globally and in Melbourne, where I was living at the time. That's how I first met Adam Neumann, the founder of Giveable, a startup that aimed to recommend gifts based on social networking data. Upon graduating, I joined Giveable as a data scientist. Changing my LinkedIn title quickly led to many other offers, but I was happy to be working on Giveable &ndash; I felt fortunate to have found a startup job that was related to my PhD research on recommender systems.

My understanding of data science at the time was heavily influenced by Kaggle and the tech industry. Kaggle was only about predictive modelling competitions back then, and so I believed that data science is about using machine learning to build models and deploy them as part of various applications. I was very comfortable with that definition, having spent my PhD years on several predictive modelling tasks, and having worked as a software engineer prior to that.

Things have changed considerably since 2012. It is now much easier to deploy machine learning models, [even without a deep understanding of how they work][7]. Many more people call themselves data scientists, [including some who are more focused on data analysis than on building data products][8]. Even Kaggle &ndash; which is now owned by Google &ndash; [has broadened its scope beyond modelling competitions to support other types of analysis][9]. Numerous articles have been published on the meaning of data science in the past six years. We seem to be going towards a broad definition of the field, which includes any type of general data analysis. This trend of broadening the definition [may make data scientist somewhat useless as a job title][3]. However, I believe that data science tasks remain useful, as shown by the following definitions.

## Recent definitions by Hernán, Hawkins, and Dubossarsky

In a [recent article][10], Hernán et al. classify data science tasks into three types: _description_, _prediction_, and _causal inference_. Like other authors, they argue that causal inference has been neglected by traditional statistics and some scientific disciplines. They claim that the emergence of data science is an opportunity to get causal inference "right". Further, they emphasise the importance of domain expert knowledge, [which is essential in causal inference][11]. Defining data science in this broad manner seems to capture the essence of what the field is about these days. However, purely descriptive tasks are still often performed by data _analysts_ rather than _scientists_. And the distinction between prediction and causal inference can be a bit fuzzy, especially as the tools for the latter are at a lower level of maturity. In addition, while I agree with Hernán et al. that domain expertise is important, it seems unlikely that this will forever be the case. No one is born an expert &ndash; expertise is gained by learning from and interacting with the world. Therefore, it's plausible that gaining expertise can and will be automated. Further, there are numerous cases where experts were proven to be wrong. For example, it wasn't so long ago that [doctors recommended smoking][12].

Despite the importance of domain knowledge, one can argue that scientists that specialise in a single domain are not data scientists. In fact, the ability to go beyond one domain and think of data in a more abstract manner is what makes a data scientist. Applying this abstract knowledge often requires some domain expertise or input from domain experts, but most data science techniques are not domain-specific &ndash; they can be applied to many different problems. John Hawkins explains this point well in an article titled _[why all scientists are not data scientists][13]_:

> Those scientists and statisticians who have focused themselves on understanding the limitations and possibilities of making inferences from experimental data are the ones who are the forerunners to data scientists. They have a skill which transcends the particulars of what it takes to do lab work on cell cultures, or field studies for ecology etc. Their core skill involves thinking about the data involved at an abstracted level. To ask the question "given data with these properties, what conclusions can we draw?" 

Finally, [according to Eugene Dubossarsky][14], _"there's only one purpose to data science, and that is to support decisions. And more specifically, to make better decisions. That should be something no one can argue with."_ This goal-focused definition is unsurprising, given the fact that Eugene runs a training and consulting business and has been working in the field for over 20 years. I'm not going to argue with him, but to put it all together, **we can define data science as a field that deals with description, prediction, and causal inference from data in a manner that is both domain-independent and domain-aware, with the ultimate goal of supporting decisions**.

## What about AI?

Everyone loves a good buzzword, and these days AI (Artificial Intelligence) is one of the hottest buzzwords. However, despite [what some people may try to tell you][15], AI is unlikely to make data science obsolete any time soon. Following the above definition, as long as there is a need to make decisions based on data, there will be a need for data scientists. This includes decisions that aren't made by humans, as data scientists are involved in building systems that make decisions autonomously.

The resurgence of AI feels somewhat amusing given my personal experience. One of the reasons I decided to pursue a PhD in natural language processing and personalisation was my interest in what I considered to be AI back in 2008. My initial introduction to the field was through an AI course and a project I did as part of my bachelor's degree in computer science. However, by the time I graduated from my PhD, saying that I'm an AI expert seemed less useful than calling myself a data scientist. It may be that the field is about to shift again, and that rebranding as an AI expert would be more beneficial (though I'd be doing exactly the same work). Titles are somewhat silly &ndash; I'm going to continue working with data to support decisions for as long as there is demand for this kind of work and I continue enjoying it. There is plenty to learn and develop in this area, regardless of buzzwords and sexy titles.

 [1]: https://hbr.org/2012/10/data-scientist-the-sexiest-job-of-the-21st-century
 [2]: https://yanirseroussi.com/2014/10/23/what-is-data-science/
 [3]: https://yanirseroussi.com/2016/08/04/is-data-scientist-a-useless-job-title/
 [4]: https://yanirseroussi.com/2017/07/29/my-10-step-path-to-becoming-a-remote-data-scientist-with-automattic/
 [5]: https://www.kaggle.com/
 [6]: https://yanirseroussi.com/2014/08/24/how-to-almost-win-kaggle-competitions/
 [7]: https://www.youtube.com/watch?v=YOIo09qjVl4
 [8]: https://eng.lyft.com/whats-in-a-name-ce42f419d16c
 [9]: https://www.youtube.com/watch?v=AoRSIdLpFqU
 [10]: https://arxiv.org/pdf/1804.10846.pdf
 [11]: https://yanirseroussi.com/2016/05/15/diving-deeper-into-causality-pearl-kleinberg-hill-and-untested-assumptions/
 [12]: https://www.healio.com/hematology-oncology/news/print/hemonc-today/%7B241d62a7-fe6e-4c5b-9fed-a33cc6e4bd7c%7D/cigarettes-were-once-physician-tested-approved
 [13]: https://www.linkedin.com/pulse/why-all-scientists-data-john-hawkins
 [14]: https://www.superdatascience.com/podcast-one-purpose-data-science-truth-analytics/
 [15]: https://www.forbes.com/sites/valleyvoices/2017/01/31/the-rise-of-ai-will-force-a-new-breed-of-data-scientist/
