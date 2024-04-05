---
title: The data engineering lifecycle is not going anywhere
author: Yanir Seroussi
type: til
date: 2024-04-05T01:00:00+00:00
url: /til/2024/04/05/the-data-engineering-lifecycle-is-not-going-anywhere/
summary: My key takeaways from reading Fundamentals of Data Engineering by Joe Reis and Matt Housley.
showBreadcrumbs: true
tags:
  - books
  - career
  - data engineering
  - quotes
---
After over a decade of engaging in [reluctant data engineering](https://yanirseroussi.com/2023/10/25/lessons-from-reluctant-data-engineering/), I've come to terms with it being a part of my life for as long as I'm going to be working in Data & AI. As the rise of data engineering happened concurrently with my career in data, I picked up some data engineering skills to solve specific problems. That is, I learned from experience rather than from a formal education program. Recently, I read the book [Fundamentals of Data Engineering](https://www.oreilly.com/library/view/fundamentals-of-data/9781098108298/) by Joe Reis and Matt Housley, which has helped consolidate my understanding of the field &ndash; including key principles and trends.

Fundamentals of Data Engineering is an essential read for anyone working in data. As it aims to remain relevant for years to come, it doesn't get into the details of specific tools, which are bound to keep changing. Instead, the book describes the data engineering lifecycle, provides guidelines for data architecture and technology choice, and then goes into details on each of the lifecycle stages.

I will not attempt to summarise the book here, as it is itself a summary of a vast field. However, a couple of key items worth pulling out are the data engineering lifecycle and the principles of good data architecture (which apply to other software systems as well). In a world awash with vendor marketing and AI hype, it's important to keep these abstractions in mind. In particular, the data engineering lifecycle is unlikely to go anywhere, even if more of the work will be done by AIs (aka [automated agents](https://yanirseroussi.com/til/2023/10/06/artificial-intelligence-was-a-marketing-term-all-along-just-call-it-automation/)).

> **Five stages of the data engineering lifecycle:**
> 1. Generation (typically outside the control of data engineers)
> 2. Storage (underlies stages 3-5 &ndash; typically managed by data engineers)
> 3. Ingestion (typically getting data from external production systems to a central warehouse/lake/lakehouse)
> 4. Transformation (turning raw ingested data into more useful datasets)
> 5. Serving (for analytics, machine learning, and reverse ETL &ndash; the latter means sending data back to production systems)
>
> **Undercurrents of the data engineering lifecycle (which manifest in every stage):**
> * Security
> * Data management
> * DataOps
> * Data architecture
> * Orchestration
> * Software engineering
> 
> **Principles of good data architecture:**
> 1. Choose common components wisely
> 2. Plan for failure
> 3. Architect for scalability
> 4. Architecture is leadership
> 5. Always be architecting
> 6. Build loosely coupled systems
> 7. Make reversible decisions
> 8. Prioritize security
> 9. Embrace FinOps
