---
title: Assessing a startup's data-to-AI health
author: Yanir Seroussi
type: post
date: 2024-04-22T06:00:00+00:00
url: /2024/04/22/assessing-a-startups-data-to-ai-health/
cover:
  relative: true
  image: cover.webp
  alt: a person dressed as a doctor conducting a health check on a screen
summary: Reviewing the areas that should be assessed to determine a startup's opportunities and challenges on the data/AI/ML front. 
tags:
  - analytics
  - artificial intelligence
  - business
  - data science
  - data strategy
  - machine learning
  - software engineering
  - startups
---
In the past year, I went from exploring product ideas to committing to my current consulting practice. One thing that became apparent was that I needed to get better at communicating my unique value proposition: who I serve, and how I can help them. The circus that is data (/AI/ML/BI/analytics/...) titles and terminology definitely doesn't help. Sprinkle a couple of decades of hype cycles on top, and you end up where we are today: a mess of inflated expectations followed by disappointments. But also a wealth of opportunities to generate genuine value.

Anyway, I'm now fairly clear on whom I'm actively targeting: funded Australian startups (around seed to series A) in the climate & nature tech space, who can use help on their data-to-AI journey. I started calling it data-to-AI rather than data & AI or data/AI/ML because anything AI (/ML/data science/...) or analytics starts with data &ndash; and keeps going back to data.

How I can help isn't as clearly communicated as I'd like it to be, so I've been working on that. Offerings at the cheap and expensive ends of the spectrum are easy to explain: one-off advisory calls include bespoke on-the-spot advice, while fractional chief data & AI officer engagements include similar responsibilities to those of a full-timer with the same title. However, it's in nobody's best interest to jump straight into a fractional relationship. To address this, I've been working on a standard offering that'd be more structured than advisory calls, deliver value to the client, and allow both parties to uncover opportunities and see how we work together.

My working title for the offering is _Data-to-AI Health Check_ (better suggestions welcome). The idea is to assess where the startup stands with their data/AI/ML stack and capabilities, and identify the top opportunities for improvement.

This has been on my mind for a while, so I've collected a heap of documents and questions for inspiration. I'm now at the "too overwhelmed" phase of turning it into something I can present, but hopefully I'll have it all sorted in the coming weeks.

In the meantime (and in the spirit of building in public), the rest of this post describes the areas I think are most important to assess. Suggestions for areas I might have missed are welcome. In future posts, I'll add more detail on performing the assessment, which will undoubtedly evolve as I offer it to more clients.

## Assessment areas

**Product and business model.** Understanding what the startup is about and where it's going is key to understanding where data/AI/ML fit in. One useful lens is determining whether the product is [ML-centric or non-ML](https://yanirseroussi.com/2024/03/04/two-types-of-startup-data-problems/), with non-ML products varying in their data intensity from data-centric to data-supported. It's also important to understand key metrics and how they're measured.

**People.** Who's working for the company and what is the team structure? In particular, what are the current data/AI/ML capabilities and experience? Can the current staff deliver what the business needs? If there are skill gaps (e.g., they haven't yet made [their first data hire](https://yanirseroussi.com/2024/02/05/substance-over-titles-your-first-data-hire-may-be-a-data-scientist/)), what's the plan to address them? Can the current team adequately assess the skills of data people?

**Processes and project management.** The best people will fail to deliver projects if the company's processes have deep flaws. My general opinion is that all the best practices from software development can and should be applied to data projects (e.g., see posts from [2023](https://yanirseroussi.com/2023/06/30/was-data-science-a-failure-mode-of-software-engineering/) and [2018](https://data.blog/2018/03/20/engineering-data-science-at-automattic/)). However, data entropy and the probabilistic nature of AI/ML require extra care and practices _in addition to_ traditional software development.

**Culture.** Knowing what people are on the team and what processes are in place isn't enough to assess how well the team can deliver the product vision. Culture &ndash; the unwritten norms and beliefs of the company &ndash; matters. A lot. For example, if the founder doesn't tolerate data-backed evidence that contradicts their preconceived notions, it's likely to be an impediment to data/AI/ML project delivery. Similarly, it's worth paying attention to how experiments are treated: If a hypothesis behind an experiment turns out to be unsupported, it's not a failure. Failing to learn from experiments is the true failure.

**Data.** What data is the company dealing with? What are the data's volume, velocity, and variety? Is all the necessary data being captured? How clean is it? Where is it stored and how is it processed? What [data management](https://en.wikipedia.org/wiki/Data_management) practices are in place, both explicitly and implicitly?

**Tech.** Closely related to data is the tech architecture, systems, and software. Tech includes where the data lives and how it flows, particularly how it feeds into AI/ML/analytics applications. Of particular interest is [the allocation of innovation tokens](https://boringtechnology.club/). Innovation tokens should be spent on tech that makes the startup meaningfully unique to its customers. Everything else should be boring and standard, i.e., proven to work and fit for purpose.

**Security and compliance.** Security is interwoven through all of the above. For example, you want a culture where any person can flag security risks &ndash; some of which may only be visible if you're close to the code and data. Security breaches and data leaks can destroy companies, especially young startups that haven't earned customer trust yet. Particular attention should be paid to compliance issues that arise with data collection, e.g., around personal and regulated data.

**Other opportunities and risks.** In exploring the above areas, issues that don't fit neatly into any bucket are likely to be uncovered. These may be new opportunities or risks. It's important to keep an eye out for such cases and flag them accordingly.

## Closing thoughts

In my experience, it's easy to find a thousand areas for improvement once you become familiar with a startup or a large company division. It's harder to identify the top three items to work on next &ndash; it is a bet on the highest-impact items that are feasible to deliver.

It is also a challenge to distill the Data-to-AI Health Check to a set of questions that would probe the right areas without burdening the startup too much. I'll report back once I've figured it out. In the meantime, comments are welcome!
