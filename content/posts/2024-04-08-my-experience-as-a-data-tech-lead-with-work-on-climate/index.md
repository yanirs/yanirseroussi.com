---
title: My experience as a Data Tech Lead with Work on Climate
author: Yanir Seroussi
type: post
date: 2024-04-08T02:00:00+00:00
url: /2024/04/08/my-experience-as-a-data-tech-lead-with-work-on-climate/
cover:
  relative: true
  image: cover.webp
summary: The story of how I joined Work on Climate as a volunteer and became its data tech lead, with lessons applied to consulting & fractional work.
tags:
  - career
  - climate change
  - data engineering
  - data science
  - data strategy
  - environment
  - personal
  - remote work
  - startups
---
After leaving [my last startup gig](https://yanirseroussi.com/2022/06/06/the-mission-matters-moving-to-climate-tech-as-a-data-scientist/) last year, I gave myself time to explore. My plan was to build my own product business while doing a bit of consulting on the side. As I was researching the climate tech space, I attended [Work on Climate's Expert Office Hours](https://workonclimate.org/expert-office-hours/) to get feedback on one of my ideas. The session was informative &ndash; it helped me avoid the common trap of techies, and _not_ build something I would find hard to sell.

To my surprise, I received an email from a user researcher with Work on Climate shortly after the session. They wanted to interview me about my experience booking and attending the Expert Office Hours. This was a level of professionalism I wasn't expecting from an organisation that's mostly run by volunteers!

Following that experience, I poked around the Work on Climate website and saw they were looking for a volunteer Data Engineer on the Metrics & Data Team. Despite being [reluctant to do data engineering work full time](https://yanirseroussi.com/2023/10/25/lessons-from-reluctant-data-engineering/), the specified time commitment of five hours per week for six months seemed manageable. I like maintaining awareness of what's happening in the data engineering world, and this seemed like a productive way of doing it: supporting climate tech work and giving back to an organisation that has helped me. Further, I thought it'd be fun to join a global team of highly-skilled volunteers while figuring out my solo ventures.

## Applying and joining the team

My impression of Work on Climate as a professional organisation was reinforced throughout the application and onboarding process:
- Despite being primarily run by volunteers, positions are advertised on a [Work with Us](https://workonclimate.org/careers/) page with descriptions that are similar to those of full-time jobs.
- In my application, I had to address key criteria: share why I wanted to volunteer, explain how I'd address common challenges with the role (listed in the position description), and describe a side project that demonstrates my volunteer experience.
- Following the submission of the application form, I had screening calls with a recruiter ([Sarah Fowler](https://www.linkedin.com/in/sarah-fowler-wa/)), the team lead ([Xanthe Travlos](https://www.linkedin.com/in/xanthetravlos/)), and a data engineer on the team ([Misha Panshenskov](https://www.linkedin.com/in/mikpan/)).

In general, this was much like a "normal" job application process, but condensed. If you look through the LinkedIn profiles above, you'll see why: Work on Climate volunteers have extensive professional experience in the same fields they contribute to as part of the organisation.

The theme of volunteering being like a normal job but condensed extended throughout my onboarding and initial work. I went through the usual experience of getting access to systems, becoming familiar with the team and problems, and picking up my first introductory issues &ndash; just as I would if this were a full-time job. In addition to being condensed, another big difference to a full-time job was the passage of time: As a volunteer workweek is only five hours, any project that spans a few workdays becomes weeks in calendar time. This requires being more mindful of delivering incremental value than you would in a full-time environment: Challenging, but doable.

## Becoming a tech lead

One of the challenges listed in the job ad was:

> We are a start-up in our data maturity—we are still figuring out how to use data and how best to model and transform it to meet wider team needs. Some things we do might not make sense to you—we’ll welcome your suggestions on how to improve things!

Other challenges were along the same lines, so my response to the application question about addressing them was:

> The challenges listed sound like many organisations I've worked with, especially having a distributed time-constrained team with a data stack that grows organically and isn't very well-documented. I don't think there's a silver bullet to address those challenges other than patiently getting up to speed and working with others to figure out the top priorities. It also makes sense to add documentation as part of my on-boarding. I suspect that prioritisation and planning given the volunteer time constraints will be key, but even when working with full-timers it's often the case that there's more work than time.

Indeed, that was pretty much what happened. While my original intent was to act as an individual contributor, I find it hard to hold back when I see ways to improve processes and systems. As promised in the ad, my suggestions were well-received, but beyond what I had expected: Xanthe suggested we become co-leads of the Metrics & Data team. This made sense given that our backgrounds are complementary &ndash; she has extensive product management experience, while I have more hands-on exposure to the data world. Therefore, we settled into a new team structure, with her retaining the team lead position and business-facing / product management responsibilities, and me setting the technical direction for the data platform.

This pattern matches what had happened before in some of my full-time roles. For example, in [my work with Automattic](https://yanirseroussi.com/2021/10/07/my-work-with-automattic/), I became the tech lead for the experimentation platform after organically spotting the need for better experimentation processes when working on machine learning for marketing applications. With Automattic, as with Work on Climate, working as a tech lead alongside a capable product manager and team lead allowed us both to capitalise on our strengths.

A brief example to illustrate the need for a data tech lead: As promised in the job ad, one of the challenges with Work on Climate is that the data stack has evolved "organically". This included data coming from scheduled Jupyter notebooks, various APIs (via a JavaScript codebase), and some transformations with [dbt](https://www.getdbt.com/product/what-is-dbt). As the notebooks weren't well-maintained, it made sense to absorb them into other parts of the stack and reduce the maintenance load. As a tech lead, I help spot and prioritise such work, moving Work on Climate towards [a minimum viable data stack](https://yanirseroussi.com/2024/02/19/building-your-startups-minimum-viable-data-stack/) that serves the organisation's needs.

## Challenges and opportunities

Much has been happening concurrently to my work with Work on Climate. My exploration of product ideas that I could bootstrap by myself led me to the realisation that [the lines between solo consulting and product building are blurry](https://yanirseroussi.com/til/2023/09/25/the-lines-between-solo-consulting-and-product-building-are-blurry/). Borrowing from [Jonathan Stark](https://jonathanstark.com/daily/20200504-1409-the-only-business-strategy-youll-ever-need), my business strategy has turned into _helping people I like get what they want_, which seems easier to achieve as a solo consultant than by building a software product. While [concise positioning remains a challenge](https://yanirseroussi.com/til/2023/12/18/positioning-is-a-common-problem-for-data-scientists/), I started taking my consulting practice more seriously rather than seeing as it a side gig. My goal is to help climate tech and nature-positive startups with the sort of problems I've been helping Work on Climate and various companies throughout my career, i.e., with shipping Data & AI solutions. However, like many solo consultants, I've discovered that generating a pipeline of qualified leads is a key challenge &ndash; harder than the technical aspects of my work.

One unexpected challenge with my climate focus has been [the October 7th attacks on Israel](https://en.wikipedia.org/wiki/2023_Hamas-led_attack_on_Israel). While I've been living in Australia since 2009, I am a Jew from Israel, so I've been deeply affected by October 7th and its aftermath. Beyond the horror of the massacres, [I was horrified by the response of some politicians and activists who claim to be "green"](https://www.linkedin.com/feed/update/urn:li:activity:7118365271970443264/). Fortunately, I haven't witnessed such responses within Work on Climate, where the internal reaction was of support and understanding of [the human suffering caused by wars](https://edition.cnn.com/2024/04/05/opinions/israel-gaza-6-months-october-7-ghitis/index.html). However, these events have led me to revise the criteria of _"people I like"_ and want to help in the climate space. I definitely dislike those who promote [Jew hatred](https://www.australianjewishnews.com/dead-jews-and-live-antisemites/) or support [calls for the destruction of Israel](https://www.linkedin.com/posts/yanirseroussi_just-a-reminder-that-from-the-river-to-the-activity-7125612754731724801-1gUZ/) (which would result in the death of my family). Fortunately, this doesn't exclude everyone, as there's a fair number of Jews and generally-decent people who are focused on building climate solutions &ndash; truly hateful people are a loud minority.

Anyway, by the beginning of 2024 I managed to find a new balance and a professional direction as an independent consultant. Further, volunteering with Work on Climate has highlighted an opportunity for consulting engagements: I learned that it is possible to provide value as a data tech lead even with five hours per week. The trendy name for this is [a fractional chief data/analytics/AI officer](https://www.fractionaldefined.com/). My ideal clients for such engagements are startups around the stage of [getting their first data hire](https://yanirseroussi.com/2024/02/05/substance-over-titles-your-first-data-hire-may-be-a-data-scientist/), with a similar level of data maturity to Work on Climate.

That said, Work on Climate has some unique challenges and opportunities that don't show up in startups with similar data maturity. On the one hand, given the large number of volunteers, keeping everyone in sync and breaking down silos is harder than with a smaller group of employees. On the other hand, the cost of "hiring" volunteers is in recruitment and onboarding rather than in ongoing salaries, which gives the organisation access to "free" fractional talent that most startups can only dream of. In any case, it is an interesting organisation to volunteer with if you come in with the right mindset. From a logistical viewpoint, it's good fit if you know you'll have about five hours per week for at least six months, keeping in mind that the hours may be spread throughout the week (e.g., for calls and discussions with other volunteers).

## Future moves

My original intention was to help Work on Climate for at least six months. I am now about nine months in. With my newfound consulting focus, I find that I have quite a bit to juggle outside Work of Climate. While I would love to do it all, I have less of the mental space to contribute to the organisation. Therefore, we are looking for someone to replace me in the coming months. However, I will likely still contribute on a more limited advisory basis. If you are interested in volunteering with Work on Climate, or know someone who would be a suitable data tech lead, please get in touch!

{{< figure src="work-on-climate-six-month-milestone-award.webp" caption="This milestone award is another example of Work on Climate's similarity to full-time work environments. It's nice to be recognised!" alt="Six-month milestone award from Work on Climate, recognising my contribution to the organisation." >}}
