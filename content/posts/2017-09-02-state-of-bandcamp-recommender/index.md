---
title: State of Bandcamp Recommender, Late 2017
author: Yanir Seroussi
type: post
date: 2017-09-02T10:19:02+00:00
url: /2017/09/02/state-of-bandcamp-recommender/
aliases:
 - /state-of-bandcamp-recommender-september-2017/
cover:
  image: bcrecommender-homepage.jpg
summary: Call for BCRecommender maintainers followed by a decision to shut it down, as I don't have enough time and Bandcamp now offers recommendations.
tags:
 - Bandcamp
 - BCRecommender

---
## November 2017: Update and goodbye

I've decided to shut down Bandcamp Recommender (BCRecommender), despite hearing back from a few volunteers. The main reasons are:

  1. Bandcamp now shows album recommendations at the bottom of album pages. While this isn't quite the same as BCRecommender, I hope that it will evolve to a more comprehensive recommender system.
  2. I tried to contact Bandcamp to get their support for the continued running of BCRecommender. I have not heard back from them. It would have been nice to receive some acknowledgement that they find BCRecommender useful.
  3. As discussed below, I don't have much time to spend on the project, and handing it off to other maintainers would have been time-consuming. Given reasons 1 and 2, I don't feel like it's worth the effort. Thanks to everyone who's contacted me &ndash; you're awesome!

## September 2017: Original announcement

I [released the first version of Bandcamp Recommender (BCRecommender) about three years ago][1], with the main goal of surfacing music recommendations from [Bandcamp][2]. A secondary goal was learning more about building and marketing a standalone web app. As such, I shared a few posts about BCRecommender over the years:

  * Initial posts on [the motivation behind building BCRecommender][1], [original system layout][3], and [the recommendation engine][4].
  * Marketing-oriented posts on [applying the Traction Book's framework to BCRecommender][5], followed by [an update on traction successes and failures][6], and another post on [finding some SEO success][7].
  * Later architectural changes, including [moving away from Parse.com][8] and [migrating from MongoDB to Elasticsearch][9].

The last of the above posts was published in November 2015 &ndash; almost two years ago. Most of the work on BCRecommender was done up to that point, when my main focus was on part-time contracting while working on my own projects. However, since January 2016 I've mostly been working full-time, so I haven't had the time to give enough attention to the project. Therefore, it looks like it's time for me to say goodbye to BCRecommender.

Despite the lack of attention, about 5,000 people still visit BCRecommender every month (down from a peak of around 9,000). I know that people find it useful, even though it hasn't been functionally updated in a long time (though the recommendations have been refreshed a few times). In an ideal world, BCRecommender would be replaced by algorithmic recommendations from Bandcamp. But unfortunately, Bandcamp still doesn't offer personalised recommendations. This is a shame, because such recommendations could be of great benefit to both artists and fans. Millions of tracks and albums have been published on Bandcamp, meaning that serving personalised recommendations that cover their full catalogue can only be achieved using algorithms. However, it seems like they're not interested in building this kind of functionality.

Rather than simply pulling the plug on BCRecommender, I thought I'd put a call out to see if anyone is interested in maintaining it. I'm happy to open source the code and hand the project over to someone else if it means it would be in good hands. With a little bit of work, BCRecommender can be turned into a full Bandcamp-based personalised radio station. If you think you'd be a good fit for maintaining the project, [drop me a line][10] and we can discuss further. If you just love BCRecommender, you can also let Bandcamp know that you want them to implement algorithmic recommendations (e.g., on [Twitter][11] or by emailing support@bandcamp.com). I'll keep BCRecommender alive for about two more months and see if I get any responses. Either way, I'll be saying goodbye to maintaining it before the end of the year.

 [1]: https://yanirseroussi.com/2014/08/30/building-a-bandcamp-recommender-system-part-1-motivation/
 [2]: https://bandcamp.com/
 [3]: https://yanirseroussi.com/2014/09/07/building-a-recommender-system-on-a-shoestring-budget/
 [4]: https://yanirseroussi.com/2014/09/19/bandcamp-recommendation-and-discovery-algorithms/
 [5]: https://yanirseroussi.com/2014/09/24/applying-the-traction-books-bullseye-framework-to-bcrecommender/
 [6]: https://yanirseroussi.com/2014/11/05/bcrecommender-traction-update/
 [7]: https://yanirseroussi.com/2014/12/15/seo-mostly-about-showing-up/
 [8]: https://yanirseroussi.com/2015/07/31/goodbye-parse-com/
 [9]: https://yanirseroussi.com/2015/11/04/migrating-a-simple-web-application-from-mongodb-to-elasticsearch/
 [10]: https://yanirseroussi.com/about/
 [11]: https://twitter.com/bandcamp
