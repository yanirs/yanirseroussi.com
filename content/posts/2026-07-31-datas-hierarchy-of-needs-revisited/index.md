---
title: Data's hierarchy of needs revisited
author: Yanir Seroussi
type: post
date: 2026-07-31T03:00:00+00:00
url: /2026/07/31/datas-hierarchy-of-needs-revisited/
cover:
  relative: true
  image: datas-hierarchy-of-needs-revisited-cover.webp
summary: Updating data's hierarchy of needs with org foundations and automated decisions. Neglect the base, and the top still fails.
tags:
  - business
  - data business
  - data science
  - data strategy
  - machine learning
  - software engineering
---
Back in 2014, I [published a post on data's hierarchy of needs](https://yanirseroussi.com/2014/08/17/datas-hierarchy-of-needs/). Heavily inspired by a snippet from a post by Jay Kreps, my focus was on the technical aspects of succeeding with data & AI. The main message was: **Too many people jump into fancy top-layer applications while neglecting the foundations. This is a recipe for failure.**

Fast forward 12 years, and the same message remains grounded in reality. Human nature doesn't change that fast, so the old post is still relevant.

That said, the original hierarchy focused on technical aspects, and had predictive modelling at the apex. Because tech work can fall apart due to organisational issues, I decided to update it with the org foundations. I also added _the automation of decisions_ to the top to capture our brave new world of AI systems that have increased autonomy and agency. Having _decisions_ at the apex also hints at [the decision-support purpose of all good analytics work](https://yanirseroussi.com/2018/07/22/defining-data-science-in-2018/).

Claude kindly prettified the visual, giving me this lovely figure:

{{< figure src="datas-hierarchy-of-needs-revisited.svg" >}}

Working from the bottom up, we have:
* `org culture, key people & strategy`: The foundation everything relies on. No amount of technical work can fix a dysfunctional org that's going in the wrong direction.
* `org systems, processes & structure`: How the org actually works. As the popular rephrasing of [Conway's Law](https://en.wikipedia.org/wiki/Conway%27s_law) goes: "you ship your org chart".
* `software systems, processes & architecture`: Mentioned in the 2014 post as everything upstream of the "pure" data systems. Partly maps to the _generation_ stage of [Reis & Housley's 2022 data engineering lifecycle](https://yanirseroussi.com/til/2024/04/05/the-data-engineering-lifecycle-is-not-going-anywhere/), but also affects the standard of work of all tech teams.
* `measure, structure & store`: The foundation of the 2014 hierarchy, which overlaps with generation, storage, and ingestion in the data engineering lifecycle.
* `transform & serve`: Updated label from the original `process & query` to align with the last two stages of the data engineering lifecycle.
* `report & present`: Analytics, parts of data science, dashboarding, and more. Even with AIs automating many of the technical aspects of this layer, human understanding is crucial for making good decisions.
* `predict & infer`: Models that vary in their sophistication from linear regression to deep neural nets. This is where [the AI/ML lifecycle](https://yanirseroussi.com/2024/07/29/ai-ml-lifecycle-models-versus-real-world-mess/) shows up, in all its glorious complexity.
* `automate decisions`: The ideal (and dangerous) application. Highly valuable, but needs to be handled with care – especially around when to automate, and when to keep humans in the loop.

While the hierarchy is richer, the message remains the same: **If you neglect the bottom layers, you can't expect magic at the top.** I suspect this will still hold in 2038.
