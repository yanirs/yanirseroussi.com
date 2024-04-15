---
title: AI does not obviate the need for testing and observability
author: Yanir Seroussi
type: post
date: 2024-04-15T05:00:00+00:00
url: /2024/04/15/ai-does-not-obviate-the-need-for-testing-and-observability/
cover:
  relative: true
  image: cover.webp
  alt: clunky untested bot on the left, slicker bot on the right  
summary: It's easy to prototype with AI, but production-grade AI apps require even more thorough testing and observability than traditional software.
tags:
  - artificial intelligence
  - machine learning
  - software engineering
---
The excitement sparked by ChatGPT has led to a flood of funding for building AI applications, especially around large language models (LLMs). The ease of getting started with AI can lead to excessive enthusiasm, to the point of believing that we have entered a new regime of software development where old best practices no longer apply. The goal of this post is to demonstrate that we are still in the old regime: **Testing and observability remain key to AI success beyond initial prototypes.**

Bookmark and reuse if anyone tries to claim otherwise.

First, let's acknowledge the fact that **prototyping AI applications is now easier than ever.** For example, I recently watched [this video by Hrishi Olickel](https://www.youtube.com/watch?v=8w0hUcQSDy8), which demonstrates how to go from zero to a working AI-powered app in about thirty minutes. Examples like this abound, but I have a feeling that people might miss two key messages from the video:

1. 99% of the time, the problem is with your data.
2. The app isn't ready for production.

**Two elements that solid production-level apps include are testing and observability.** This is highlighted in recent posts by two consultants who are helping companies ship LLM-powered applications:

1. [Your AI Product Needs Evals](https://hamel.dev/blog/posts/evals/) by Hamel Husain. Key quote: _"Unsuccessful products almost always share a common root cause: a failure to create robust evaluation systems."_
2. [Levels of Complexity: RAG Applications](https://jxnl.github.io/blog/writing/2024/02/28/levels-of-complexity-rag-applications/) by Jason Liu. Level 3 is observability. Level 4 is evaluations.

The use of the word _evaluations_ (or _evals_) by both authors is intentional. This is the common term for testing that deals with the challenges of working with LLMs (essentially a complex mapping from any text input to any text output). As noted in [the OpenAI Evals repository](https://github.com/openai/evals):

> If you are building with LLMs, creating high quality evals is one of the most impactful things you can do. Without evals, it can be very difficult and time intensive to understand how different model versions might affect your use case.

That is, we are at the opposite to a new regime where traditional software testing can be forgotten: **Production-level AI apps still require all the usual software tests, _as well as_ AI-specific evaluations.**

In a way, this is nothing new. Before ChatGPT drew significant attention to LLMs, much of the buzz was around traditional machine learning (ML) apps. And [many of the best practices from ML engineering apply to LLM / AI engineering](https://yanirseroussi.com/til/2023/09/21/googles-rules-of-machine-learning-still-apply-in-the-age-of-large-language-models/).

If you are inexperienced with shipping production-grade AI/ML/LLM applications, please don't let it stop you from prototyping. But if you are getting serious about going beyond a prototype, it's time to either get help from experienced AI engineers, or to become one yourself (experience is a great teacher). Just remember that **there is no way around testing and observability if you want to ship a quality product.**
