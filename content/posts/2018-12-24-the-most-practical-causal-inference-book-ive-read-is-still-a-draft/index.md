---
title: The most practical causal inference book I’ve read (is still a draft)
author: Yanir Seroussi
type: post
date: 2018-12-24T02:37:50+00:00
url: /2018/12/24/the-most-practical-causal-inference-book-ive-read-is-still-a-draft/
cover:
  image: chicken-egg-roost.jpg
timeline_notification:
  - 1545619075
tags:
  - causal inference
  - causality
  - data science
  - statistics

---
I've been interested in the area of causal inference in the past few years. In my opinion [it's more exciting and relevant to everyday life than more hyped data science areas like deep learning][1]. However, I've found it hard to apply what I've learned about causal inference to my work. Now, I believe I've finally found a book with practical techniques that I can use on real problems: [_Causal Inference_][2] by Miguel Hernán and Jamie Robins. It is available for free from their site, but is still in draft mode. This post is a short summary of the reasons why I think _Causal Inference_ is a great practical resource.

One of the things that sets _Causal Inference_ apart from other books on the topic is the background of its authors. Hernán and Robins are both epidemiologists, which means they often have to deal with data with strong limitations on sample size and feasibility of experiments. Decisions driven by causal inference in epidemiology can often make the difference between life and death of individuals. Hence, the book is full of practical examples.

The book focuses on randomised controlled trials and well-defined interventions as the basis of causal inference from both experimental and observational data. As the authors show, even with randomised experiments, the analysis often requires using observational causal inference tools due to factors like selection and measurement biases. Their insistence on well-defined interventions is particularly refreshing, as one of the things that bothers me about the writings of Judea Pearl (a prominent researcher of causal inference) is [the vagueness of statements like _"smoking causes cancer"_ and _"mud doesn't cause rain"_][3]. The need for well-defined interventions was summarised by Hernán in the article [_Does water kill? A call for less casual causal inferences_][4].

Unlike some other resources, _Causal Inference_ doesn't appear to be too dogmatic about the framework used for modelling causality. I'm not an expert on where each idea originated, but it seems like the authors mix elements from the [potential outcomes framework][5] and from [Pearl's graphical models][6]. They also don't neglect time as an important consideration in cause-and-effect relationships. In fact, the third part of the book is dedicated to the topic of time-varying treatments and effects.

The practicality of the book is also demonstrated by the fact that it comes with code examples in multiple languages. In addition, the authors don't dwell too much on the philosophy of causality. While it is a fascinating topic, the opening paragraphs of the book make its goals clear:

> By reading this book you are expressing an interest in learning about causal inference. But, as a human being, you have already mastered the fundamental concepts of causal inference. You certainly know what a causal effect is; you clearly understand the difference between association and causation; and you have used this knowledge constantly throughout your life. In fact, had you not understood these causal concepts, you would have not survived long enough to read this chapter–or even to learn to read. As a toddler you would have jumped right into the swimming pool after observing that those who did so were later able to reach the jam jar. As a teenager, you would have skied down the most dangerous slopes after observing that those who did so were more likely to win the next ski race. As a parent, you would have refused to give antibiotics to your sick child after observing that those children who took their medicines were less likely to be playing in the park the next day.
> 
> Since you already understand the definition of causal effect and the difference between association and causation, do not expect to gain deep conceptual insights from this chapter. Rather, the purpose of this chapter is to introduce mathematical notation that formalizes the causal intuition that you already possess. Make sure that you can match your causal intuition with the mathematical notation introduced here. This notation is necessary to precisely define causal concepts, and we will use it throughout the book. 

I won't try to summarise the technical aspects of the book &ndash; partly because I don't fully understand it all, and partly because the book itself is already a summary of a very rich research area. However, I'm likely to go back and reread the book in the future, with the goal of applying the techniques from the book to my work. I'd also like to take [Hernán's causal inference course][7] as a way of practising what I've learned from the book. For people who want a non-technical summary of the topics covered by the book, I recommend the article [_The c-word: Scientific euphemisms do not improve causal inference from observational data_][8]. If you're curious about other (less practical) causality books I've read, check out [my causal inference reading list][9] and my two previous posts on the topic: [_Why you should stop worrying about deep learning and deepen your understanding of causality instead_][1] and [_Diving deeper into causality: Pearl, Kleinberg, Hill, and untested assumptions_][3].

 [1]: http://yanirseroussi.com/2016/02/14/why-you-should-stop-worrying-about-deep-learning-and-deepen-your-understanding-of-causality-instead/
 [2]: https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/
 [3]: http://yanirseroussi.com/2016/05/15/diving-deeper-into-causality-pearl-kleinberg-hill-and-untested-assumptions/
 [4]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5207342/
 [5]: https://en.wikipedia.org/wiki/Rubin_causal_model
 [6]: https://en.wikipedia.org/wiki/Structural_equation_modeling
 [7]: https://www.edx.org/course/causal-diagrams-draw-assumptions-harvardx-ph559x
 [8]: https://ajph.aphapublications.org/doi/10.2105/AJPH.2018.304337
 [9]: https://yanirseroussi.com/causal-inference-reading-list/
