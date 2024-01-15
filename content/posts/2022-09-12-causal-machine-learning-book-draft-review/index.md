---
title: "Causal Machine Learning is off to a good start, despite some issues"
author: Yanir Seroussi
type: post
date: 2022-09-12T02:45:00+00:00
url: /2022/09/12/causal-machine-learning-book-draft-review/
cover:
  relative: true
  image: dall-e-a-steampunk-painting-of-a-data-scientist-reading-a-book-about-causal-machine-learning.png
  caption: "[DALL·E](https://labs.openai.com/)'s _steampunk painting of a data scientist reading a book about causal machine learning_."
summary: Reviewing the first three chapters of the book Causal Machine Learning by Robert Osazuwa Ness.
tags:
  - artificial intelligence
  - causal inference
  - data science
  - machine learning

---
I was recently given a free eBook copy of the MEAP of [_Causal Machine Learning_](https://www.manning.com/books/causal-machine-learning). [MEAP stands for Manning Early Access Program](https://www.manning.com/meap-program), where books are published one chapter at a time. While the current version could use better copyediting and proofreading, I'm keen on reading more of the book as it becomes available.

_Causal Machine Learning_ addresses a gap in the causal inference literature: While [much has been published on the topic](https://yanirseroussi.com/causal-inference-reading-list/), putting the theory to practice in the real world can be challenging. For example, even though I considered [_Causal Inference: What If_](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/) to be [the most practical book I've read on the topic](https://yanirseroussi.com/2018/12/24/the-most-practical-causal-inference-book-ive-read-is-still-a-draft/), I haven't used much of its content directly. This is partly due to my focus on other areas, e.g., [online experimentation](https://yanirseroussi.com/2022/01/14/analysis-strategies-in-online-a-b-experiments/) and [the energy space](https://yanirseroussi.com/2022/06/06/the-mission-matters-moving-to-climate-tech-as-a-data-scientist/). But it is also due to the availability of sample code and mature packages that can be quickly adapted to my needs. The book aims to address the latter through a code-first approach that utilises Python packages such as [Pyro](https://pyro.ai/), [pgmpy](https://pgmpy.org/), and [DoWhy](https://py-why.github.io/dowhy/).

Despite the code-first promise, the book feels a bit slow at getting into the more exciting content. I couldn't help but compare it to [the fast.ai book](https://github.com/fastai/fastbook), which first shows how to build and deploy a custom image classifier, and only then goes into unpacking how it all works. However, despite the verbosity of the first two chapters, by the third chapter things start to get more interesting. At the time of this writing, only chapters 1-3 are available, but upcoming chapters look promising based on the table of contents.

  While lacking a production-ready example early in the book is a minor concern, I found the many grammatical errors more distracting. Even though a MEAP is essentially a draft, I think its proofreading level should be higher than that of a blog post.[^inevitable-mistakes] This is especially the case for paid content published by an organisation that cares enough to have contacted me to promote the book. As Steven Pinker says in the intro to [The Sense of Style](https://stevenpinker.com/publications/sense-style-thinking-persons-guide-writing-21st-century):

> Style earns trust. If readers can see that a writer cares about consistency and accuracy in her prose, they will be reassured that the writer cares about those virtues in conduct they cannot see as easily. Here is how one technology executive explains why he rejects job applications filled with errors of grammar and punctuation: "If it takes someone more than 20 years to notice how to properly use it's, then that's not a learning curve I'm comfortable with." And if that isn't enough to get you to brush up your prose, consider the discovery of the dating site OkCupid that sloppy grammar and spelling in a profile are "huge turn-offs." As one client said, "If you're trying to date a woman, I don't expect flowery Jane Austen prose. But aren't you trying to put your best foot forward?"

Another source of distraction is the choice of variables for some of the toy examples. For instance, one model of blood type inheritance confuses the phenotype and genotype, claiming that _"knowing your grandfather's \[blood\] type has no benefit in predicting your type once we know your father's"_. However, [knowing the grandparents' blood types _can_ help predict the grandchild's blood type even when the parent's blood type is known](https://en.wikipedia.org/wiki/ABO_blood_group_system#Genetics). The toy example would work if it focused on genotypes, not on the common meaning of _blood type_ as the phenotype (i.e., observable traits). See [pages 58-60 in Probabilistic Graphical Models: Principles and Techniques](https://books.google.com.au/books?id=7dzpHCHzNQ4C&lpg=PA59&ots=px4BFm4XAP&pg=PA58#v=onepage&q&f=false) for a less casual presentation of a similar example.

{{< figure src="wikipedia-blood-group-inheritance-table.png" caption="When observing parent phenotypes (ABO blood types) without genotypes, grandparent phenotypes are informative.<br>Source: [Wikipedia &ndash; ABO blood group system](https://en.wikipedia.org/wiki/ABO_blood_group_system#Genetics) (retrieved on 2022-09-11)." >}}

I also struggle with overly-casual statements like this one:

> Suppose we were interested in modeling the relationship between altitude and temperature. The two are clearly correlated; the higher up you go, the colder it gets. However, you know temperature doesn't cause altitude, otherwise heating the air within a city would cause the city to fly. Altitude is the cause, and temperature is the effect.

In fact, heating the air within a city _would_ cause the heated air to rise. And extremely high heat can melt a city and the land it's on, thereby causing a reduction in its altitude.

While this may seem like nitpicking, ill-defined causal graphs are a serious problem. One of my favourite papers on the topic is [_Does water kill? A call for less casual causal inferences_](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5207342/), which argues that _"\[while\] it is impossible to provide an absolutely precise definition of a version of treatment \[...\] specification of versions of treatment is required only until no meaningful vagueness remains"_. However, _"declaring a version of treatment sufficiently well-defined is a matter of agreement among experts based on the available substantive knowledge"_ because we don't have an objective way of determining that treatments are well-defined. In line with this thinking, the book may benefit from reducing the variety of examples in favour of a handful of small datasets that are more well-defined and defensible.

Despite these shortcomings, I found chapters 1-3 of _Causal Machine Learning_ pleasant enough to get through, and I look forward to reading more. Getting into DoWhy and other related packages has been on my list, and I'm sure I'll learn a lot by following the MEAP. After tracking the field for almost a decade and complaining about [the relative hype levels of deep learning and causal inference](https://yanirseroussi.com/2016/02/14/why-you-should-stop-worrying-about-deep-learning-and-deepen-your-understanding-of-causality-instead/), it's great to see a practical book that aims to marry the two. [The Causal Revolution](https://arxiv.org/abs/1801.04016) is truly upon us.

[^inevitable-mistakes]: It is almost inevitable that when pointing out the mistakes of others I will make mistakes myself. I apologise for any mistakes and welcome feedback. 
