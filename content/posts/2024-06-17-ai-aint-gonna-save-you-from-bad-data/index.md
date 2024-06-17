---
title: AI ain't gonna save you from bad data
author: Yanir Seroussi
type: post
date: 2024-06-17T02:00:00+00:00
url: /2024/06/17/ai-aint-gonna-save-you-from-bad-data/
cover:
  relative: true
  image: helpless-robot-with-data-monster.webp
  alt: bad data monster with a helpless robot
summary: Since we're far from a utopia where data issues are fully handled by AI, this post presents six questions humans can use to assess data projects.
tags:
  - artificial intelligence
  - data science
  - data strategy
  - startups
---
Now that we have generative AI, we no longer need to worry about data, right? Well, we're not quite there yet. On their own, ChatGPT, Gemini, and their friends can't save us from bad decisions around data collection and modelling, or from poorly-designed metrics.

While we wait for better AI agents to replace data scientists and engineers, I propose we ask a standard set of six questions about the data health of any project. These questions come from [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/), but they apply anywhere. You can use them as a starting point when joining a new initiative, or to assess the state of an existing project.

Before we start, note that the goal is to identify gaps as opportunities for improvement. It's easy to see data issues as insurmountable, but despair isn't a viable data strategy. Aim to adopt [Stockdale-style optimism](https://en.wikipedia.org/wiki/James_Stockdale#The_Stockdale_Paradox) when dealing with data:

> You must never confuse faith that you will prevail in the end &ndash; which you can never afford to lose &ndash; with the discipline to confront the most brutal facts of your current reality, whatever they might be.

As with other posts in the health check series, this post provides a brief explanation for every question.

Let's jump in.

## The questions

**Q1: Do you track Kukuyeva's five business aspects as wide events?**

This question is foundational, as inadequate instrumentation often makes data-informed decisions impossible. Given its importance, I wrote [a separate post on this question](https://yanirseroussi.com/2024/06/10/startup-data-health-starts-with-healthy-event-tracking/).

The short story is that you _need_ event-based tracking and event data modelling of key aspects of the business and product. Events are essentially timestamped mappings. For example, a customer purchase is an event that should be logged along with metadata on the customer and platform at the time of purchase.

**Q2: Is there data you need that isn't collected or is inaccessible? What is stopping you from obtaining it?**

While Q1 covers high-level event tracking, Q2 brings it down to specific needs.

Sometimes, data can't be collected due to practical or legal reasons. In some cases, other data can serve as a proxy. For example, companies are typically interested in measuring  "customer satisfaction", but asking directly about satisfaction suffers from a host of problems (e.g., not everyone responds, and the timing and phrasing of questions influence answers). Instead, customer satisfaction can be partly inferred from behaviour like repeat purchases &ndash; but that's also not perfect.

In any case, seeking perfection in data is a recipe for disappointment. You should start with business needs and find the data to best address them within a reasonable timeframe.

**Q3: On a scale of 1 to 5, rate the quality of your key datasets. If you're unsure due to limited observability and quality checks, it's a 1.**

This question should be answered by those who are closest to the data: usually data engineers, scientists, analysts, or one of the dozens of other titles data specialists go by. An experienced data specialist would have a subjective sense of data quality, so it's worth agreeing on [quality definitions](https://en.wikipedia.org/wiki/Data_quality) if the rating is done by multiple people. Generally, a dataset is of high quality if it's fit for its intended uses in [decisions and automation](https://yanirseroussi.com/2024/05/27/plumbing-decisions-and-automation-de-hyping-data-and-ai/). 

Again, absolute perfection is impossible: Data is a model of the world, and [_all models are wrong, but some are useful_](https://en.wikipedia.org/wiki/All_models_are_wrong).

**Q4: On a scale of 1 to 5, what is the confidence of stakeholders in the data and metrics that are used to make business decisions? Explain why.**

Low data quality often leads to low trust and confidence in the outputs of data specialists. However, that's not always the case. Sometimes, stakeholders may have high confidence in metrics because they're unaware of underlying data issues. In other cases, confidence is low due to historical reasons: Trust takes time to build &ndash; it is a trailing indicator of consistently making and keeping promises. Data specialists are sometimes enamoured with fancy tech and tools, neglecting simple wins that are at the foundation of [data's hierarchy of needs](https://yanirseroussi.com/2014/08/17/datas-hierarchy-of-needs/). After decades of hype (from big data through data science to AI agents), I can see why many people treat anything that falls under Data & AI with suspicion. If you're a data specialist, serving your customers with relevant trustworthy data can be a rare delight.

**Q5: If you are currently using advanced AI/ML, do you have all the data you need for the models to perform as accurately as required?**

By advanced AI/ML, I mean fine-tuning or building machine learning models from scratch. This is distinct from basic AI/ML, which relies on third-party models as black boxes. For example, calling a vision API to extract text from images is basic AI/ML. Training a model on your proprietary image data is advanced AI/ML. The latter requires data of sufficient quality for model accuracy, where sufficient accuracy depends on the application.

Implicit in this question are satisfactory answers to Q1-Q3: You need to be tracking advanced AI/ML performance in the context where it's used (Q1), have access to the data you need (Q2), and ensure that data quality is fit for advanced AI/ML (Q3). Advanced AI/ML is hard to do well, and failure can erode stakeholder trust (Q4). However, "failure" depends on expectations &ndash; AI/ML models are probabilistic, so setting the right expectations is key. For example, as ChatGPT has shown, it's possible to build a useful consumer product on top of an AI/ML model that is often wrong.

**Q6: If you are planning new advanced AI/ML projects, do you have all the data you need for them? If not, what is the effort required to obtain the data? Is it time-sensitive (e.g., ingesting a public dataset is less time-sensitive than starting to collect timestamped proprietary data)?**

This is the future-oriented version of Q5. It's best to think of data and metrics _before_ kicking off advanced AI/ML projects. Further, [it's better to start without AI/ML than over-complicate things early on](https://yanirseroussi.com/til/2023/09/21/googles-rules-of-machine-learning-still-apply-in-the-age-of-large-language-models/).

In short, user needs should inform project decisions on what to build. These decisions and plans then inform data collection. Don't make the common mistake of starting with shiny tech as the proverbial hammer that's looking for nail-shaped problems.

## Don't forget the opportunities!

Data is much like solar energy: It exists even if you don't capture it, and most of it bounces back to space unused. Harnessed wisely, it can power business decisions and become a differentiator for your product.

However, when working closely with data, it's easy to feel despair due to the never-ending stream of quality issues and stakeholder requests. I've felt this despair myself many times.

For me, the cure for data despair comes from shifting focus from gaps to opportunities:

1. Map the current state of data, including key gaps.
2. Learn about relevant business opportunities from internal/external customers and industry peers.
3. Create a plan to incrementally improve the state of data, and seize opportunities starting with the lowest-hanging fruit.
4. Execute the plan.
5. Repeat steps 1-4 periodically.

##  Data-to-AI health beyond abstract data

This post is part of a series on [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/). Previous posts:

* [Assessing a startup's data-to-AI health: Overview and motivation](https://yanirseroussi.com/2024/04/22/assessing-a-startups-data-to-ai-health/)
* [Business questions to ask before taking a startup data role](https://yanirseroussi.com/2024/05/06/business-questions-to-ask-before-taking-a-startup-data-role/)
* [Probing the People aspects of an early-stage startup](https://yanirseroussi.com/2024/05/13/probing-the-people-aspects-of-an-early-stage-startup/)
* [Question startup culture before accepting a data-to-AI role](https://yanirseroussi.com/2024/05/20/question-startup-culture-before-accepting-a-data-to-ai-role/)
* [Plumbing, Decisions, and Automation: De-hyping Data & AI](https://yanirseroussi.com/2024/05/27/plumbing-decisions-and-automation-de-hyping-data-and-ai/)
* [How to avoid startups with poor development processes](https://yanirseroussi.com/2024/06/03/how-to-avoid-startups-with-poor-development-processes/)
* [Startup data health starts with healthy event tracking](https://yanirseroussi.com/2024/06/10/startup-data-health-starts-with-healthy-event-tracking/)

[You can download a guide containing all the questions as a PDF](https://yanirseroussi.com/data-to-ai-health-check/). Next, I'll go into the questions from the Tech section, which are directly related to how the abstract Data questions manifest in practice. Feedback is always welcome!
