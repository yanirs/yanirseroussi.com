---
title: Artificial intelligence, automation, and the art of counting fish
author: Yanir Seroussi
type: post
date: 2024-04-01T06:00:00+00:00
url: /2024/04/01/artificial-intelligence-automation-and-the-art-of-counting-fish/
cover:
  relative: true
  image: lord-howe-island-view-from-intermediate-hill.webp
  caption: View from Lord Howe Island's Intermediate Hill (showcasing many RLS sites)
summary: Discussing the use of AI to automate underwater marine surveys as an example of the uneven distribution of technological advancement.
tags:
  - artificial intelligence
  - machine learning
  - marine science
  - Reef Life Survey
---
I recently returned from a [Reef Life Survey (RLS)](https://reeflifesurvey.com/) trip to [Lord Howe Island](https://lordhoweisland.info/). As a volunteer RLS diver, I record fish and invertebrates using [methods](https://reeflifesurvey.com/methods/) that have remained unchanged for decades. Sites around Lord Howe Island have been consistently surveyed at least every two years since February 2006. This regularity and consistency in survey methods enables comparisons over time, which help inform marine park management decisions.

As a Data & AI specialist, [I've wondered about the potential for automating RLS surveys since I first became a volunteer nearly ten years ago](https://yanirseroussi.com/2016/01/24/the-joys-of-offline-data-collection/). Surely the data can be collected without using an underwater clipboard? Given advances in AI over the past decade, I believe that the answer is an emphatic _yes_ &ndash; in principle.

However, just because something can be automated doesn't mean it happens instantaneously. As the saying goes, [the future is here, but it is unevenly distributed](https://quoteinvestigator.com/2012/01/24/future-has-arrived/). In fact, Lord Howe Island provides another example of this uneven distribution: As of 2024, the island still lacks mobile phone reception, despite [the feasibility of providing coverage](https://www.lhib.nsw.gov.au/sites/default/files/2023-09/Lord%20Howe%20Island%20Communications%20Options%20Paper_Respiro_250823_FINAL.pdf).

Specifically for RLS automation, even though computers can in principle identify, count, and size fish better than humans, there are several key challenges on the path to automation:

* **Consistency:** Much of the value of RLS data comes from employing the same methods over decades. Using new survey methods would mean introducing different biases, which would need to be modelled when comparing new data to pre-automation data.
* **Underwater logistics and costs:** Replacing volunteer divers with robots isn't simple, as the RLS methodology goes beyond swimming along a transect line and counting fish. Divers also need to look under ledges and in crevices, move kelp, and inspect the undersides of shells. This is probably within the abilities of underwater robots, but it'd be hard for such robots to compete with volunteer divers on cost.
* **Boating logistics and costs:** Anyone who's been to sea knows that boating isn't straightforward. Conditions vary, and things break all the time. Getting humans out of the loop can make things more expensive, especially when there are many volunteers like me, who happily pay to go to sea and dive with or without RLS. Unlike humans, robots don't dive for fun.

Given the challenges, partial automation may be the way to go initially: Mount cameras on volunteers, collect many survey videos, and process them as a quality control. With enough work, the output of the processing should be similar to the survey output of the volunteers &ndash; or at a minimum, the biases will be better understood. This approach would enable modelling of biases in subsequent analyses, addressing the issue of consistency. At that point, it'd be possible to do away with the need for volunteers to record the data manually &ndash; they can just record videos of the dives. This would be an example of [combining AI with citizen science to supercharge ecological monitoring](https://www.sciencedirect.com/science/article/pii/S2666389920301434).

If we accept partial automation as a desirable option, the key question becomes one of budget allocation. Collecting enough survey videos and doing the data and machine learning work isn't a trivial exercise, i.e., it won't be cheap. That said, I believe that with current technology the cost isn't prohibitive either &ndash; it can probably be done as a PhD project with the right student and guidance. Still, whether the budget is best spent on partial automation or on other initiatives is an open question (that is not for me to decide).

In general, similar questions around budget allocation arise everywhere. While many of us in tech feel somewhat overwhelmed by the rate of progress in Data & AI, it is important to remember the uneven distribution of automation ([treating AI as a synonym of automation makes it sound less magical](https://yanirseroussi.com/til/2023/10/06/artificial-intelligence-was-a-marketing-term-all-along-just-call-it-automation/)). This uneven distribution means that opportunities abound for deploying proven technologies in various domains. These opportunities are unlikely to disappear overnight &ndash; they will be here for years to come. Focusing on solutions to real problems while maintaining an awareness of emerging tech ([without chasing shiny objects](https://yanirseroussi.com/2023/10/25/lessons-from-reluctant-data-engineering/)) will remain the key to success. In particular, Data & AI engineering are likely to remain lucrative in coming years, though they will undoubtedly change with [new tools](https://yanirseroussi.com/2020/01/11/software-commodities-are-eating-interesting-data-science-work/) and novel automation methods.

{{< figure src="lord-howe-island-algal-hole-trevally.webp" caption="Automation or no automation, hanging out with the fish is always fun" >}}
