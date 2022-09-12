---
title: Causal inference resources
author: Yanir Seroussi
aliases:
  - /causal-inference-reading-list/
type: page

---
This is a list of some causal inference resources, which I update from time to time. You can also check out my posts on [causal inference](/tags/causal-inference/) and [A/B testing](/tags/a/b-testing/).

**Books**:

  * [_Causal Inference: What if_](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/) by Miguel Hernán and Jamie Robins: [The most practical book I've read](https://yanirseroussi.com/2018/12/24/the-most-practical-causal-inference-book-ive-read-is-still-a-draft/). Highly recommended.
  * [_Trustworthy Online Controlled Experiments : A Practical Guide to A/B Testing_](https://experimentguide.com/) by Ron Kohavi, Diane Tang, and Ya Xu: Building on the authors' decades of industry experience, this is pretty much the bible of online experiments, which is how causal inference is often done in practice.
  * [_Why: A Guide to Finding and Using Causes_][3] by Samantha Kleinberg: A high-level intro to the topic. I discussed highlights in [_Why you should stop worrying about deep learning and deepen your understanding of causality instead_][4].
  * [_Causality, Probability, and Time_][5] by Samantha Kleinberg: More technical than Kleinberg's other book. As the title suggests, the element of time is central to the methods presented in the book. However, I'm still unsure about the practicality of those methods on real data. See my post [_Diving deeper into causality: Pearl, Kleinberg, Hill, and untested assumptions_][6] for more details.
  * [_Causal Inference in Statistics: A Primer_][7] by Judea Pearl, Madelyn Glymour, Nicholas P. Jewell: A fairly accessible introduction to Judea Pearl's work. I didn't find it that practical, but I believe it helped me understand the graphical modelling parts of _Causal Inference_ by Hernán and Robins.
  * [_Elements of Causal Inference: Foundations and Learning Algorithms_][8] by Jonas Peters, Dominik Janzing, and Bernhard Schölkopf: The name of the book is an obvious reference to the classic book [_The Elements of Statistical Learning_][9] by Trevor Hastie, Robert Tibshirani, and Jerome Friedman. Unfortunately, the _Elements of Causal Inference_ isn't as widely applicable as Hastie et al.'s book &ndash; it contains some interesting ideas, but it appears that algorithms for causal learning from data with minimal assumptions aren't yet scalable enough for practical use. This will probably change in the future.
  * [_Mostly Harmless Econometrics_][10] by Joshua D. Angrist and Jörn-Steffen Pischke: I started reading this book on my Kindle and was put off by some formatting issues. It also seemed like a less-general version of Pearl's work. I may get back to it one day.
  * [_Causality: Models, Reasoning, and Inference_][11] by Judea Pearl: I haven't read it, and I doubt it'd be very practical given [the opinions of people who have][12]. But maybe I'll get to it one day.
  * [_The Book of Why: The New Science of Cause and Effect_][13] by Judea Pearl and Dana Mackenzie: An accessible overview of the field, focusing on Pearl's contributions, but with plenty of historical background. Worth reading to get excited about the causal revolution.
  * [_Causal Machine Learning_](https://www.manning.com/books/causal-machine-learning) by Robert Osazuwa Ness: Still a draft as of September 2022, but [it looks promising](https://yanirseroussi.com/2022/09/12/causal-machine-learning-book-draft-review/).

**Articles**:

  * [_Does water kill? A call for less casual causal inferences_][14] by Miguel Hernán: A great demonstration of why talking about causality requires well-defined interventions.
  * [_The C-Word: Scientific Euphemisms Do Not Improve Causal Inference From Observational Data_][15] by Miguel Hernán: A high-level summary of causal inference and the need to be explicit about the causal goals of scientific studies.
  * [_The Environment and Disease: Association or Causation?_][16] by Austin Bradford Hill: A classic discussion of [the Bradford Hill criteria for causation][17]. Highly recommended, as this 1965 paper also foresaw the problems with the statistical significance cult.
  * [_Causal inference in statistics: An overview_][18] by Judea Pearl: A summary of Pearl's work, which may be somewhat dated at this point (it's from 2009). It's still worth reading if you're not ready to commit to reading his books.
  * [_Simpson's Paradox: An Anatomy_][19] by Judea Pearl: An explanation of [Simpson's paradox][20] and its relationship to causal inference. This paper is worth reading, though I found that further reading is required to better understand why causal modelling "solves" the paradox.
  * [_Guidelines for estimating causal effects in pragmatic randomized trials_](https://arxiv.org/abs/1911.06030) by Eleanor J. Murray, Sonja A. Swanson, and Miguel A. Hernán. Once you get over the terminology gap, you see how these guidelines apply to any field where experiments don't always go as planned.

**Courses**:

  * [_Causal Diagrams: Draw Your Assumptions Before Your Conclusions_](https://www.edx.org/course/causal-diagrams-draw-your-assumptions-before-your). A high-level introduction to causal diagrams by Miguel Hernán. Highly recommended for those who want to get a conceptual overview of how causal diagrams work and why they're useful.
  * [_A/B Testing by Google: Online Experiment Design and Analysis_](https://www.udacity.com/course/ab-testing--ud257). Experimentation is key to causal inference, with the online world offering an accessible ground for running experiments. This short course is worth doing if you're involved in online experiments in any way.

 [3]: http://www.skleinberg.org/why/
 [4]: https://yanirseroussi.com/2016/02/14/why-you-should-stop-worrying-about-deep-learning-and-deepen-your-understanding-of-causality-instead/
 [5]: http://www.skleinberg.org/causality_book/index.html
 [6]: https://yanirseroussi.com/2016/05/15/diving-deeper-into-causality-pearl-kleinberg-hill-and-untested-assumptions/
 [7]: http://bayes.cs.ucla.edu/PRIMER/
 [8]: https://mitpress.mit.edu/books/elements-causal-inference
 [9]: https://web.stanford.edu/~hastie/ElemStatLearn/
 [10]: http://www.mostlyharmlesseconometrics.com/
 [11]: http://bayes.cs.ucla.edu/BOOK-2K/index.html
 [12]: https://www.reddit.com/r/statistics/comments/8lu1sr/causal_inference_book_recommendations/
 [13]: http://bayes.cs.ucla.edu/WHY/
 [14]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5207342/
 [15]: https://ajph.aphapublications.org/doi/10.2105/AJPH.2018.304337
 [16]: https://www.edwardtufte.com/tufte/hill
 [17]: https://en.wikipedia.org/wiki/Bradford_Hill_criteria
 [18]: http://ftp.cs.ucla.edu/pub/stat_ser/r350.pdf
 [19]: http://bayes.cs.ucla.edu/R264.pdf
 [20]: https://en.wikipedia.org/wiki/Simpson%27s_paradox
