---
title: Startup data health starts with healthy event tracking
author: Yanir Seroussi
type: post
date: 2024-06-10T04:00:00+00:00
url: /2024/06/10/startup-data-health-starts-with-healthy-event-tracking/
cover:
  relative: true
  image: kafka-inspired-startup-data-pipelines.webp
  alt: Kafka-inspired startup data pipelines
summary: Expanding on the startup health check question of tracking Kukuyeva's five business aspects as wide events.
tags:
  - analytics
  - business
  - data science
  - data strategy
  - startups
---
The first question in the Data section of [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/) is:

> Do you track Kukuyeva's five business aspects as wide events?

Whole books can be written about this question, so I figured it's worth its own post. Let's dive in.

## Why track and when?

In my past decade of work with startups and scaleups, one thing has remained a constant: **There are always gaps in the data.**

Data gaps may take the form of missing data or low-quality data (from partial to deceptively wrong). The feasibility of any [AI/ML automation or data-informed decisions](https://yanirseroussi.com/2024/05/27/plumbing-decisions-and-automation-de-hyping-data-and-ai/) depends on the nature of the data gaps.

Another important feature of data tracking is: **You can't go back in time to collect or fix most proprietary data.** In other words, historical gaps in the data are there to stay.

Therefore, the answers to the questions from the heading are:

1. **Why track?** To make data-informed decisions, and support automation and optimisation of decision-making via AI/ML. The latter comes after the former, as you need to turn your data into trustworthy business metrics _before_ you use algorithms to optimise for those metrics.
2. **When do you start tracking?** As soon as you have interesting data to track, along with the commitment to ensuring that you're not just tracking garbage. Typically, you should start once you move from a throwaway prototype to a product that has user traction.

## What are wide events?

An event is essentially a timestamped key-value document. _Wide_ events encourage liberal use of attributes to support downstream exploration.

Here's an example from [Ivan Burmistrov's post on the topic](https://isburmistrov.substack.com/p/all-you-need-is-wide-events-not-metrics), of a wide event for ad impressions at Meta:

```
{
    "Timestamp": "1707951423",
    "AdId": "542508c92f6f47c2916691d6e8551279”,
    "UserCountry": "US",
    "Placement": "mobile_feed",
    "CampaignType": "direct_ads",
    "UserOS": "Android",
    "OSVersion": "14",
    "AppVersion": "798de3c28b074df9a24a479ce98302b6",
    ...
}
```

Burmistrov's post is worth reading, as it delves deeper into specific examples of how such events are useful for observability and exploration of _unknown unknowns_: things you weren't aware would be interesting when the code emitting the event was written.

Having been on both the producing and consuming side of such event streams, I have a few thoughts to add:

* [A common objection to Burmistrov's post is the cost of tracking](https://news.ycombinator.com/item?id=39529775). This depends on implementation specifics &ndash; there are ways to balance cost and usefulness of events. Further, if a startup is growing and more events are emitted, revenue and funding should also grow &ndash; which supports higher-volume tracking. Further, tracking costs should be compared to the opportunity cost of data gaps and to the cost of engineering time for cost-optimising the tracking system.
* Many software engineers don't think in terms of events, as data models for production systems typically reflect the _current_ state of the product rather than its entire history. This is unlikely to radically change, as this sort of data model makes sense in production. To bring engineers along for the event ride, it's worth getting them to read [the classic article about The Log by Jay Kreps](https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying).
* As a step towards data quality assurance by event producers, automated tests should ensure that events are emitted as expected. This is different from traditional logging, which is seen as a side effect of the system that doesn't require testing.

## What are Kukuyeva's five business aspects?

I came across [Irina Kukuyeva](https://www.ikukuyeva.com/) last year, when I was looking for other people who are offering Chief Data Officer engagements. Her website is a treasure trove of advice for founders, investors, data consultants, and others.

On the topic of data that should be tracked, [she has this to say](https://www.ikukuyeva.com/blog/Data-to-capture):

> After 10 years of collaborating with companies of all shapes, sizes and industries, I've found that all aspects of your business fall into just 5 attributes that you should (legally and ethically) track across your platform/hardware/service and your customers, timestamped at the individual event level:
>
> 1. "Demographics" of the customer's/IoT device (e.g., Android/iPhone, tablet, desktop, hardware type),
> 2. Your app's/platform's "demographics" (e.g., release 0.9.3, pricing plan(s)),
> 3. State(s) of the app's/platform's assets (e.g., inventory, sensor(s)),
> 4. Interactions of all of the above, and
> 5. Touch-points (e.g. acquisition channels, marketing emails, customer service interactions, sensor maintenance)

One thing I found confusing when I first read the article was the use of the word _attributes_, which commonly refers to specific event attributes. However, now I understand that not all aspects are tracked in each event &ndash; it's a broad overview of what should _ideally_ be tracked across the business.

Importantly, when thinking of tracking at the logical level, **the tools don't matter**. This is exemplified by [another Kukuyeva article that advises founders to get started on their data strategy](https://www.ikukuyeva.com/blog/founders/getting-started-data-strategy) with tools that can be as simple as pen and paper.

For examples of how events fold up to analytics and other use cases, see [Eventify Everything by Timo Dechau](https://substack.timodechau.com/p/eventify-everything-data-modeling) and [Activity Schema](https://www.activityschema.com/). However, keep in mind [this observation by Misha Panko of Motif Analytics](https://news.ycombinator.com/item?id=39529775):

> It took the world decades to develop widely accepted standards for working with relational data and SQL. I believe we are at the early stages of doing the same with event data and sequence analytics. It is starting to simultaneously emerge in many different fields:
>
> - eng observability (traces at Datadog, Sumologic, etc)
> - operational research (process mining at Celonis)
> - product analytics (funnels at Amplitude, Mixpanel)
>
> As with every new field, there are a lot of different and overlapping terms being suggested and explored at the same time.

In short, even though systems for event stream processing like [Apache Kafka](https://en.wikipedia.org/wiki/Apache_Kafka) are now over a decade old, the industry is still figuring out how to best model and use all the event data. No one has all the answers, and your mileage will vary.

## What's a healthy level of tracking?

Assuming compliance with relevant data privacy regulations, there's still a question of what tracking level is healthy. Despite the yes/no phrasing of my original question (_"do you track Kukuyeva's five business aspects as wide events?"_), responses are likely to fall on a continuum between 0 and 1:

0. **Obviously unhealthy:** No, we don't track any events.
1. **Unrealistically healthy:** Yes, we track everything and have high confidence that we know everything we need to know.

Health is relative to the stage of the startup and its current goals. If data gaps are blocking growth or likely to start hurting growth in the 6-12 month horizon, then tracking is insufficiently healthy and should be addressed.

## Data-to-AI health beyond event tracking

This post is part of a series on [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/). Previous posts:

* [Assessing a startup's data-to-AI health: Overview and motivation](https://yanirseroussi.com/2024/04/22/assessing-a-startups-data-to-ai-health/)
* [Business questions to ask before taking a startup data role](https://yanirseroussi.com/2024/05/06/business-questions-to-ask-before-taking-a-startup-data-role/)
* [Probing the People aspects of an early-stage startup](https://yanirseroussi.com/2024/05/13/probing-the-people-aspects-of-an-early-stage-startup/)
* [Question startup culture before accepting a data-to-AI role](https://yanirseroussi.com/2024/05/20/question-startup-culture-before-accepting-a-data-to-ai-role/)
* [Plumbing, Decisions, and Automation: De-hyping Data & AI](https://yanirseroussi.com/2024/05/27/plumbing-decisions-and-automation-de-hyping-data-and-ai/)
* [How to avoid startups with poor development processes](https://yanirseroussi.com/2024/06/03/how-to-avoid-startups-with-poor-development-processes/)

[You can download a guide containing all the questions as a PDF](https://yanirseroussi.com/data-to-ai-health-check/). Next, I'll go into the other questions in the Data section. Feedback is always welcome!
