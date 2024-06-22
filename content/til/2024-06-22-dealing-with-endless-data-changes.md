---
title: Dealing with endless data changes
author: Yanir Seroussi
type: til
date: 2024-06-22T22:50:00+00:00
url: /til/2024/06/22/dealing-with-endless-data-changes/
summary: Quotes from Demetrios Brinkmann on the relationship between MLOps and DevOps, with MLOps allowing for managing changes that come from data.
showBreadcrumbs: true
tags:
  - artificial intelligence
  - data strategy
  - DevOps
  - machine learning
  - quotes
  - software engineering
---

I recently listened to [the Super Data Science podcast episode on MLOps: The Job and The Key Tools (with Demetrios Brinkmann)](https://www.superdatascience.com/podcast/mlops-the-job-and-the-key-tools-with-demetrios-brinkmann). The full episode is worth a listen, but one part that especially resonated with me is on how MLOps is about dealing with the unpredictable changes created by data. This is a key difference between working with machine learning in production and traditional applications that are less data-intensive.

Quotes with minor edits:

> And now I think it's very common for people to understand, okay, you need some kind of change management solutions when you're playing around with data, when you're doing things in ML, you need to make sure that if you're going to put something into production, you test it in every way possible before it goes out there. Otherwise, you are left with that situation that can wind you up in the headlines. And you don't want that. Nobody wants to be in the head headlines for bad AI uses.
> 
> [...]
> 
> I also think that MLOps is a subset of DevOps.
> 
> [...]
> 
> It's easy to get caught up in is thinking that MLOps is just implementing some tools and then you're good. But really it's that organizational level and having the reliability, having the ability to put things into production quickly and roll them back if you need to.
> 
> [...]
> 
> DevOps has a lot of change management. So when you make changes to code, you have a process and it's very mature process that goes into that, right? You change code and then you have unit tests and you have integration tests, and you have somebody that's merging the branch and maybe you look over it and so there's a human in the loop and then you roll it out slowly and so you can do some kind of feature flags so that this new code goes into production and you make sure that it doesn't take down the whole website or take down the whole app, whatever it is. Then you have other tools that can monitor if that new feature or that piece of code is actually being used by users.
> 
> None of that exists when it comes to data. Where is all that? So when it comes to data, data's changing all the time and people are making changes to data all the time, whether it's way upstream or downstream.
> 
> [...]
> 
> Data's changing continuously, but there's no integration tests, there's no unit tests, there's no type of feature flag on rolling out these data changes. There's no type of monitoring if the data is actually being used later on or the new data streams, it just can break things. And you see that in a broken ML model that now is making bad predictions or it's going insanely slow for some reason, or it's just not hitting the mark. Or you see it in a broken dashboard, you see it at the end product. And so it's funny to me that, going back to DevOps and that whole idea of change management and having these processes in place so that when you do change something, you can still have the reliability that you are going to be able to push out this change and you don't have to get a call at 03:00 AM.

In short, **unlike software, data changes in ways you can only manage, rather than fully control**. Organisations should recognise this reality and manage data-intensive applications accordingly by adopting MLOps and DataOps practices, in addition to traditional DevOps.
