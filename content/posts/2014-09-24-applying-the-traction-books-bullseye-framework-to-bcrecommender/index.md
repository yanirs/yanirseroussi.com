---
title: Applying the Traction Book’s Bullseye framework to BCRecommender
author: Yanir Seroussi
type: post
date: 2014-09-24T04:57:39+00:00
url: /2014/09/24/applying-the-traction-books-bullseye-framework-to-bcrecommender/
tags:
  - Bandcamp
  - BCRecommender
  - business
  - marketing
  - recommender systems
  - traction book

---
<p class="intro-note">
This is the fourth part of a series of posts on my <a href="http://www.bcrecommender.com" target="_blank" rel="noopener">Bandcamp recommendations (BCRecommender)</a> project. Check out previous posts on <a href="https://yanirseroussi.com/2014/08/30/building-a-bandcamp-recommender-system-part-1-motivation/">the general motivation behind this project</a>, <a href="https://yanirseroussi.com/2014/09/07/building-a-recommender-system-on-a-shoestring-budget/">the system's architecture</a>, and <a href="https://yanirseroussi.com/2014/09/19/bandcamp-recommendation-and-discovery-algorithms/">the recommendation algorithms</a>.
</p>

Having used BCRecommender to find music I like, I'm certain that other Bandcamp fans would like it too. It could probably be extended to attract a wider audience of music lovers, but for now, just getting feedback from Bandcamp fans would be enough. There are about 200,000 fans that I know of – getting even a fraction of them to use and comment on BCRecommender would serve as a good guide to what's worth building and improving.

In addition to getting feedback, the personal value for me in getting BCRecommender users is learning some general lessons on traction building. Like many technical people, I like building products and playing with data, but I don't really enjoy sales and marketing (and that's an understatement). One of my goals in working independently is forcing myself to get better at the things I'm not good at. To that end, I recently started reading <a href="http://tractionbook.com/" target="_blank" rel="noopener">Traction: A Startup Guide to Getting Customers</a> by Gabriel Weinberg and Justin Mares.

The Traction book identifies 19 different channels for getting traction, and suggests a simple framework (named Bullseye) to ranking and quickly exploring the channels. They explain that many technical founders tend to focus on traction channels they're familiar with, and that the effort invested in those channels tends to be rather small compared to the investment in building the product. The authors rightly note that "Almost every failed startup has a product. What failed startups don't have is traction – real customer growth." They argue that following a rigorous approach to gaining traction via their framework is likely to improve a startup's chances of success. From personal experience, this is very likely to be true.

The key steps in the Bullseye framework are brainstorming ideas for each traction channel, ranking the channels into tiers, prioritising the most promising ones, testing them, and focusing on the channels that work. This is not a one-off process – channel suitability changes over time, and one needs to go through the process repeatedly as the product evolves and traction grows.

Here are the traction channels, ordered in the same order as in the book. Each traction channel is marked with a letter denoting its ranking tier from A (most appropriate) to C (unsuitable right now). A short explanation is provided for each channel.

  * [B] **viral marketing:** everyone wants to go viral, but at the moment I don't have a good-enough understanding of my target audience to seriously pursue this channel. 
  * [C] **public relations (PR):** I don't think that PR would give me access to the kind of focused user group I need at this phase. 
  * [C] **unconventional PR:** same as conventional PR. 
  * [C] **search engine marketing (SEM):** may work, but I don't want to spend money at this stage. 
  * [C] **social and display ads:** see SEM. 
  * [C] **offline ads:** see SEM. 
  * [A] **search engine optimization (SEO):** this channel seems promising, as ranking highly for queries such as "bandcamp recommendations" should drive quality traffic that is likely to convert (i.e., play recommendations and sign up for updates). It doesn't seem like "bandcamp recommendations" is a very competitive query, so it's definitely worth doing some SEO work. 
  * [A] **content marketing:** I think that there's definitely potential in this channel, since I have a lot of data that can be explored and presented in interesting ways. The problem is creating content that is compelling enough to attract people. I started playing with this channel via the <a href="http://www.bcrecommender.com/spotlights" target="_blank" rel="noopener">Spotlights feature</a>, but it's not good enough yet. 
  * [B] **email marketing:** BCRecommender already has the subscription feature for retention. At this stage, this doesn't seem like a viable acquisition channel. 
  * [B] **engineering as marketing:** this channel sounds promising, but I don't have good ideas for it at the moment. This may change soon, as I'm currently reading this chapter. 
  * [A] **targeting blogs:** this approach should work for getting high-quality feedback, and help SEO as well. 
  * [C] **business development:** there may be some promising ideas in this channel, but only worth pursuing later. 
  * [C] **sales:** not much to sell. 
  * [C] **affiliate programs:** I'm not going to pay affiliates as I'm not making any money. 
  * [B] **existing platforms:** in a way, I'm already building on top of the existing Bandcamp platform. One way of utilising it for growth is by getting fans to link to BCRecommender when it leads to sales (<a href="https://bandcamp.com/yanir" target="_blank" rel="noopener">as I've done on my fan page</a>), but that would be more feasible at a later stage with more active users. 
  * [C] **trade shows:** I find it hard to think of trade shows where there are many Bandcamp fans. 
  * [C] **offline events:** probably easier than trade shows (think concerts/indie events), but doesn't seem worth pursuing at this stage. 
  * [C] **speaking engagements:** similar to offline events. I do speaking engagements, and I'm actually going to mention BCRecommender as a case study at <a href="https://generalassemb.ly/education/demystifying-data-an-introduction-to-data-science/sydney/7692" target="_blank" rel="noopener">my workshop this week</a>, but the intersection between Bandcamp fans and people interested in data science seems rather small. 
  * [C] **community building:** this may be possible later on, when there is a core group of loyal users. However, some aspects of community building are provided by Bandcamp and I don't want to compete with them. 

Cool, writing everything up explicitly was actually helpful! The next step is to test the three channels that ranked the highest: SEO, content marketing and targeting blogs. I will report the results in future posts.
