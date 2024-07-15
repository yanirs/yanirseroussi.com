---
title: Learn about Dataland to avoid expensive hiring mistakes
author: Yanir Seroussi
type: post
date: 2024-07-15T05:30:00+00:00
url: /2024/07/15/learn-about-dataland-to-avoid-expensive-hiring-mistakes/
cover:
  relative: true
  image: cover.webp
  alt: screenshot of Yanir Seroussi presenting a slide from the webinar
summary: Video and key points from the first part of a webinar on a startup's first data hire, covering data & AI definitions and high-level recommendations.
tags:
  - analytics
  - artificial intelligence
  - data engineering
  - data science
  - data strategy
  - startups
  - video
---
This week, I will present a webinar on hiring a startup's first Data-to-AI specialist.

Why Data-to-AI rather than Data & AI?

Because AI isn't distinct from Data &ndash; AI is built on data. Further, [solid data plumbing underlies both analytics and advanced AI/ML](https://yanirseroussi.com/2014/08/17/datas-hierarchy-of-needs/). Despite the hype, descriptive models (aka analytics) are often as critical as predictive and causal models (aka advanced AI/ML & statistics).

As practice for the webinar, I recorded myself going through the first part of the deck. I'm a bit uncomfortable watching myself, which makes sharing the video an especially valuable exercise:

<p>
  {{< youtube yqexINnrZMs >}}
</p>

The full slides are [here](https://yanirseroussi.com/talks/first-data-hire/#/) (use the left/right and up/down arrows to navigate).

## Key points from the video

These are the key points covered in the video, along with a couple of pointers to relevant posts:

- Intro: The intended audience and my relevant background.
- **Main goal of the webinar: Avoid expensive mistakes** &ndash; remembering that the cost of a _wrong_ hire entails compensation + slowdown + opportunity.
- Sub-goals:
  - De-hype Data & AI
  - Clarify needs & opportunities
  - Consider not hiring
  - Hire well
  - Avoid pitfalls
- **Dataland is Venn diagram paradise** &ndash; but startups need not worry about Dataland Venns. The lines between areas like artificial intelligence and data science are arbitrary and blurry. In any case, **startups need generalists early on**.
- [Ask de-hyping questions on plumbing, decisions, and automation](https://yanirseroussi.com/2024/05/27/plumbing-decisions-and-automation-de-hyping-data-and-ai/):
  - _Plumbing:_ What's the state of your data engineering lifecycles?
  - _Decisions:_ How do you use descriptive, predictive, and causal modelling to support decisions?
  - _Automation:_ How do you use AI to automate processes?
- Work up from principles and business problems rather than by starting with the many tools from [the MAD landscape](https://mattturck.com/landscape/mad2024.pdf). But keep in mind that tools do matter. Paraphrasing a quote from [David Allen](https://gettingthingsdone.com/), _a great wrench doesn't make a great plumber, but a great plumber will always want to use a great wrench_.
- Keep these terms in mind:
  - _Basic AI:_ Black boxes like ChatGPT and transcription tools.
  - _Advanced AI/ML:_ Custom models, harder, [requires MLOps & serious data work beyond the prototype](https://yanirseroussi.com/2024/03/04/two-types-of-startup-data-problems/).
  - _Analytics:_ The M in Build-Measure-Learn, key to product-led growth &ndash; depends on plumbing.
- **Don't expect magic: Advanced AI/ML and Analytics are both hard and depend on solid plumbing.**

## Going deep into one Venn diagram

After creating the initial draft of the slides and making fun of Dataland Venns, I realised that going deep into one Venn diagram would be beneficial. I cover the diagram below in the last part of the video.  

In the diagram, I highlight these three roles:
- _Analyst:_ Focused on understanding and explaining the business (descriptive modelling)
- _Engineer:_ Focused on building scalable systems (i.e., plumbing)
- _Statistician:_ Focused on building mathematical models from data (predictive and causal modelling)

{{< figure src="first-data-hire-venn.png" alt="Venn diagram of data roles and options for first hire (described in the text)" >}}

This diagram evolved from [a post I wrote on the first data hire a few months ago](https://yanirseroussi.com/2024/02/05/substance-over-titles-your-first-data-hire-may-be-a-data-scientist/). I adapted it from [Andrew Bartholomew's post on the same topic](https://www.abartholomew.com/writing/your-first-data-hire). The main change from the original is that it now contains two different recommendations for the first hire:

1. _Data Tech Lead (Analytics Engineer):_ If [the startup isn't AI/ML-centric or highly data-intensive](https://yanirseroussi.com/2024/03/04/two-types-of-startup-data-problems/), the first data hire would likely focus on setting up data pipelines and analytics. Therefore, they should have the skills of an analytics engineer (between an analyst and a data engineer).
2. _AI/ML Lead (AI/ML Engineer):_ If advanced AI/ML is core to the startup's product, the first data hire would focus on building and iterating on the product. Therefore, they should have the skills of an AI/ML engineer and of a data engineer (i.e., build and scale data pipelines and AI/ML in production).

In the middle of the diagram, we have the unicorns who are good at everything. These do exist &ndash; they're just hard to hire and retain. But even the most talented person can't do everything all the time. That's why hiring for one of the above two options is more feasible.

Next up, I'll record the second part of the webinar, which covers the actual hiring. In the meantime, any feedback is welcome.
