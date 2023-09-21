---
title: Google's Rules of Machine Learning still apply in the age of large language models
author: Yanir Seroussi
type: til
date: 2023-09-21T21:30:00+00:00
url: /til/2023/09/21/googles-rules-of-machine-learning-still-apply-in-the-age-of-large-language-models/
summary: Despite the excitement around large language models, building with machine learning remains an engineering problem with established best practices.
showBreadcrumbs: true
tags:
  - artificial intelligence
  - data science
  - machine learning
  - software engineering 
---

I heard about [Google's Rules of Machine Learning (ML)](https://developers.google.com/machine-learning/guides/rules-of-ml) maybe 4-5 years ago. Much like [Steve McConnell's classic software engineering mistakes](https://yanirseroussi.com/2023/06/30/was-data-science-a-failure-mode-of-software-engineering/), the rules capture lessons learned from software engineering projects, though they are focused on the problems that arise from the engineering problem of shipping ML systems to production.

Despite the excitement about playing with data and models, the reality of building ML systems is that it's mostly an engineering problem. This remains the case in the age of large language models. Perhaps it's even more so because integrating language models into a product can be as simple as calling an API, which _should_ make it easier to focus on business problems, pipelines, data, and evaluation. It's important to remember that at an abstract level, ML is just a data transformation &ndash; there is no magic involved.

As the page containing Google's ML rules is long and detailed, I put together this TIL post for my own ease of reference. It contains the key quote from the overview, along with the rules without their explanations. Go to [the source](https://developers.google.com/machine-learning/guides/rules-of-ml) for further details.

<blockquote>

## Overview

To make great products:

**do machine learning like the great engineer you are, not like the great machine learning expert you aren't.**

Most of the problems you will face are, in fact, engineering problems. Even with all the resources of a great machine learning expert, most of the gains come from great features, not great machine learning algorithms. So, the basic approach is:

1. Make sure your pipeline is solid end to end.
2. Start with a reasonable objective.
3. Add common-sense features in a simple way.
4. Make sure that your pipeline stays solid.

## The Rules

### Before Machine Learning

1. Don't be afraid to launch a product without machine learning.
2. First, design and implement metrics.
3. Choose machine learning over a complex heuristic.

### ML Phase I: Your First Pipeline

4. Keep the first model simple and get the infrastructure right.
5. Test the infrastructure independently from the machine learning.
6. Be careful about dropped data when copying pipelines.
7. Turn heuristics into features, or handle them externally.

### Monitoring

8. Know the freshness requirements of your system.
9. Detect problems before exporting models.
10. Watch for silent failures.
11. Give feature columns owners and documentation.

### Your First Objective

12. Don't overthink which objective you choose to directly optimize.
13. Choose a simple, observable and attributable metric for your first objective.
14. Starting with an interpretable model makes debugging easier.
15. Separate Spam Filtering and Quality Ranking in a Policy Layer.

### ML Phase II: Feature Engineering

16. Plan to launch and iterate.
17. Start with directly observed and reported features as opposed to learned features.
18. Explore with features of content that generalize across contexts.
19. Use very specific features when you can.
20. Combine and modify existing features to create new features in human­-understandable ways.
21. The number of feature weights you can learn in a linear model is roughly proportional to the amount of data you have.
22. Clean up features you are no longer using.

### Human Analysis of the System

23. You are not a typical end user.
24. Measure the delta between models.
25. When choosing models, utilitarian performance trumps predictive power.
26. Look for patterns in the measured errors, and create new features.
27. Try to quantify observed undesirable behavior.
28. Be aware that identical short-term behavior does not imply identical long-term behavior.

### Training-Serving Skew

29. The best way to make sure that you train like you serve is to save the set of features used at serving time, and then pipe those features to a log to use them at training time.
30. Importance-weight sampled data, don't arbitrarily drop it!
31. Beware that if you join data from a table at training and serving time, the data in the table may change.
32. Re-use code between your training pipeline and your serving pipeline whenever possible.
33. If you produce a model based on the data until January 5th, test the model on the data from January 6th and after.
34. In binary classification for filtering (such as spam detection or determining interesting emails), make small short-term sacrifices in performance for very clean data.
35. Beware of the inherent skew in ranking problems.
36. Avoid feedback loops with positional features.
37. Measure Training/Serving Skew.

### ML Phase III: Slowed Growth, Optimization Refinement, and Complex Models

38. Don't waste time on new features if unaligned objectives have become the issue.
39. Launch decisions are a proxy for long-term product goals.
40. Keep ensembles simple.
41. When performance plateaus, look for qualitatively new sources of information to add rather than refining existing signals.
42. Don't expect diversity, personalization, or relevance to be as correlated with popularity as you think they are.
43. Your friends tend to be the same across different products. Your interests tend not to be.

</blockquote>
