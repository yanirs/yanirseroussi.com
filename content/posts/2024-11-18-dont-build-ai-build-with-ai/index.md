---
title: Don't build AI, build with AI
author: Yanir Seroussi
type: post
date: 2024-11-18T01:00:00+00:00
url: /2024/11/18/dont-build-ai-build-with-ai/
cover:
  relative: true
  image: cover.webp
  alt: A robotic intern points towards a glowing AI God surrounded by cogs
summary: Building AI is hard and expensive. For most companies, the path to AI success is building with third-party AI interns and cheap AI cogs.
tags:
  - artificial intelligence
  - business
  - data science
  - startups
---
Drew Breunig divides AI uses cases into [Gods, Interns, and Cogs](https://www.dbreunig.com/2024/10/18/the-3-ai-use-cases-gods-interns-and-cogs.html):

> 1. **Gods:** Super-intelligent, artificial entities that do things autonomously.
> 2. **Interns:** Supervised copilots that collaborate with experts, focusing on grunt work.
> 3. **Cogs:** Functions optimized to perform a single task extremely well, usually as part of a pipeline or interface.

Each category comes with different costs:
- **Gods may cost billions or trillions of dollars to develop.** The feasibility of building them is unclear, as they don't exist yet.
- **Interns are free or cheap to use.** The cost of building them can range from negligible (e.g., creating [a custom GPT via prompting](https://openai.com/index/introducing-gpts/)) to the millions of dollars (e.g., [Bloomberg spent millions building a specialised model on its finance data](https://www.forbes.com/sites/jamielsheikh/2023/04/05/the-chatgpt-of-finance-is-here-bloomberg-is-combining-ai-and-fintech/)).
- **Cogs are free or cheap to build and run,** and they are reliable enough to run independently.

This categorisation is useful when considering startup and product ideas, and your use of AI:
1. **Don't build AI Gods**, unless you have access to ungodly amounts of capital. This may be obvious to most people, but I still see pitches for model-centric startups, and [God-building model companies are the focus of much AI hype](https://research.contrary.com/deep-dive/long-tail-of-ai).  
2. **Build with AI Interns**, as they can significantly increase your productivity. Interns include writing assistants, meeting transcribers, and programming copilots. Ignoring the wealth of AI interns is foolish for individuals and companies alike.
3. **Don't build complex AI Interns**, unless you have a use case that justifies the costs and risks. For example, [Bloomberg's multi-million dollar model was outperformed by GPT-4 a few months after its release](https://www.linkedin.com/posts/emollick_remember-bloomberggpt-which-was-a-specially-activity-7150359287024795648-65rD/), and [it's unclear whether it ended up powering any features](https://research.contrary.com/deep-dive/long-tail-of-ai).
4. **Build with and build AI Cogs**, but ensure you can [manage non-deterministic components in production](https://yanirseroussi.com/2024/07/29/ai-ml-lifecycle-models-versus-real-world-mess/). This includes anything from traditional machine learning to the plethora of AI tasks that have become commodified in recent years like [object recognition](https://yanirseroussi.com/2024/02/26/avoiding-ai-complexity-first-write-no-code/) and text summarisation.  

Above all, **start by defining the problem and assessing the impact rather than making AI use your goal.** Focusing on problems and [solution impact](https://longform.asmartbear.com/problem/) is robust to hype cycles. I've considered this focus to be [the hardest problem in data science since at least 2015](https://yanirseroussi.com/2015/11/23/the-hardest-parts-of-data-science/). Amazon data scientist Dzidas Martinaitis has recently captured a similar sentiment in his [flowchart for data science projects](https://www.dzidas.com/ml/2024/10/22/implementing-data-science-projects/). Similarly, Douglas Gray and Evan Shellshear have found that [data science and AI projects typically fail due to issues with strategy and process, rather than tech and people shortfalls](https://www.routledge.com/Why-Data-Science-Projects-Fail-The-Harsh-Realities-of-Implementing-AI-and-Analytics-without-the-Hype/Gray-Shellshear/p/book/9781032660301).

Ignore at your own risk.

---
<small><i>Acknowledgement:</i> This post was produced with the help of AI interns. One version of Gemini produced the cover image, while another made helpful suggestions on earlier drafts.</small>
