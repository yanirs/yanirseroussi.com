---
title: 'Avoiding AI complexity: First, write no code'
author: Yanir Seroussi
type: post
date: 2024-02-26T00:00:00+00:00
url: /2024/02/26/avoiding-ai-complexity-first-write-no-code/
cover:
  relative: true
  image: first-write-no-code-primum-non-codere.webp
  alt: "Illustration showing ancient stone tablets with the inscription 'primum non codere' (inspired by primum non noncere: first, do no harm)" 
summary: Two stories of getting AI functionality in the hands of users demonstrate the risks inherent in custom development versus starting with no-code approach.
tags:
  - artificial intelligence
  - data strategy
  - machine learning
  - software engineering
  - startups
---
Custom software is notoriously hard to build and maintain. Machine learning (ML) adds a layer of complexity on top of traditional software, with [many novel ways to accrue technical debt](https://proceedings.neurips.cc/paper_files/paper/2015/file/86df7dcfd896fcaf2674f757a2463eba-Paper.pdf). Therefore, my general advice to young startups considering custom ML development borrows from [the first and second rules of optimisation](https://wiki.c2.com/?RulesOfOptimization):

1. Don't.
2. Don't Yet (for experts only).

For startups where Data & AI/ML isn't a core part of the team's capabilities, there are usually higher priorities than building custom ML models. However, deriving commercial value from advancements in AI is still possible &ndash; even without writing code at all.

I recently witnessed two stories that exemplify this point.

**Exhibit A.** Consider this story: A technical lead reached out to me for advice on a computer vision project that wasn't progressing as expected. For the sake of illustration, let's say it was a custom model to [classify food pictures as hotdog / not hotdog](https://www.theverge.com/tldr/2017/5/14/15639784/hbo-silicon-valley-not-hotdog-app-download).

The company had contracted an ML engineer to drive the project. Despite having no background in ML, the lead felt like the contractor was going down the wrong track, and asked me for my thoughts.

It turned out that the contractor believed that the best path forward was trying different model architectures. My advice was to ensure the contractor did the data work first. Often, [there are bigger gains to be had from data augmentations than from model tweaks](https://journalofbigdata.springeropen.com/articles/10.1186/s40537-019-0197-0) (e.g., applying distortions to the hotdog photos). As the data wasn't sensitive, I also suggested trying third-party computer vision APIs or GPT-4 Vision to get an idea of what's possible with the dataset.

**Exhibit B.** Recently, I caught up with an entrepreneur who comes from a marketing background. Just prior to our meeting, they had successfully pitched an app they had built to a large client.

Remarkably, **the app included a hotdog detector similar to the one the ML engineer was struggling to ship.** The entrepreneur used the [FlutterFlow](https://flutterflow.io/) no-code platform along with Google's computer vision APIs to rapidly create an app with commercial value &ndash; without deep knowledge of ML.

## Expanding the rules

No two companies are exactly alike. Sometimes, custom code or ML models are necessary. However, given the pace of innovation in no-code and low-code software & AI, starting with the least code possible is often a wise choice. Those who build software as their craft often have a blind spot when it comes to no-code possibilities &ndash; _coders gonna code_. However, it's important to rein in the coding instinct. The difference in total cost between a custom build and using third-party APIs or no-code solutions can easily be in six or seven figures.

When contemplating custom ML and AI development, consider the following options:

1. Don't build it.
2. [Wait until it becomes easier](https://www.oneusefulthing.org/p/the-lazy-tyranny-of-the-wait-calculation).
3. Use a no-code solution.
4. Get a software engineer to implement it with third-party APIs.
5. Get a software engineer to implement it with third-party models that you self-host (with minimal customisation).
6. Get the experts to build it: ML engineers, data scientists, and data engineers.

You should be pretty certain that the cost of Option 6 is worth the investment. One way to get there is by starting with one of Options 3-5, thereby proving (or disproving) that there's commercial value in the most expensive option. And when the time comes for Option 6, [always do the data work](https://yanirseroussi.com/2014/08/17/datas-hierarchy-of-needs/)!
