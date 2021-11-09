---
title: 'Building a recommender system on a shoestring budget (or: BCRecommender part 2 – general system layout)'
author: Yanir Seroussi
type: post
date: 2014-09-07T10:48:44+00:00
url: /2014/09/07/building-a-recommender-system-on-a-shoestring-budget/
cover:
  image: bcrecommender-architecture.png
tags:
  - Bandcamp
  - BCRecommender
  - DevOps
  - recommender systems
  - software engineering

---
<p class="intro-note">This is the second part of a series of posts on my <a href="http://www.bcrecommender.com" target="_blank" rel="noopener">BCRecommender – personalised Bandcamp recommendations</a> project. Check out <a href="http://yanirseroussi.com/2014/08/30/building-a-bandcamp-recommender-system-part-1-motivation/">the first part</a> for the general motivation behind this project.</p>

<a href="http://www.bcrecommender.com" target="_blank" rel="noopener">BCRecommender</a> is a hobby project whose main goal is to help me find music I like on <a href="https://bandcamp.com" target="_blank" rel="noopener">Bandcamp</a>. Its secondary goal is to serve as a testing ground for ideas I have and things I'd like to explore.  
One question I've been wondering about is: how much money does one need to spend on infrastructure for a simple web-based product before it reaches meaningful traffic?  
The answer is: not much at all. It can easily be done for less than $1 per month.  
This post discusses my exploration of this question by describing the main components of the BCRecommender system, without getting into the algorithms that drive it (which will be covered in subsequent posts).

The general flow of BCRecommender is fairly simple: crawl publicly-available data from Bandcamp (fan collections and tracks/albums = tralbums), generate recommendations based on this data (static lists of tralbums indexed by fan for personalised recommendations and by tralbum for similarity), and present the recommendations to users in a way that's easy to browse and explore (since we're dealing with music it must be playable, which is easy to achieve by embedding Bandcamp's iframes).

### First iteration: Django & AWS

The first iteration of the project was implemented as a <a href="https://www.djangoproject.com/" target="_blank" rel="noopener">Django</a> project. Having never built a Django project from scratch, I figured this would be a good way to learn how it's done properly. One thing I was keen on learning was using the Django ORM with an SQL database (in the past I've worked with Django and <a href="https://www.mongodb.org/" target="_blank" rel="noopener">MongoDB</a>). This ended up working less smoothly than I expected, perhaps because I'm too used to MongoDB, or because SQL forces you to model your data in unnatural ways, or because I insisted on using <a href="https://sqlite.org/" target="_blank" rel="noopener">SQLite</a> for simplicity. Whatever it was, I quickly started missing MongoDB, despite its flaws.

I chose <a href="https://aws.amazon.com/" target="_blank" rel="noopener">AWS</a> for hosting because my personal account was under the free tier, and using a micro instance is more than enough for serving a website with no traffic. I considered <a href="https://developers.google.com/appengine/" target="_blank" rel="noopener">Google App Engine</a> with its indefinite free tier, but after reading the docs I realised I don't want to jump through so many hoops to use their system – Google's free tier was likely to cost too much in pain and time.

While an AWS micro instance is enough for _serving_ the recommendations, it's not enough for generating them. Rather than paying Amazon for another instance, I figured that using spare capacity on my own laptop (quad-core with 16GB of RAM) would be good enough. So the backend worker for BCRecommender ended up being a local virtual machine using one core and 4GB of RAM.

After some coding I had a nice setup in place:

  * AWS webserver running Django with SQLite as the database layer and a simple frontend, styled with <a href="http://getbootstrap.com/" target="_blank" rel="noopener">Bootstrap</a>
  * Local backend worker running <a href="http://www.celeryproject.org/" target="_blank" rel="noopener">Celery</a> under <a href="http://supervisord.org/" target="_blank" rel="noopener">Supervisor</a> to collect the data (with errors reported to a dedicated Gmail account), Dropbox for backups, and Django management commands to generate the recommendations
  * Code and issue tracker hosted on <a href="https://bitbucket.org/" target="_blank" rel="noopener">Bitbucket</a> (which provides free private repositories)
  * <a href="http://www.fabfile.org/" target="_blank" rel="noopener">Fabric</a> scripts for deployments to the AWS webserver and the local backend worker (including database sync as one big SQLite file)
  * Local virtual machine for development (provisioned with <a href="http://www.vagrantup.com/" target="_blank" rel="noopener">Vagrant</a>)

This system wasn't going to scale, but I didn't care. I just used it to discover new music, and it worked. I didn't even bother registering a domain name, so it was all running for free.

### Second iteration: "Django" backend & Parse

A few months ago, <a href="http://blog.parse.com/2014/04/30/parse-pricing-now-cheaper-and-simpler/" target="_blank" rel="noopener">Facebook announced that Parse's free tier will include 30 requests / second</a>. That's over 2.5 million requests per day, which is quite a lot – probably enough to run the majority of websites on the internet. <!--In addition, Parse is meant to be a backend service for mobile apps. Being able to use it for website hosting as well appears to be a pleasant side effect.--> It seemed too good to be true, so I had to try it myself.

It took a few hours to convert the Django webserver/frontend code to Parse. This was fairly straightforward, and it had the added advantages of getting rid of some deployment scripts and having a more solid development environment. Parse supplies a command-line tool for deployment that constantly syncs the code to an app that is identical to the production app – much better than the Fabric script I had.

The disadvantages of the move to Parse were having to rewrite some of the backend in JavaScript (= less readable than Python), and a more complex data sync command (no longer just copying a big SQLite file). However, I would definitely use it for other projects because of the generous free tier, the availability of APIs for all major platforms, and the elimination of most operational concerns.

### Current iteration: Goodbye Django, hello BCRecommender

With the Django webserver out of the way, there was little use left for Django in the project. It took a few more hours to get rid of it, replacing the management commands with <a href="https://github.com/tellapart/commandr" target="_blank" rel="noopener">Commandr</a>, and the SQLite database with MongoDB (wrapped with the excellent <a href="http://mongoengine.org/" target="_blank" rel="noopener">MongoEngine</a>, which has matured a lot in recent years). MongoDB has become a more natural choice now, since it is the database used by Parse. I expect this setup of a local Python backend and a Parse frontend to work quite well (and remain virtually free) for the foreseeable future.

The only fixed cost I now have comes from registering the <a href="http://www.bcrecommender.com" target="_blank" rel="noopener">bcrecommender.com domain</a> and managing it with Route 53. This wasn't required when I was running it only for myself, and I could have just kept it under bcrecommender.parseapp.com, but I think it would be useful for other Bandcamp users. I would also like to use it as a training lab to improve my (poor) marketing skills – not having a dedicated domain just looks bad.

In summary, it's definitely possible to build simple projects and host them for free. It also looks like my approach would scale way beyond the current BCRecommender volume. The next post in this series will cover some of the algorithms and general considerations of building the recommender system.
