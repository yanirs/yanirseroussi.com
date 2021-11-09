---
title: This holiday season, give me real insights
author: Yanir Seroussi
type: post
date: 2015-12-08T06:57:25+00:00
url: /2015/12/08/this-holiday-season-give-me-real-insights/
cover:
  image: dikw-pyramid.jpg
tags:
  - analytics
  - data science
  - Facebook
  - insights
  - LinkedIn
  - marketing
  - WordPress

---
Merriam-Webster defines an <a href="http://www.merriam-webster.com/dictionary/insight" target="_blank" rel="noopener">insight</a> as _an understanding of the true nature of something_. Many companies seem to define an insight as _any piece of data or information_, which I would call a pseudo-insight. This post surveys some examples of pseudo-insights, and discusses how these can be built upon to provide real insights.

## Exhibit A: WordPress stats

This website is hosted on <a href="http://wordpress.com" target="_blank" rel="noopener">wordpress.com</a>. I'm generally happy with WordPress &ndash; though it's not as exciting and shiny as newer competitors, it is rock-solid and very feature-rich. An example of a great WordPress feature is the new stats area (available under <a href="https://wordpress.com/stats" target="_blank" rel="noopener">wordpress.com/stats</a> if you have a WordPress website). This area includes an insights page, which is full of prime examples of pseudo-insights.

At the top of the insights page, there is a visualisation of posting activity. As the image below shows, this isn't very interesting for websites like mine. I already know that I post irregularly, because writing a blog post is time-consuming. I suspect that this visualisation isn't very useful even for more active multi-author blogs, as it is essentially just a different way of displaying the raw data of post dates. Without joining this data with other information, we won't gain a better understanding of how the blog is performing and why it performs the way it does.

{{< figure src="wordpress-insights-posting-activity.png" alt="WordPress insights: posting activity" >}}

An attempt to extract more meaningful insights from posting times appears further down the page, in the form of a widget that tells you the most popular day and hour. The help text says that _This is the day and hour when you have been getting the most Views on average. The best timing for publishing a post may be around this period_. Unfortunately, I'm pretty certain that this isn't true in my case. Monday happens to be the most popular day because that's when I published two of my most popular posts, and I usually try to spread the word about a new post as soon as I publish it. Further, blog posts can become popular a long time after publication, so it is unlikely that the best timing for publishing a post is around Monday 3pm.

{{< figure src="wordpress-insights-popular-time.png" alt="WordPress insights: most popular day and hour" >}}

**What would real WordPress insights look like?** If we stick to idea of exploring the effect of publication timing, I would be curious to know if there is indeed a link between when a post is published and its popularity. Automattic (the company behind WordPress) is in a position to test this, as they can explore data from millions of blogs. My gut feeling is that the time of publication has a negligible effect on popularity. Things that matter much more are a post's title, content, and effective distribution channels. Given the amount of data that they have, Automattic data scientists can definitely explore all of these factors. This would allow them to surface insights that will help authors drive more quality traffic to their websites.

## Exhibit B: Facebook page insights

As anyone who manages a Facebook page probably knows, Facebook provides pretty rich analytics of pages on their platform. For example, you can see the likes you've received over time and how your posts perform, and slice and dice this information in various ways. This is a great feature, but again, calling it <a href="https://www.facebook.com/help/336893449723054/" target="_blank" rel="noopener">insights</a> is a misuse of the word and somewhat of an insult for those of us who work to extract real insights from data. An analytics dashboard is not insights.

{{< figure src="facebook-page-insights.png" alt="Facebook page insights" >}}

**What would real Facebook page insights look like?** Working off the assumption that people manage a Facebook page to reach and engage their audience, real insights would enhance a page administrator's understanding of their audience and improve their ability to engage them and reach new people. However, Facebook is famous for having a conflict of interest here, because they require you to pay to reach more people. For example, if a post you shared is performing better than usual, Facebook will send you a notification, asking you to pay to boost the post further. It would be better if they told you what has caused this post to reach more people, and how to reproduce this success with future posts (for free). But this is very unlikely to happen. In <a href="http://www.cgpgrey.com/blog/the-professional-sharer" target="_blank" rel="noopener">the words of CGP Grey</a>: _professional sharers cannot trust the platforms upon which they stand, audiences cannot trust the platform to show what they asked to see._

## Exhibit C: LinkedIn profile views

<a href="https://help.linkedin.com/app/answers/detail/a_id/42/~/who%E2%80%99s-viewed-your-profile---frequently-asked-questions" target="_blank" rel="noopener">Who's viewed your profile</a> is a popular LinkedIn feature. A key part of this feature is a graph that includes your weekly profile views together with actions taken on LinkedIn. The official LinkedIn blog calls this graph the <a href="http://blog.linkedin.com/2014/10/06/new-ways-to-engage-with-whos-viewed-your-linkedin-profile/" target="_blank" rel="noopener">insights graph</a> and provides some examples for its uses:

> So, for example, if you are trying to attract new clients or business leads, you can see how many potential partners looked at your profile after you joined an important industry group. Or, if you're looking for a new job, you can look at your insights graph to see whether adding a skill to your profile or endorsing a peer gave you a bigger bump in views by recruiters. No matter your goal, you'll be able to see which actions lead to the most relevant profile views &ndash; then start reaching out and closing the sale or applying for your dream job. 

As the examples show, the so-called insights graph merely provides information about past actions and profile views on the LinkedIn platform. It is up to you to come up with the insights, but this may be hard if you consider only the actions taken within the walled garden of LinkedIn. For example, as shown in the following graph, my profile views received a boost on the week starting November 23, which was mostly due to publishing a [popular post on this website][1]. In general, social networks such as LinkedIn, Twitter, and Facebook tend to have a very narrow view of the world &ndash; as if the only interesting things happen on the platform. In reality, most of the action happens off-platform, either within other digital assets or in the physical world. 

{{< figure src="linkedin-profile-views.png" alt="LinkedIn profile views" >}}

**What would real LinkedIn insights look like?** First, I think that the focus on profile views is somewhat misguided. It's not that hard to artificially generate profile views &ndash; simply view other people's profiles. There is no intrinsic value in someone having viewed your profile &ndash; the value comes from a connection that leads to an interesting offer or conversation. Second, LinkedIn is about professional networking that is based on real-world activity. As such, it only forms a small part of the world of professional networking by allowing people to have an online presence that makes them contactable by people they don't already know. When it comes to insights, it'd be useful to know the true causal factors that lead to interesting connections &ndash; much more useful than suggestions such as _add software development as a skill on your profile to get up to 3% more profile views_.

## Summary: Real insights are about the _why_

There are many other examples of pseudo-insights out there. The reason is probably that the field of analytics is becoming increasingly commoditised, and it is easier to rebrand an analytics dashboard as an insights dashboard than to provide real insights. Providing real insights requires moving up the <a href="https://en.wikipedia.org/wiki/DIKW_Pyramid" target="_blank" rel="noopener">DIKW pyramid</a> from data and information to knowledge and wisdom &ndash; from describing the past to learning general lessons that allow you to influence the future. Providing real insights can be very hard, as it often requires inferring the causes of events &ndash; the _why_ that comes after the _what_ and _how_. More on this later &ndash; I have just started reading <a href="http://www.skleinberg.org/why/" target="_blank" rel="noopener">Samantha Kleinberg's Why: A Guide to Finding and Using Causes</a> and will report (hopefully real) insights on causality in future posts.

 [1]: https://yanirseroussi.com/2015/11/23/the-hardest-parts-of-data-science/
