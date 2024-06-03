---
title: How to avoid startups with poor development processes
author: Yanir Seroussi
type: post
date: 2024-06-03T02:45:00+00:00
url: /2024/06/03/how-to-avoid-startups-with-poor-development-processes/
cover:
  relative: true
  image: release-early-release-often.webp
  alt: 'minimalist image of the phrase RERO: release early, release often'
  caption: Avoid those who release late, release seldom, and don't listen to their customers.
summary: Questions that prospective data specialists and engineers should ask about development processes before accepting a startup role.
tags:
  - business
  - career
  - data strategy
  - software engineering
  - startups
---
Many founders have never worked at a startup. This may make them oblivious to failure modes that arise from poor development processes. With poor processes, even the most brilliant people are ineffective, as they're constantly wasting time and fighting fires.

You don't want to join a startup that's mired in intractable chaos. To avoid such a place, ask questions from the Processes & Project Management section of [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/). Do this even if you're a data scientist or a junior engineer &ndash; because everyone suffers in an environment with poor processes.

This post briefly explains each question, along with expected answers and suggestions for eliciting informative responses.

## The questions

**Q1: How often are changes shipped to production?** Even in 2024, there are software startups that don't follow the [RERO philosophy](https://en.wikipedia.org/wiki/Release_early,_release_often): _"Release early. Release often. And listen to your customers."_ Sporadic releases are often indicative of poor processes. Stay away from such startups, unless you have a mandate to improve things.

**Q2: How is the impact of new features quantified before and after their release?** Another classic quote in the spirit of RERO is [the first principle behind the Agile Manifesto](https://agilemanifesto.org/principles.html): _"Our highest priority is to satisfy the customer through early and continuous delivery of valuable software."_ And you can't know what's _valuable software_ if you don't collect data from your users and meaningfully aggregate it. Helping with this is likely to be your responsibility if you're [the first data hire](https://yanirseroussi.com/2024/02/05/substance-over-titles-your-first-data-hire-may-be-a-data-scientist/) &ndash; ensure that the founders understand that.

**Q3: What processes and systems are in place to collect qualitative and quantitative feedback from users (both internal and external)?** This takes a more holistic view of user feedback and includes internal users. A common failure mode for internal-facing data teams is to spend too much time satisfying low-value requests, e.g., build a dashboard that is barely used. Given the opportunity cost, it's important to collect truthful feedback from _all_ users.

**Q4: Were there any outages in recent months? How did they affect users? What changes did you implement to reduce the chance of outages and impact on users?** Some outages are unavoidable, especially early on. If the answers reveal that there are repeated issues that go unaddressed, the team may be too busy fighting fires rather than shipping valuable software. This applies to internal systems as well, e.g., data ingestion pipelines that keep breaking shouldn't be seen as normal.

**Q5: What system do you use for prioritising and tracking work across the company?** This includes project management tools, and their use in practice &ndash; but any tool can be misused. The important things to look for are that: (1) a system exists; and (2) the system will improve over time.

**Q6: How do you balance paying down tech debt and shipping new features?** [Tech debt is unavoidable](https://blog.codinghorror.com/paying-down-your-technical-debt/), especially in a fast-growing startup. You're looking for an acknowledgement of this fact, along with an understanding that accruing too much tech debt reduces the ability to ship new features. While the concept comes from software engineering, it also applies to product analytics: if the data is a tangled mess and pipelines are unreliable (i.e., _data_ tech debt is high), then analytics can't be trusted to help improve the product.

**Q7: What proportion of the engineering and data staff time is spent on: (1) dealing with bugs and incidents; (2) meetings and admin overheads; and (3) shipping new features?** This question takes Q5 & Q6 from philosophy to practice &ndash; [_"don't tell me your priorities; show me your calendar"_](https://www.instagram.com/p/CrdiX-4OBlv/). If individual contributors don't spend most of their time shipping new features (including research into the necessity of these features), there may be too much tech debt or too many overheads.

**Q8: What are the key team rituals (e.g., recurring meetings, sprint planning, demos, postmortems, standups)?** Again, the calendar is a source of insights. For early-stage startups, awareness of the need for rituals may be low, and they may be implemented poorly. For example, I believe that daily synchronous standups are a bad idea for remote teams. A better approach is using a bot that asks everyone for their progress, upcoming tasks, and blockers &ndash; _and following up to ensure that everyone is on track as a team_.

**Q9: What processes are in place for code, design, and architecture reviews?** The depth and time of each process should be proportional to the magnitude and impact of the change. For example, a trivial code improvement in a product that barely has any users can be shipped with a post-commit review. In contrast, migrating a live product to a different database system requires deeper consultation.

**Q10: Are there different processes for internal-facing data products (e.g., custom admin dashboards)?** The unfortunate reality of many organisations is that data analytics and software engineering live in different silos. This can easily happen at small startups as well, with a single analyst working in isolation from product teams. I believe that the ideal situation is that internal-facing data products are treated like the software products that they are. They may not need to be as pretty as external-facing products, but their development should follow processes that ensure high quality, trustworthiness, and satisfaction of user needs.

**Q11: Give an example of how the above items manifest in a big project that was recently completed.** It's often hard to speak of abstract processes. An example of a big project may be the best way of moving from the abstract to the everyday reality of the startup.

**Q12: Are there any gaps in the current processes or changes you'd like to introduce?** This probes for a growth mindset. If the answer is _no_, there's probably something wrong.

## What if you can't fit in all the questions?

If you're simply trying to avoid a dysfunctional startup rather than dive deep into development processes, a subset of the questions will suffice:

* Q1 + Q2: Ensure that products are continuously improving based on user feedback.
* Q7: Ensure that time spent by current staff aligns with how you want to spend your time.
* Q11 + Q12: Ensure that leaders are conscious of the need to implement and improve processes.

## Data-to-AI health beyond processes

This post is part of a series on [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/). Previous posts:

* [Assessing a startup's data-to-AI health: Overview and motivation](https://yanirseroussi.com/2024/04/22/assessing-a-startups-data-to-ai-health/)
* [Business questions to ask before taking a startup data role](https://yanirseroussi.com/2024/05/06/business-questions-to-ask-before-taking-a-startup-data-role/)
* [Probing the People aspects of an early-stage startup](https://yanirseroussi.com/2024/05/13/probing-the-people-aspects-of-an-early-stage-startup/)
* [Question startup culture before accepting a data-to-AI role](https://yanirseroussi.com/2024/05/20/question-startup-culture-before-accepting-a-data-to-ai-role/)
* [Plumbing, Decisions, and Automation: De-hyping Data & AI](https://yanirseroussi.com/2024/05/27/plumbing-decisions-and-automation-de-hyping-data-and-ai/)

[You can download a guide containing all the questions as a PDF](https://yanirseroussi.com/data-to-ai-health-check/). The next area of the health check is Data (_finally!_). Feedback is always welcome!
