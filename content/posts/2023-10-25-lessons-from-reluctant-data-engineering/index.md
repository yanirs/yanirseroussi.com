---
title: Lessons from reluctant data engineering
author: Yanir Seroussi
type: post
date: 2023-10-25T04:45:00+00:00
url: /2023/10/25/lessons-from-reluctant-data-engineering/
cover:
  relative: true
  image: yanir-seroussi-dataengbytes-brisbane-2023.webp
  alt: Yanir Seroussi presenting at DataEngBytes Brisbane 2023
summary: Video and summary of a talk I gave at DataEngBytes Brisbane on what I learned from doing data engineering as part of every data science role I had.
tags:
  - career
  - data engineering
  - data science
  - software engineering

---

In May 2023, I submitted the following talk abstract to the Brisbane [DataEngBytes](https://dataengconf.com.au/) conference.

> As we all know, solid data engineering is essential to the success of data science and AI applications. And yet, people often get excited about fancy machine learning models and neglect the data engineering layer. This is totally understandable: playing with data in a throwaway notebook is more relaxing than dealing with a data pipeline that keeps finding ways to break in production.
>
> In this talk, I'll share lessons on data engineering from a data science perspective. Everywhere I've worked, from small start-ups to established companies, I've found that I had to do some data engineering if I wanted my work to ever get to production. While I've always been reluctant to do too much of it, my engineering background has placed me in a better position to do it than colleagues who started off as analysts and academics.
>
> You could call my work full-stack data science, reluctant data engineering, or some other data & AI thing. Whatever it is, I hope that my talk will help us all play better with each other, across all layers of the data stack.

As I don't identify as a data engineer and have never attended a DataEngBytes conference, I didn't know whether my talk would fit the agenda. However, it seemed harmless to submit an abstract and see how it goes.

When I got the acceptance notification and realised I had to turn my abstract into a coherent talk, I was a bit wary of lacking a good grasp of who's in my audience. However, when the full agenda was published, I realised that the focus of the conference won't be on arcane data engineering knowledge, given that one of the keynotes was titled _"How The Full-Stack Data Scientist Is STILL The Sexiest Job"_. It turned out that despite the name and tagline (_"by data engineers, for data engineers"_), DataEngBytes was a great event for all data professionals.

Here's the video of the talk ([slides](https://docs.google.com/presentation/d/100GiDkp3UKfQtWtxZOF4CaJWTuSYtkEYxkI0_INdqq8/edit)):

{{< youtube id="NE6e7Xx7OLQ" title="Talk video: Lessons from reluctant data engineering" >}}
<br>
**Quick summary.** I start off with a disclaimer, stating that I am not a data engineer. Then I show evidence that the market values data engineering more than data science, given the ratio of _Data Engineer_ to _Data Scientist_ job ads (x3 in the AU$100-150k compensation range; x4 in the AU$200k+ range).[^seek-details] I follow that observation with another disclaimer, stating that some of my lessons may be obvious or better learnt the hard way (as I often have to learn and relearn lessons). Then I detail five chronologically ordered snippets and their corresponding lessons:

1. 2012: My first data science job, where we made mistakes around technology choice and premature optimisation. The lesson is that **shiny tech ain't always shiny**. Like all lessons, this one ends with a quote that shows that what I learned wasn't entirely new. The first quote is by Donald Knuth from 1974: _"We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%."_
2. 2013: My first head of data science job, where we solved real scaling issues by following principles and adapting solutions to our situation. The lesson is that **shiny tech can be transformative; but principles beat tools**, which goes with a 1911 quote by Harrington Emerson: _"As to methods, there may be a million and then some, but principles are few. The person who grasps principles can successfully select their own methods. The person who tries methods, ignoring principles, is sure to have trouble."_[^emerson-man]
3. 2015: My first enterprise consulting stint, where I experienced being a not-so-useful data scientist and working with some not-so-useful data engineers. This led me to dabble in "shadow IT" (a term I learned at the conference), and build a separate Python machine learning pipeline to work around various limitations. The lesson is that you should **solve problems; don’t be the problem**, or in the words of circa 2004 Google: _"Focus on the user and all else will follow."_
4. 2017: My first remote data science job, where I played around with many job functions across the data stack and went down various data rabbit holes. The lesson is to **go deep; trust but verify**, which goes with a 1999 quote by Eric S. Raymond: _"Given enough eyeballs, all bugs are shallow."_
5. 2022: My first committed climate and biodiversity moves (still a work in progress). The lesson is that **tech & titles are tools; focus on what matters**, but recall Rabbi Tarfon's quote from almost two thousand years ago: _"You are not obliged to complete the work, but neither are you free to desist from it."_

The main takeaway from the talk is that **data problems have human roots – and human solutions**. This is because:

* Humans get excited by shiny tech... and produce transformative tech.
* Humans optimise prematurely... and when it makes sense.
* Humans can act as unreasonable blockers... and as the users we serve.
* Humans generate messy data... and clean it up.
* Humans get distracted by tools... and use them for beneficial ends.

[^seek-details]: This is based on [Seek](https://www.seek.com.au/) searches for jobs advertised in July 2023. Given the limitations of Seek search, it's not an accurate representation of the demand for each role, as the results included all ads that _mentioned_ the terms. One could also argue that data engineers tend to change jobs more than data scientists, fuelling demand. Despite this, I think the results support the general message around the value of data engineering, especially as [others have noted the need for 4-5 data engineers per data scientist in organisations with complex data engineering requirements](https://www.oreilly.com/radar/data-engineers-vs-data-scientists/).
[^emerson-man]: Emerson referred to _man_ rather than _person_ in the original quote, but I took the liberty to make it gender-neutral and retain the original message.
