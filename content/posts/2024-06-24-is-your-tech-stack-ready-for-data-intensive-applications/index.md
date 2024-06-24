---
title: Is your tech stack ready for data-intensive applications?
author: Yanir Seroussi
type: post
date: 2024-06-24T02:00:00+00:00
url: /2024/06/24/is-your-tech-stack-ready-for-data-intensive-applications/
cover:
  relative: true
  image: modern-tech-stack.webp
  alt: a stack of computers, wires, and hay in an office area
summary: 'Questions to assess the quality of tech stacks and lifecycles, with a focus on artificial intelligence, machine learning, and analytics.'
tags:
  - analytics
  - artificial intelligence
  - data science
  - data strategy
  - machine learning
  - software engineering
  - startups
---
Data-intensive projects fail when you treat them like traditional software projects. But they also fail when you don't apply best practices from software engineering.

Why?

Because data-intensive systems are made of data, and also made of software. Therefore:

1. data changes can lead to failures; and
2. software changes can lead to failures.

In traditional software systems, you fully control the changes. Your software doesn't change unexpectedly.

In data-intensive systems, you cede control to the data. The data changes constantly, and it affects the behaviour of your system.

To succeed, you need to manage both the data and software aspects of your systems. This successful management is the essence of the questions from the Tech section of [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/). This post presents the questions along with guidance on what constitutes healthy answers.

## What do I mean by data intensity?

For the last few months, I have set my LinkedIn tagline to _"helping startups ship data-intensive solutions (AI/ML for climate/nature tech)"_. I landed on it after a bit of a struggle with succinctly defining exactly what it is I do.

The problem is that after over a decade of "data" roles, I don't see the field of AI/ML (artificial intelligence and machine learning) as a sanctified sphere that's separate from real-world data and humans. Further, while business intelligence (aka analytics) is seen by some as less "sexy" than AI/ML, I see it as a different lens of using data to drive business outcomes. Essentially, it all comes down to [plumbing, decisions, and automation](https://yanirseroussi.com/2024/05/27/plumbing-decisions-and-automation-de-hyping-data-and-ai/).

In the days of the Big Data hype, much attention was given to the three Vs of data: Volume, Velocity, and Variety &ndash; what flows through the plumbing. To me, data intensity goes beyond the three Vs. This is how I define it in the first section of my Data-to-AI Health Check:

> High data intensity typically requires low-latency processing of large volumes of data with more than one database server. With high intensity, data processing issues noticeably affect key business metrics.

That is, in data-intensive settings, data issues affect decisions and automation in a way that hurts the business.

A couple of examples may help:
* Low intensity: A dashboard that doesn't contain any actionable metrics. If the metrics change due to bugs in the data processing, it doesn't affect decisions.
* High intensity: An ad-serving platform that personalises ads in real time based on numerous data points. If any model or system breaks, millions of dollars may be lost.

In short, **the higher the data intensity, the more the flow of data affects the bottom line**.

## Understanding tech stacks and lifecycles

At 15 questions, the Tech section of [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/) is long and deep. To keep this post digestible, I won't go into every question. Instead, I've grouped the questions by theme.

First up, on the tech stacks and lifecycles:

> * Q1: Provide an architecture diagram for your tech systems (product and data stacks), including first-party and third-party tools and databases. If a diagram doesn't exist, an ad hoc drawing would work as well.
> * Q2: Zooming in on data stacks, what tools and pipelines do you use for the [data engineering lifecycles (generation, storage, ingestion, transformation, and serving)](https://yanirseroussi.com/til/2024/04/05/the-data-engineering-lifecycle-is-not-going-anywhere/), and downstream uses (analytics, AI/ML, and reverse ETL)?
> * Q3: Zooming in further on the downstream uses of analytics and AI/ML, what systems, processes, and tools do you use to manage their lifecycles (discovery, data preparation, model engineering, deployment, monitoring, and maintenance)? Give specific project examples.
> * Q4: Are there any tech choices you regret? Why?
> * Q5: Are there any new tools you want to introduce to your stack? Why?

To an extent, tech stacks and lifecycles follow [the Anna Karenina principle](https://en.wikipedia.org/wiki/Anna_Karenina_principle): _All healthy stacks are alike; each unhealthy stack is unhealthy in its own way._

By asking for their descriptions, I'm aiming to uncover gaps and opportunities.

Often, some gaps are known to the people in charge, but they haven't been explicitly discussed. This is especially common in startups, where competing priorities and resource constraints require compromising on scope and quality to fuel growth. In addition, it's impossible for small startups to have all the relevant experts on the founding team, so best practices aren't followed due to ignorance rather than due to intentional compromises made to move fast. However, a lack of awareness of best practices can often lead to the startup moving too slowly.

Two concrete examples:

* many people outside the data world are unaware of recent advances in tooling for management of data transformations ([dbt](https://www.getdbt.com/product/what-is-dbt) and its competitors), and
* practitioners who've only built ML models in academia rarely appreciate the complexity of running ML in production ([MLOps](https://en.wikipedia.org/wiki/MLOps) is much more than ML).

Beyond gaps that may be exposed by Q1-Q3, explicitly asking about regrettable and future tech choices (Q4 & Q5) helps surface evidence of an overreliance on unproven or exotic tech (aka [wasted innovation tokens](https://boringtechnology.club/)) and an underreliance on proven tech (aka reinvention of wheels). This is especially common with [inexperienced operators who are too excited about playing with shiny tools](https://yanirseroussi.com/2023/10/25/lessons-from-reluctant-data-engineering/). Use of unproven tech should be reserved to the cases where it confers a competitive advantage (e.g., being first to market with the latest AI advances).

## Basic quality assurance and delivery

The next set of questions covers what I consider to be the basics of quality assurance and continuous delivery:

> * Q6: How do you test product code and infrastructure setup? How good is the coverage (formally – percentage of statements covered, and conceptually – confidence from 1 to 5 that tests capture faults prior to deployment)?
> * Q7: Do all tests run automatically on every version of the code?
> * Q8: Are deployments done as a single automated step (e.g., push new containers to production when the main branch is updated)?
> * Q9: How faithful are development, testing, and staging environments to the production setup? Are there gaps that can be feasibly addressed? If so, what is stopping you from addressing them?

As I'm writing this in 2024, all the tooling exists to set things up with solid testing and deployment processes &ndash; and it's constantly getting easier. The only place where such processes may be skipped is in throwaway prototypes, where testing unnecessarily slows things down.

Being a startup is also not an excuse. [As Martin Fowler pointed out years ago](https://martinfowler.com/articles/is-quality-worth-cost.html), the _internal_ quality of software doesn't incur a cost. That is, by implementing solid systems and processes for automated testing and deployment, teams move faster. Teams that cut corners on internal quality may move faster in the _very_ short term, but typically get overtaken by their higher-internal-quality counterparts within weeks.

No startup aims to be around only for a few weeks, so investing in internal quality is key to tech health.

In Fowler's words:

> * Neglecting internal quality leads to rapid build up of cruft
> * This cruft slows down feature development
> * Even a great team produces cruft, but by keeping internal quality high, is able to keep it under control
> * High internal quality keeps cruft to a minimum, allowing a team to add features with less effort, time, and cost

Unfortunately, some software engineers never learn this lesson. Further, data professionals that don't have a software background are even less likely to be exposed to the importance of internal quality and how it can be enforced.

That said, it's never too late to learn and improve. This is key to avoiding failure modes that arise in data projects when best practices from software engineering aren't applied.

## Specific data-intensive failure modes

The next set of questions probes for failure modes that are specific to data-intensive work (data engineering, analytics, AI/ML, etc.):

> * Q10: Do you apply the same standards of testing and deploying product code to data? For example, is there untested SQL code hidden in dashboarding tools or the database layer, or is SQL treated like core product code (tracked in source control with isolated testing)?
> * Q11: How are schema changes managed and tested in each data system?
> * Q12: Do you rely on notebooks for production data code? If so, how do you ensure that notebook code meets the same quality standards as core product code (especially around testing and change management)?
> * Q13: Do advanced AI/ML projects meet your performance expectations? If not, do you know how to improve performance without data changes?

Data-intensive work is essentially about building models with software:

* Raw data is a model of real-world entities and events, expressed in database schemas (even "schemaless" databases have a schema &ndash; it's just unbounded).
* Dashboards present models of metrics that originate in raw data, with the goal of informing decisions.
* AI/ML models are essentially complex data transformations, e.g., from a matrix of pixels to a probability that the image modelled by the pixels is of a cat or a dog.

Due to historical and practical reasons, much of this modelling work is done by people with no training in software engineering. While [the industry is maturing](https://yanirseroussi.com/2023/06/30/was-data-science-a-failure-mode-of-software-engineering/), Q10-13 often expose gaps. The ideal answer to each question is that all models are fully tested and managed &ndash; just like software, but with [extra care for the complexity introduced by data](https://yanirseroussi.com/2024/04/15/ai-does-not-obviate-the-need-for-testing-and-observability/).

## Maintaining long-term success

Finally, the last two questions cover monitoring and maintenance:

> * Q14: On a scale of 1 to 5, how confident are you in detecting and addressing issues in production (including product, infra, data, and [ML observability 1.0 & 2.0](https://twitter.com/mipsytipsy/status/1738048200630792245))? Do you have action plans to increase your level of confidence?
> * Q15: What DevOps, DataOps, and MLOps practices do you follow that weren't covered above? Are there known gaps and plans to address them?

Even if a data-intensive project is considered "done", it still changes in production due to its dependence on data. The degree of likely change varies by project, but it needs to be actively managed for long-term success.

##  Data-to-AI health beyond the tech

This post is part of a series on [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/). Previous posts:

* [Assessing a startup's data-to-AI health: Overview and motivation](https://yanirseroussi.com/2024/04/22/assessing-a-startups-data-to-ai-health/)
* [Business questions to ask before taking a startup data role](https://yanirseroussi.com/2024/05/06/business-questions-to-ask-before-taking-a-startup-data-role/)
* [Probing the People aspects of an early-stage startup](https://yanirseroussi.com/2024/05/13/probing-the-people-aspects-of-an-early-stage-startup/)
* [Question startup culture before accepting a data-to-AI role](https://yanirseroussi.com/2024/05/20/question-startup-culture-before-accepting-a-data-to-ai-role/)
* [Plumbing, Decisions, and Automation: De-hyping Data & AI](https://yanirseroussi.com/2024/05/27/plumbing-decisions-and-automation-de-hyping-data-and-ai/)
* [How to avoid startups with poor development processes](https://yanirseroussi.com/2024/06/03/how-to-avoid-startups-with-poor-development-processes/)
* [Startup data health starts with healthy event tracking](https://yanirseroussi.com/2024/06/10/startup-data-health-starts-with-healthy-event-tracking/)
* [AI ain't gonna save you from bad data](https://yanirseroussi.com/2024/06/17/ai-aint-gonna-save-you-from-bad-data/)

[You can download a guide containing all the questions as a PDF](https://yanirseroussi.com/data-to-ai-health-check/). Next, I'll go into the questions from the Security & Compliance section. Feedback is always welcome!
