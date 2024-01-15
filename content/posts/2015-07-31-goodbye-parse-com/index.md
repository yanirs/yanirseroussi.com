---
title: Goodbye, Parse.com
author: Yanir Seroussi
type: post
date: 2015-07-31T03:29:50+00:00
url: /2015/07/31/goodbye-parse-com/
cover:
  relative: true
  image: farewell.jpg
  responsiveImages: false
summary: Migrating my web apps away from Parse.com due to reliability issues. Self-hosting is a better solution.
tags:
  - BCRecommender
  - DevOps
  - parse.com
  - software engineering

---
Over the past year, I've been using <a href="https://parse.com" target="_blank" rel="noopener">Parse</a>&#8216;s free backend-as-a-service and web hosting to serve <a href="http://www.bcrecommender.com" target="_blank" rel="noopener">BCRecommender (music recommendation service)</a> and Price Dingo (now-closed shopping comparison engine). The main lesson: You get what you pay for. Despite some improvements, Parse remains very unreliable, and any time saved by using their APIs and SDKs tends to be offset by having to work around the restrictions of their sandboxed environment. This post details some of the issues I faced and the transition away from the service.

### What's so bad about Parse?

In one word: **reliability**. The service is simply unreliable, with many latency spikes and random errors. I <a href="https://developers.facebook.com/bugs/1550140598598847/" target="_blank" rel="noopener">reported this issue six months ago</a>, and it's still being investigated. Reliability has been a known issue for years (see <a href="http://stackoverflow.com/questions/11283729/how-scalable-is-parse/24253932#24253932" target="_blank" rel="noopener">Stack Overflow</a> and <a href="https://news.ycombinator.com/item?id=8347310" target="_blank" rel="noopener">Hacker News</a> discussions). Parse's acquisition by Facebook over two years ago gave some hope that these issues would be resolved quickly, but this is just not the case.

It is worth noting that the way I used Parse was probably somewhat uncommon. For both Price Dingo and BCRecommender, data was scraped and processed outside Parse, and then imported in bulk into Parse. As bulk imports are not supported by the API, [automating the process required reliance on the web interface][1], which made things somewhat fragile. Further, a few months ago Parse inexplicably dropped support for uploading zipped files, making imports much slower. Finally, when importing large collections, I found that it takes ages for the data to get indexed. The final straw was with the last BCRecommender update, where even after days of waiting the data was still not fully indexed.

### Price Dingo's transition

Price Dingo was a shopping comparison engine with a web interface. The idea was to focus on user needs in specialised product categories, as opposed to the traditional model that requires merchants to pay to be listed. I decided to shut down the service a few months ago to focus on other things, but before the shutdown, I almost completed the transition away from Parse. The first step was replacing the persistence layer with <a href="https://www.algolia.com/" target="_blank" rel="noopener">Algolia &ndash; search engine as a service</a>. Algolia is super-fast, its advanced search capabilities are way better than Parse's search options, and as a paid service their customer support was excellent. If I hadn't shut Price Dingo down, the second step would have been replacing Parse hosting with a more reliable service, as I have recently done for BCRecommender.

### BCRecommender's transition

The Parse-hosted part of BCRecommender was a fairly simple <a href="http://expressjs.com/" target="_blank" rel="noopener">express.js</a> backend that rendered <a href="http://jade-lang.com/" target="_blank" rel="noopener">Jade</a> templates. The fastest transition would probably have been to set up a standalone express.js backend and replace the Parse API calls with calls to the database. But as I much prefer coding in Python ([the recommendation-generating backend is in Python][2]), I decided to completely rewrite the web backend using <a href="http://flask.pocoo.org/" target="_blank" rel="noopener">Flask</a>.

For hosting, I decided to go with <a href="https://www.digitalocean.com/?refcode=cd96cae9d5e1" target="_blank" rel="noopener">DigitalOcean</a> (signing up with this link gives you US$10 credit), because it has a good reputation, and it <a href="https://www.scriptrock.com/articles/cloud-service-provider-roundup-the-best-of-the-best" target="_blank" rel="noopener">compares favourably with other infrastructure-as-a-service providers</a>. For US$10/month you get a server with 1GB of memory, 30GB of SSD storage, and 2TB of data transfers, which should be more than enough for BCRecommender's modest traffic (200 daily users + ~2 bot requests per second). 

Setting up the BCRecommender webapp stack is a bit more involved than getting started with Parse, but fortunately I was already familiar with all parts of the stack. It ended up being almost identical to the stack used in Charlie Huang's blog post <a href="http://www.sasanalysis.com/2015/02/deploy-mongodb-powered-flask-app-in-5.html" target="_blank" rel="noopener">Deploy a MongoDB powered Flask app in 5 minutes</a>: an Ubuntu server running MongoDB as the persistence layer, Nginx as the webserver, Gunicorn as the WSGI proxy, Supervisor for daemon management, and Fabric for managing deployments.

Before deploying to DigitalOcean, I used <a href="https://www.vagrantup.com/" target="_blank" rel="noopener">Vagrant</a> to set up a local development environment, which is almost identical to the production environment. Deployment scripts are one thing that you don't have to worry about when using Parse, as they provide their own build tools. However, it's not too hard to implement your own scripts, so within a few hours I had the environment and the deployment scripts up and ready for translating the webapp code from express.js to Flask.

The translation process was pretty straightforward and actually enjoyable. The Python code ended up being much cleaner and shorter than the JavaScript code (line count reduced to 284 from 378). This was partly thanks to the newly-found freedom of being able to install any package I wanted, and partly due to the reduction in callbacks, which made the code less nested and easier to understand.

I was hoping to use <a href="https://github.com/SyrusAkbary/pyjade" target="_blank" rel="noopener">PyJade</a> to obviate the need for translating the page templates to <a href="http://jinja.pocoo.org/" target="_blank" rel="noopener">Jinja</a>. However, I ran into a bunch of issues and subtle bugs that made me decide to use PyJade for one-off translation to Jinja, followed by a manual process of ensuring that each template was converted correctly. Some of the issues were:

  * Using PyJade's Flask extension compiles the templates to Jinja on the fly, so debugging issues is hard because the line numbers in the generated Jinja templates don't match the line numbers in the original Jade files.
  * Jade allows the use of arbitrary JavaScript code, which PyJade doesn't translate to Python (makes sense &ndash; it'd be too hard and messy). This caused many of my templates to simply not work because, e.g., I used the ternary operator or called a built-in JavaScript function. Worse than that, some cases failed silently, e.g., calling `arr.length` where `arr` is an array works fine in pure Jade, but is undefined in Python because arrays don't have a length attribute.
  * Hyphenated block names are fine in Jade, but don't compile in Jinja.

The conversion to Jinja pretty much offset the cleanliness gained in the Python code, with a growth in template line count from 403 to 464 lines, and much clutter with unnecessary closing tags. Jade, I will miss you, but I guess I can't have it all.

The good news is that latency immediately dropped as I deployed the new environment. The graph below almost says it all. What's missing is the much more massive spikes (5-60 seconds) and timeouts that happen pretty frequently with Parse hosting.

{{< figure src="bcrecommender-latency-digital-ocean.png" alt="BCRecommender latency with DigitalOcean" >}}

Note that this graph is for a simple GET request of the homepage without fetching any of the embedded static assets or running client-side rendering. Handling the request simply populates a Jade template without touching the database. It really shouldn't take too long unless the server is under very heavy load. And even then, Parse is supposed to handle such loads gracefully &ndash; not needing to worry about this kind of stuff is the key reason for using a backend-as-a-service!

### Final thoughts

I really like the idea behind Parse, as setting up and running a web backend is not a trivial task. They do provide some good tooling, and I was happy to work around the minor issues and restrictions that come with working in a sandboxed environment. However, the lack of reliability is a huge disadvantage, even at the attractive price point of $0. Further, there's no indication that paying for the service would increase reliability, as the free tier includes up to 30 requests / second and it can barely handle a single request. Maybe I'll get back to Parse one day, but for now I'm much happier with the increased power and responsibility of managing my own servers.

**Update (30 January, 2016):** <a href="http://blog.parse.com/announcements/moving-on/" target="_blank" rel="noopener">Facebook has announced it will be shutting Parse down</a>, which is a shame. It could have been a great service if they had just focused more on reliability. You just couldn't run serious apps on Parse, which probably meant that not many apps were upgraded to the paid tiers. It's very disappointing that Facebook didn't help Parse realise its potential, but this isn't the first time a big company takes over a small product and shuts it down. It's <a href="http://ourincrediblejourney.tumblr.com/" target="_blank" rel="noopener">just the way of the world</a>.

 [1]: https://yanirseroussi.com/2015/01/15/automating-parse-com-bulk-data-imports/
 [2]: https://yanirseroussi.com/2014/09/07/building-a-recommender-system-on-a-shoestring-budget/
