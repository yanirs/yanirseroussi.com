---
title: Giving up on the minimum viable data stack
author: Yanir Seroussi
type: post
date: 2024-08-19T03:30:00+00:00
url: /2024/08/19/giving-up-on-the-minimum-viable-data-stack/
cover:
  relative: true
  image: mad-landscape-2024.webp
  caption: MAD landscape 2024. 2000+ logos and expanding. [Source](https://mattturck.com/mad2024/).
summary: Exploring why universal advice on startup data stacks is challenging, and the importance of context-specific decisions in data infrastructure.
tags:
  - data engineering
  - data strategy
  - startups
---
Back in February, I [had an idea for a series of posts on a startup's minimum viable data stack](https://yanirseroussi.com/2024/02/19/building-your-startups-minimum-viable-data-stack/). The motivation was to provide advice that'd help startups navigate [the ever-expanding MAD (Machine Learning, AI, and Data) landscape, which as of 2024 includes over 2,000 logos](https://mattturck.com/mad2024/). I was also aiming to deepen my knowledge through research and writing for the series.

Since then, I've decided to drop the idea because:

1. **Specific constraints are key.** A startup's decisions on hiring, infrastructure, and requirements constrain what's minimally viable in their case.
2. **MAD is a moving target.** The MAD landscape is a moving target even when restricted to "minimum viable" data stack components.
3. **Deep research requires real-world experimentation.** I was planning to use every tool as part of my research, but this is both time-consuming and shallow. I simply don't have the capacity to use every tool to the level it'd be used by a full-time team (no single person does).

I'll illustrate these issues through a question I advised on recently:

> Should a startup use Snowflake, Databricks, or a collection of AWS products at the core of their Data & AI stack?

## (1) Specific constraints are key

The question is constrained to three top-level options. This was informed by the company's choice of AWS as their cloud platform. While Snowflake and Databricks can run with either of the three major cloud providers, throwing Google Cloud or Azure into the mix would be foolish.

Indeed, when the time comes to get serious about Data & AI, it's often the case that many infrastructure decisions have already been made. These decisions introduce constraints &ndash; which is a _Good Thing_. Such constraints narrow down the search through the MAD landscape.

The question also implies that the company would benefit from a cloud lakehouse solution. This isn't always the case, especially in a _minimum viable_ setting! Sometimes, spreadsheets are good enough. In other cases, [the increasingly-popular DuckDB](https://duckdb.org/) can serve analytical needs. Determining what's minimally viable requires understanding the specific context.

Finally, the context also includes current staff capabilities and plans for hiring. Continuing with our example, setting up Databricks or cobbling together AWS products requires more data engineering expertise than getting started with Snowflake (at least in 2024). The preferred choice has to be informed by team expertise, which limits the usefulness of general advice posts.

## (2) MAD is a moving target

[One Redditor distilled the question of Snowflake versus Databricks in February 2023](https://www.reddit.com/r/dataengineering/comments/114vyvz/comment/j91zuka/) to a choice between: _"(1) a product made to be a cloud RDBMS-style SQL engine focused on ELT and data collaboration, which is now adding data engineering workloads as a bolt-on; or (2) a product made to be a datalake-based Spark engine for distributed computations and engineering/data science workloads, which is adding a SQL database as a bolt-on."_

The collection of AWS offerings is also ever-evolving, but anyone who's used AWS products deeply knows that they're not all equal in quality. For example, I was wondering whether AWS Redshift has caught up with Snowflake and Databricks, given that it now includes a serverless option. However, Redshift still isn't getting much love &ndash; both from personal discussions with experts and from [Reddit comments like](https://www.reddit.com/r/dataengineering/comments/12mw1yy/comment/jgeh9m7/): _"We use Redshift extensively, and I would take my chances and pick an unknown solution over Redshift at this point"_.

Check again next year and things might change. General recommendations based on current capabilities will get old pretty quickly.

## (3) Deep research requires real-world experimentation

Vendors tend to paint a rosy picture of the everyday reality of setting up, managing, and using the products they're selling. For complex tools, going through a basic setup on a sample project isn't enough to gain the deep understanding that comes from real-world deployments. For an illustration of the practical knowledge gained by making many such decisions, check out the post [_(almost) every infrastructure decision I endorse or regret after 4 years running infrastructure at a startup_](https://cep.dev/posts/every-infrastructure-decision-i-endorse-or-regret-after-4-years-running-infrastructure-at-a-startup/).

Further, when it comes to Data & AI platforms, there are multiple users with different views. For example, how an analyst interacts with the platform is different from how a data engineer interacts with it. My original thought of trying to cover all bases in a post series was just too ambitious.

As a shortcut to gaining deep experience with _all_ the tools (an impossible endeavour), I opt for a combination of desk research and consulting experts. Returning to the running example, this sort of research means that I can now speak more confidently about the trade-offs between choosing Snowflake, Databricks, and AWS tools in 2024. The short answer to the question of _which Data & AI platform_ is a big _IT DEPENDS_ (and it will keep changing).

## Beyond the tools: People, Platform, and Processes

Tools cover only one aspect of making technology decisions &ndash; the Platform. People and Processes are no less important. Keeping the Platform constant, some companies will succeed, and some will fail.

In general, the best tools are those that your People already know, or are committed to using well. Given the richness of the MAD landscape and software tooling in general, [making reversible decisions](https://yanirseroussi.com/til/2024/04/05/the-data-engineering-lifecycle-is-not-going-anywhere/) and [choosing boring, well-supported components](https://boringtechnology.club/) where possible is the way to go.

While I've abandoned the idea of _posting_ about each component in the minimum viable data stack, I still advocate for the core concepts: Work back from business needs, set up the minimal Platform that makes sense in your case, and ensure that your People and Processes are making the most out of the chosen Platform. Then keep iterating.

Good luck out there!
