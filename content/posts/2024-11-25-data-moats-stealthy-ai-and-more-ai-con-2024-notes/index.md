---
title: "Data moats, stealthy AI, and more: AI Con 2024 notes"
author: Yanir Seroussi
type: post
date: 2024-11-25T02:30:00+00:00
url: /2024/11/25/data-moats-stealthy-ai-and-more-ai-con-2024-notes/
cover:
  relative: true
  image: ai-con-2024-speaker-cover.webp
  alt: image showcasing some of the speakers from AI Con 2024
summary: "Themes from AI Con 2024: data moats, stealthy AI use, Chatty's UX revolution, and enduring fundamentals"
tags:
  - artificial intelligence
  - business
  - data science
  - data strategy
  - startups
---
Earlier this month, I was delighted to participate in a panel discussion as part of [Sydney's AI Con 2024](https://www.aicon.org.au/event/9205e371-f13a-4688-9d36-20f5722230fd/summary).
I felt like a bit of an impostor as I found myself on the cover banner alongside truly accomplished speakers like [Cassie Kozyrkov](https://www.linkedin.com/in/kozyrkov/) and [Mike Bewley](https://www.linkedin.com/in/michaelbewley/), but it all went smoothly.

This post summarises five themes from the conference:
- Data is the moat (but _data scientist_ is a somewhat toxic term)
- Stealthy AI use may be the wisest approach
- Chatty is a UX revolution – model building is dead
- Testing is key
- Business and product fundamentals remain unchanged

The talks weren't recorded, so I'm basing this post on rereading my notes a few weeks later.
Also, some of my takeaways draw on conversations from the best part of any conference: The Hallway Track.
Therefore, I apologise if I misquoted any speaker, and I'd be happy to update the post if needed.

## Data is the moat (but _data scientist_ is a somewhat toxic term)

As I've been banging on about [how data is still key to success in the GenAI world](https://yanirseroussi.com/2024/06/17/ai-aint-gonna-save-you-from-bad-data/), it was great to feed my confirmation bias.
For example, Mike Bewley noted that much of [Nearmap](https://www.nearmap.com/au)'s competitive advantage comes from the proprietary dataset they collected.
Their dataset is harder to replicate than the AI layer (which is also world-class).

This view of proprietary data as a moat was echoed by other speakers and discussions.
However, despite what we might have thought about a decade ago, data scientists are no longer the superstars they used to be.
In fact, _data scientist_ is a somewhat toxic term.
It's now clear that data & AI success requires more than unicorn data scientists – [it's an engineering-heavy](https://yanirseroussi.com/2023/06/30/was-data-science-a-failure-mode-of-software-engineering/) endeavour.

## Stealthy AI use may be the wisest approach

_"If you can ask ChatGPT something and get a good answer, so can anyone else"_ (paraphrasing [Rami Mukhtar](https://www.linkedin.com/in/rami-mukhtar-a801801/)).

One corollary to this quote is to avoid building a product that is a thin wrapper around an AI model, or ensuring that you have a data moat.

Another approach is to stop worrying about customer-facing AI:
- You can use AI for back & middle office automation, as done by [some companies in the long tail of AI](https://research.contrary.com/deep-dive/long-tail-of-ai), or by one of the startups cited in my talk.
- You can use AI for trading or betting decisions and not tell anyone about it.
- As an individual in an organisation with restrictive IT policies, use AI on your personal device (but don't be an idiot about it).

My sense is that such stealthy AI use cases are on the rise. It's just not as exciting and visible as sprinkling GenAI fairy dust ✨ on your product.

## Chatty is a UX revolution – model building is dead

Cassie Kozyrkov's talk was in line with what you'd expect from her other content.
I'm not much of a Cassie follower, but poking around her YouTube channel I found the [Making Friends with Machine Learning](https://www.youtube.com/playlist?list=PLRKtJ4IpxJpDxl0NTvNYQWKCYzHNuy2xG) series.
Her keynote covered similar ground, but shorter and updated for the age of GenAI – so not too surprising in terms of content for those who are already in the field (though she is a brilliant speaker).

That said, one of the things I got out of Cassie's talk is that she sees ChatGPT and other GenAI advances as a user experience (UX) revolution.
That is, from the perspective of practitioners training the models, not much has changed.
But from the perspective of the broader population, a lot has changed: AI is now accessible to many more people.

In a separate talk, Greg Baker argued that things have changed for practitioners too.
In his words, _"model building is dead"_.
This is a bold claim that I initially disagreed with, but considering the caveats he included in [his post on the topic](https://solresol.substack.com/p/what-i-see-successful-gen-ai-projects), I'm more or less in agreement.
There is now a broad variety of tasks where prompting is the best approach – effectively killing model building unless you have the data and use case to justify it.

## Testing is key

Even if model building is dead for some tasks, [we can't get away from testing](https://yanirseroussi.com/2024/04/15/ai-does-not-obviate-the-need-for-testing-and-observability/).
This was highlighted in several points from Cassie's talk:
- Beware the AI reliability paradox: intuitively trusting AI because you haven't seen it make mistakes (echoing [stop using LGTM@Few as a metric](https://jxnl.github.io/blog/writing/2024/02/05/when-to-lgtm-at-k/)).
- Test everything in the context of the deployed system.
- Define mistakes based on the purpose of the system, where the purpose depends on the people.
- Things get trickier with GenAI in comparison to traditional (discriminative) AI/ML: now there are endless "right" answers rather than a single one.
- You still need to work with data and stats specialists if you're serious about testing.

My impression is that the last point isn't broadly understood and applied, even among data specialists.
This is partly due to the toxicity of the _data scientist_ term, which is somewhat justified.
Looking at it from an outsider's perspective, if you've only worked with low-skilled data scientists or those who are over-excited about building models, you would be skeptical of the value of data science – especially in light of the historical hype.
But no matter how you feel about evaluating your AI system, if you get serious about it, you'll eventually come to appreciate the importance of rigorous testing.

## Business and product fundamentals remain unchanged

While AI tech is way more capable than it was earlier this century, some things move more slowly.

First, the fundamentals of dealing with enterprise organisations, as covered by [Stephen Samild](https://www.linkedin.com/in/stephensamild/).
I don't have good notes on this, but here are a couple of tables summarising key slides.
I've been contemplating these a lot recently, as they capture some of my career experience.
For example, the numbers in the second table give the pecking order of parts of the organisation, which explains why many data teams feel neglected and under-appreciated.
The way out of this feeling is to better support Sales or Product work – not by building better models.

| Org            | Market relationship | New tech relationship |
|----------------|---------------------|-----------------------|
| **Startup**    | Find                | Existential           |
| **Scaleup**    | Grow                | Opportunistic         |
| **Enterprise** | Protect             | Narcissistic          |
| **Government** | Regulate            | Domestication         |

|                       | Looking out          | Looking in          |
|-----------------------|----------------------|---------------------|
| **Taking orders**     | (1) Sales            | (2) Product         |
| **Fulfilling orders** | (3) Customer Service | (4) Shared Services |

Second, my talk was on the fundamentals: Redefining the FLOPS acronym as a guide to failing with AI ([slides](we-need-more-flops-how-to-fail-with-ai.pdf)).
- **F**orget the end users
- **L**augh off data issues
- **O**bsess over shiny tech
- **P**rocrastinate on pipelines
- **S**tick AI everywhere ✨

I demonstrated these points through quick stories from my experience, and ended with flipping the FLOPS for success:
- **F**ollow end user needs
- **L**oathe data issues
- **O**bserve shiny tech suspiciously
- **P**repare pipelines early
- **S**tick AI where it belongs

None of this should be particularly new to anyone who's been following me, but I suppose that highlighting the fundamentals from different angles is necessary.
I still see people making mistakes I've made over a decade ago (and I sometime repeat my own mistakes).
