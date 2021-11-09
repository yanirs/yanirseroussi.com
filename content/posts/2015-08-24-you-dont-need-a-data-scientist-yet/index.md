---
title: You don’t need a data scientist (yet)
author: Yanir Seroussi
type: post
date: 2015-08-24T08:25:30+00:00
url: /2015/08/24/you-dont-need-a-data-scientist-yet/
cover:
  image: hammer.jpg
tags:
  - business
  - data business
  - data science

---
The hype around big data has caused many organisations to hire data scientists without giving much thought to what these data scientists are going to do and whether they're actually needed. This is a source of frustration for all parties involved. This post discusses some questions you should ask yourself before deciding to hire your first data scientist.

### Q1: Do you know what data scientists do?

Somewhat surprisingly, there are quite a few companies that hire data scientists without having a clear idea of what data scientists actually do. People seem to have a fear of missing out on the big data hype, and think of hiring data scientists as the solution. A common misconception is that a data scientist's role includes telling you what to do with your data. While this may sometimes happen in practice, the ideal scenario is where the business has problems that can be solved using data science (more on this under Q3 below). If you don't know what your data scientist is going to do, you probably don't need one.

So what do data scientists do? When you think about it, adding the word "data" to "science" is a bit redundant, as all science is based on data. Following from this, <a href="http://robjhyndman.com/hyndsight/am-i-a-data-scientist/" target="_blank" rel="noopener">anyone who does any kind of data analysis is a data scientist</a>. While it may be true, this broad definition is not very helpful. [As discussed in a previous post][1], it's more useful to define data scientists as individuals who combine expertise in statistics and machine learning with strong software engineering skills.

### Q2: Do you have enough data available?

It's not uncommon to see products that suffer from over-engineering and premature investment in advanced analytics capabilities. In the early stages, it's important to focus on creating a minimum viable product and getting it to market quickly. Data science starts to shine once the product is generating enough data, as most of the power of advanced analytics is in optimising and automating existing processes.

Not having a data scientist in the early stages doesn't mean the data is being ignored &ndash; it just means that it doesn't require the attention of a full-time data scientist. If your product is at an early stage and you are still concerned, you're better off hiring a data science consultant for a few days to help lay out the long-term vision for data-driven capabilities. This would be cheaper and less time-consuming than hiring a full-timer. The exception to this rule is when the product itself is built around advanced analytics (e.g., <a href="http://www.alchemyapi.com/" target="_blank" rel="noopener">AlchemyAPI</a> or <a href="http://www.enlitic.com/" target="_blank" rel="noopener">Enlitic</a>). Building such products without data scientists is far from ideal, or just impossible.

Even if your product is mature and generating a lot of data, it doesn't mean it's ready for data science. Advanced analytics capabilities are at the top of [data's hierarchy of needs][2]: If your product is buggy, or if your data is scattered everywhere and your platform lacks centralised reporting, you need to first invest in fixing your data plumbing. This is the job of [data engineers][1]. Getting data scientists involved when the data is hardly available due to infrastructure issues is likely to lead to frustration. In addition, setting up centralised reporting and dashboarding is likely to give you ideas for problems that data scientists can solve.

### Q3: Do you have a specific problem to solve?

If the problem you're trying to solve is "everyone is doing smart things with data, we should be doing stuff with data too", you don't have a specific problem that can be solved by bringing a data scientist on board. Defining the problem often ends up occupying a lot of the data scientist's time, so you are likely to obtain better results if have more than just a vague idea around "doing something with data, because Hadoop". Ideally you want to optimise an existing process that is currently being solved with heuristics, make an existing model better, implement a new data-driven feature, or something along these lines. Common examples include reducing churn, increasing conversions, and replacing manual processes with automated data-driven systems. Again, getting advice from experienced data scientists before committing to hiring one may be your best first step.

### Q4: Can you get away with heuristics, intuition, and/or manual processes?

Some data scientists would passionately claim that you must deploy only models that are theoretically justified and well-tested. However, in many cases you can get away with using simple heuristics, intuition, and/or manual processes. These can be orders of magnitude cheaper than building sophisticated predictive models and the infrastructure to support them. For many businesses, there are more pressing needs than doing everything in a theoretically sound way. Despite what many technical people like to think, customers don't tend to care how things are implemented, as long as their needs are fulfilled.

For example, I spent some time with a client whose product includes a semi-manual part where structured data is extracted from documents. Their process included sending some of the documents to a trained team in the Philippines for manual analysis. The client was interested in replacing that manual work with a machine learning algorithm. As is often the case with machine learning, it was unknown whether the resultant model would be accurate enough to completely replace the manual workers. This generally depends on data quality and the feasibility of solving the problem. Assessing the feasibility would have taken some time and money, so the client decided to park the idea and focus on other areas of their business.

Every business has resource constraints. Situations where the best investment you can make is hiring a full-time data scientist are rarer than what the hype may make you think. It's often the case that functions that would be the responsibility of a data scientist are adequately performed by existing employees, such as software engineers, business/data analysts, and marketers.

### Q5: Are you committed to being data-driven?

I have seen more than one case where data scientists are hired only to be blocked or ignored. This is more prevalent in the corporate world, where managers are often incentivised to prioritise doing things that look good over things that make financial sense. But even if recruitment is done with the best intentions, progress may be blocked by employees who feel threatened because they would be replaced by automated data-driven algorithms. Successful data science projects require support from senior leadership, as discussed by <a href="http://venturebeat.com/2015/07/22/stop-hiring-data-scientists-until-youre-ready-for-data-science/" target="_blank" rel="noopener">Greta Roberts</a>, <a href="https://berlinbuzzwords.de/sites/berlinbuzzwords.de/files/media/documents/radim_rehurek-so_you_want_to_be_a_data_science_consultant.pdf" target="_blank" rel="noopener">Radim Řehůřek</a>, <a href="https://www.linkedin.com/pulse/big-data-science-analytics-australia-alec-smith" target="_blank" rel="noopener">Alec Smith</a>, and many others. Without such support and a strong commitment to making data-driven decisions, everyone is just wasting their time.

### Closing thoughts

While data science is currently over-hyped, many organisations still have much to gain from hiring data scientists. I hope that this post has helped you decide whether you need a data scientist right now. If you're unsure, please don't hesitate to <a href="https://yanirseroussi.com/about/" target="_blank" rel="noopener">contact me</a>. And to any data scientists reading this: Be very wary of potential employers who do not have good answers to the above questions. At this point in time you can afford to be picky, at least until the hype is over.

 [1]: https://yanirseroussi.com/2014/10/23/what-is-data-science/
 [2]: https://yanirseroussi.com/2014/08/17/datas-hierarchy-of-needs/
