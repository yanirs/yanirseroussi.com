---
title: What is data science?
author: Yanir Seroussi
type: post
date: 2014-10-23T03:22:08+00:00
url: /2014/10/23/what-is-data-science/
cover:
  image: data-skill-continuum.png
summary: Data science has been a hot term in the past few years. Still, there isn't a single definition of the field. This post discusses my favourite definition.
tags:
  - data science
  - Kaggle
  - software engineering

---
<p class="intro-note">Data science has been a hot term in the past few years. Despite this fact (or perhaps because of it), it still seems like there isn't a single unifying definition of data science. This post discusses my favourite definition.</p>

> Data Scientist (n.): Person who is better at statistics than any software engineer and better at software engineering than any statistician.
> 
> — Josh Wills (@josh_wills) <a href="https://twitter.com/josh_wills/status/198093512149958656" target="_blank" rel="noopener">May 3, 2012</a>

One of my reasons for doing a PhD was wanting to do something more interesting than "vanilla" software engineering. When I was in the final stages of my PhD, I started going to meetups to see what's changed in the world outside academia. Back then, I defined myself as a "software engineer with a research background", which didn't mean much to most people. My first post-PhD job ended up being a data scientist at a small startup. As soon as I changed my LinkedIn title to Data Scientist, many offers started flowing. This is probably the reason why so many people call themselves data scientists these days, often diluting the term to a point where it's so broad it becomes meaningless. This post presents my preferred data science definitions and my opinions on who should or shouldn't call themselves a data scientist.

### Defining data science

I really like the definition quoted above, of data science as _the intersection of software engineering and statistics_. <a href="http://hortonworks.com/blog/hortonworks-hadoop-data-science/" target="_blank" rel="noopener">Ofer Mendelevitch</a> goes into more detail, drawing a continuum of professions that ranges from software engineer on the left to pure statistician (or machine learning researcher) on the right.

{{< figure src="data-skill-continuum.png" alt="Data skill continuum" >}}

This continuum contains two additional roles, which are often confused with data scientists:

  * _Data engineer:_ a software engineer that deals with data plumbing (traditional database setup, Hadoop, Spark and all the rest)
  * _Data analyst:_ a person who digs into data to surface insights, but lacks the skills to do so at scale (e.g., they know how to use Excel, Tableau and SQL but can't build a web app from scratch)

_Data science mixes all these roles_. Because of this, there are few true data science positions for people with no work experience. A successful data scientist needs to be able to "become one with the data" by exploring it and applying rigorous statistical analysis (right-hand side of the continuum). But good data scientists also understand what it takes to deploy production systems, and are ready to get their hands dirty by writing code that cleans up the data or performs core system functionality (left-hand side of the continuum). Gaining all these skills takes time. It is still somewhat rare to find people who are true data scientists according to this definition, which is why <a href="http://hortonworks.com/blog/hortonworks-hadoop-data-science/" target="_blank" rel="noopener">Ofer Mendelevitch's post</a> recommends building teams that consist of people with skills from both sides of the continuum.

### How is data science different from just science?

Data is everywhere. Extracting knowledge from data is an essential part of any science. Hence, the name _data science_ doesn't really capture what's new about the field. The way I see it, the novelty of data science comes from the application of software to model any type of data in a way that generalises across domains. So while a physicist may use software to build models based on data, they won't become a data scientist until they've gone and applied these skills to other fields (as many physicists end up doing). As <a href="http://www.kaggle.com" target="_blank" rel="noopener">Kaggle</a> shows, data scientists can work on a wide variety of problems – from biology and physics to marketing, text mining and web search personalisation. It's often the case in Kaggle competitions that the same people apply similar techniques to very different problems, obtaining results that significantly improve on the state of the art.

However, domain experts such as physicists aren't going to be made redundant any time soon. Contrary to what Kaggle may have you believe, there is much more to data science than predictive modelling on a well-defined problem. Data scientists typically spend much of their time working with domain experts to define the problem, and chasing down diverse data sources to extract features that enable predictive modelling (also known as "the fun part"). Despite the existence of these less-glamorous aspects of data science, there's still a lot of fun to be had working in the area. I highly recommend getting into data science to people who enjoy such challenges.

Getting started as a data scientist is actually pretty simple: become a software engineer, become a data analyst, learn how to model data using software (e.g., by participating in Kaggle competitions), and find a job as a data scientist. Obviously, <a href="http://norvig.com/21-days.html" target="_blank" rel="noopener">it's not going to happen overnight</a>. It took me around 10 ten years, and I'm still learning.
