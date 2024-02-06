---
title: Future software development may require fewer humans
author: Yanir Seroussi
type: til
date: 2024-02-06T06:15:00+00:00
url: /til/2024/02/06/future-software-development-may-require-fewer-humans/
summary: Reflecting on an interview with Jason Warner, CEO of poolside.
showBreadcrumbs: true
tags:
  - artificial intelligence
  - quotes
  - software engineering
---

I listened to [an interesting interview with Jason Warner](https://www.superdatascience.com/podcast/a-code-specialized-llm-will-realize-agi-with-jason-warner), CEO of [poolside](https://www.poolside.ai/), which works on _"building the world's most capable AI for software development"_. Key quotes:

> So imagine, if you will, that GPT-4, which is, as far as I'm concerned, the gold standard. It is by far the best in almost every way possible at what it does. But let's just call GPT-4, for the moment, the Toyota Camry. It is a vehicle. It is the bestselling sedan in the world, and is a general purpose vehicle. It can take you to work, go on vacation, haul your family around, go get groceries. But imagine all of a sudden, because it's the only vehicle in the world at the moment, you start abusing it for things that it really wasn't built for.
> \[...\]
> Well, we're introducing a new vehicle type. So still a large language model with applications that are built on top of it, but it's a new vehicle type, and it's the Ford F-150. And it is specifically built for those environments and those orientations and those jobs.

> From a model perspective, there's a massive, massive difference between us and others in that, one, something that's tuned for software will know more about software. \[...\] OpenAI has made famous reinforcement learning via human feedback. Anthropic has made famous reinforcement learning via constitutional AI or algorithmic AI and things of that nature. We're introducing something that we call reinforcement learning via code execution feedback. So taking advantage of the aspects of software and the aspects of code that you might imagine. One, it's inspectable, two, it's runnable, and three, you have to compile or execute these things and you can get deterministic feedback. And so what we have done is inside of our training set, we've made very, very, very, very different decisions than general purpose models would make.
> 
> And this goes to the heart of why a truck is different than a sedan, we've made very different design decisions. We have included only high-quality code in the model. We have cut data sources out of the initial dataset because it's a very different audience that's going to use this for a very different purpose. And so this goes to the reinforcement learning side of the fence, too. We care very deeply that yeah, we'll have human feedback as well, but the reinforcement learning is going to be all about what's produced from the software side. So we've taken about 50,000 high quality real-world projects out of the initial training dataset and are using it on the reinforcement side. We've made all the git commits executable. We have all three legs of the stool that we need. We've got the issue that's described in real language. We've got the code, we've got tests, we've got all of the things that we need, and we send this through a reinforcement learning platform on our model to see what it does.

I find the idea of reinforcement learning from code execution feedback very compelling. Given how well GPT-4 already performs, it makes sense that you could get much better results by following poolside's approach.

As with other AI advancements, the implications on society are likely to be profound. It's not hard to imagine a situation where software development becomes much less labour-intensive than it is today, leading to unemployment among software developers. Or it could be that access to better AI software developers would lead to much more software getting built. Who knows?

My bet is on the future of software development being quite different from today, and on things changing more rapidly than most people realise. Skills that are valuable today may be obsolete within 5-10 years. Rephrasing poolside's website, we're likely to switch from human-led-AI-assisted development to AI-led-human-assisted development.  
