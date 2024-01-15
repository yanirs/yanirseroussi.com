---
title: Is Data Scientist a useless job title?
author: Yanir Seroussi
type: post
date: 2016-08-04T22:26:03+00:00
url: /2016/08/04/is-data-scientist-a-useless-job-title/
cover:
  relative: true
  image: silly-data-scientist.jpg
summary: It seems like anyone who touches data can call themselves a data scientist, which makes the title useless. The work they do can still be useful, though.
tags:
  - business
  - data science
  - marketing
  - software engineering
  - statistics

---
Data science can be defined as either the [intersection][1] or <a href="http://robjhyndman.com/hyndsight/am-i-a-data-scientist/" target="_blank" rel="noopener">union</a> of software engineering and statistics. In recent years, the field seems to be gravitating towards the broader unifying definition, where everyone who touches data in some way can call themselves a data scientist. Hence, while many people whose job title is Data Scientist do very useful work, the title itself has become fairly useless as an indication of what the title holder actually does. This post briefly discusses how we got to this point, where I think the field is likely to go, and what data scientists can do to remain relevant.

## The many definitions of data science

About two years ago, I [published a post discussing the definition of data scientist by Josh Wills][1], as a _person who is better at statistics than any software engineer and better at software engineering than any statistician_. I still quite like this definition, because it describes me well, as someone with education and experience in both areas. However, to be better at statistics than **any** software engineer and better at software engineering than **any** statistician, you have to be truly proficient in both areas, as some software engineers are <a href="https://code.facebook.com/posts/1072626246134461/introducing-fblearner-flow-facebook-s-ai-backbone/" target="_blank" rel="noopener">comfortable running complex experiments</a>, and some statisticians <a href="https://www.r-project.org/contributors.html" target="_blank" rel="noopener">are capable of building solid software</a>. Quite a few people who don't meet Wills's criteria have decided they wanted to be data scientists too, expanding the definition to be something along the lines of _someone who is better at statistics than some software engineers (who've never done anything fancier than calculating a sample mean) and better at software engineering than some statisticians (who can't code)_.

In addition to software engineering and statistics, data scientists are expected to deeply understand the domain in which they operate, and be excellent communicators. This leads to the proliferation of increasingly ridiculous Venn diagrams, such as the one by <a href="http://datascience.stackexchange.com/a/2406" target="_blank" rel="noopener">Stephan Kolassa</a>:

{{< figure src="perfect-data-scientist-venn-diagram.png" alt="Perfect data scientist Venn diagram" >}}

The perfect data scientist from Kolassa's Venn diagram is a mythical sexy unicorn ninja rockstar who can transform a business just by thinking about its problems. A more realistic (and less exciting) view of data scientists is <a href="http://robjhyndman.com/hyndsight/am-i-a-data-scientist/" target="_blank" rel="noopener">offered by Rob Hyndman</a>:

> I take the broad inclusive view. I am a data scientist because I do data analysis, and I do research on the methodology of data analysis. The way I would express it is that I’m a data scientist with a statistical perspective and training. Other data scientists will have different perspectives and different training.
> 
> We are comfortable with having medical specialists, and we will go to a GP, endocrinologist, physiotherapist, etc., when we have medical problems. We also need to take a team perspective on data science.
> 
> None of us can realistically cover the whole field, and so we specialise on certain problems and techniques. It is crazy to think that a doctor must know everything, and it is just as crazy to think a data scientist should be an expert in statistics, mathematics, computing, programming, the application discipline, etc. Instead, we need teams of data scientists with different skills, with each being aware of the boundary of their expertise, and who to call in for help when required. 

Indeed, data science is too broad for any data scientist to fully master all areas of expertise. Despite the misleading name of the field, it encompasses both science and engineering, which is why data scientists can be categorised into two types, as <a href="https://www.quora.com/What-is-data-science/answer/Michael-Hochster?srid=2sK8&share=98226ca3" target="_blank" rel="noopener">suggested by Michael Hochster</a>:

  * Type A (analyst): focused on static data analysis. Essentially a statistician with coding skills.
  * Type B (builder): focused on building data products. Essentially a software engineer with knowledge in machine learning and statistics.

Type A is more of a scientist, and Type B is more of an engineer. Many people end up doing both, but it is pretty rare to have an even 50-50 split between the science and engineering sides, as they require different mindsets. This is illustrated by the following diagram, showing the information flow in science and engineering (<a href="https://www.farnamstreetblog.com/2013/07/the-difference-between-science-and-engineering/" target="_blank" rel="noopener">source</a>).

{{< figure src="science-versus-engineering.png" alt="Information flow in science and engineering" >}}

## Why Data Scientist is a useless job title

Given that a data scientist is someone who does data analysis, and/or a scientist, and/or an engineer, what does it mean for a person to hold a Data Scientist position? It can mean anything, as it depends on the company and industry. A job title like Data Scientist at Company is about as meaningful as Engineer at Organisation, Scientist at Institution, or Doctor at Hospital. It gives you a general idea what the person's background is, but provides little clue as to what the person actually does on a day-to-day basis.

Don't believe me? Let's look at a few examples. <a href="https://m.signalvnoise.com/data-scientists-mostly-just-do-arithmetic-and-that-s-a-good-thing-c6371885f7f6" target="_blank" rel="noopener">Noah Lorang (Basecamp)</a> is OK with mostly doing arithmetic. <a href="http://varianceexplained.org/r/year_data_scientist/" target="_blank" rel="noopener">David Robinson (Stack Overflow)</a> builds machine learning features and internal R packages, and visualises data. <a href="https://medium.com/@rchang/my-two-year-journey-as-a-data-scientist-at-twitter-f0c13298aee6" target="_blank" rel="noopener">Robert Chang (Twitter)</a> helps surface product insights, create data pipelines, run A/B tests, and build predictive models. <a href="http://robjhyndman.com/hyndsight/am-i-a-data-scientist/" target="_blank" rel="noopener">Rob Hyndman (Monash University)</a> and <a href="http://staff.washington.edu/jakevdp/" target="_blank" rel="noopener">Jake VanderPlas (University of Washington)</a> are academic data scientists who contribute to major R and Python open-source libraries, respectively. From personal knowledge, data scientists in many Australian enterprises focus on generating reports and building dashboards. And in my current role at <a href="https://www.carnextdoor.com.au" target="_blank" rel="noopener">Car Next Door</a> I do a little bit of everything, e.g., implement new features, fix bugs, set up data pipelines and dashboards, run experiments, build predictive models, and analyse data.

To be clear, the work done by many data scientists is very useful. The number of decisions made based on arbitrary thresholds and <a href="https://blog.kissmetrics.com/how-to-calculate-lifetime-value/" target="_blank" rel="nofollow noopener">some means multiplied together on a spreadsheet</a> can be horrifying to those of us with minimal knowledge of basic statistics. Having a good data scientist on board can have a transformative effect on a business. But it's also very easy to end up with ineffective hires working on low-impact tasks if [the business has no idea what their data scientists should be doing][2]. This situation isn't uncommon, given the wide range of activities that _may_ be performed by data scientists, the lack of consensus on the definition of the field, and <a href="https://www.quora.com/What-are-20-questions-to-detect-fake-data-scientists" target="_blank" rel="noopener">a general disagreement over who deserves to be called a <i>real</i> data scientist</a>. We need to move beyond the hype towards clearer definitions that would help align the expectations of data scientists with those of their current and future employers. 

## It's time to specialise

Four years ago, I changed my LinkedIn title from _software engineer with a research background_ to _data scientist_. Various offers started coming my way, and they haven't stopped since. Many people have done the same. To be a data scientist, you just need to call yourself a data scientist. The dilution of the term means that as a job title, it is useless. Useless terms are unlikely to last, so if you're seriously thinking of <a href="https://www.experfy.com/blog/how-to-become-a-data-scientist-part-1-3" target="_blank" rel="noopener">becoming a data scientist</a>, you should also consider specialising. I believe we'll see the emergence of new specific titles, such as <a href="http://machinelearningmastery.com/machine-learning-for-programmers/" target="_blank" rel="noopener">Machine Learning Engineer</a>. In addition, less "sexy" titles, such as Data Analyst, may end up making a comeback. In any case, those of us who invest in building their skills, delivering value in their job, and <a href="http://analyticsmadeskeezy.com/2012/11/05/check-yo-self-5-things-you-should-know-about-data-science-author-note/" target="_blank" rel="noopener">making sure people know about it</a> don't have much to worry about.

What do you think? Is specialisation inevitable or are generalist data scientists here to stay? Please let me know [privately][3], via <a href="https://twitter.com/yanirseroussi" target="_blank" rel="noopener">Twitter</a>, or in the comments section.

 [1]: https://yanirseroussi.com/2014/10/23/what-is-data-science/
 [2]: https://yanirseroussi.com/2015/08/24/you-dont-need-a-data-scientist-yet/
 [3]: https://yanirseroussi.com/about/
