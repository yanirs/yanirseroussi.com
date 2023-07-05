---
title: Building a Bandcamp recommender system (part 1 – motivation)
author: Yanir Seroussi
type: post
date: 2014-08-30T08:11:38+00:00
url: /2014/08/30/building-a-bandcamp-recommender-system-part-1-motivation/
cover:
  image: bcrecommender-screenshot.png
summary: My motivation behind building BCRecommender, a free recommendation & discovery service for Bandcamp music. 
tags:
  - Bandcamp
  - BCRecommender
  - music
  - music industry
  - recommender systems

---
I've been a <a href="http://bandcamp.com" target="_blank" rel="noopener">Bandcamp</a> user for a few years now. I love the fact that they pay out a <a href="https://bandcamp.com/pricing" target="_blank" rel="noopener">significant share of the revenue</a> directly to the artists, unlike <a href="https://en.wikipedia.org/wiki/Spotify#Criticism" target="_blank" rel="noopener">other services</a>. In addition, despite the fact that fans may stream all the music for free and even <a href="https://bandcamp.com/help/audio_basics#steal" target="_blank" rel="noopener">easily rip it</a>, almost $80M were paid out to artists through Bandcamp to date (including almost $3M in the last month) &ndash; serving as strong evidence that the traditional music industry's fight against piracy is a waste of resources and time.

One thing I've been struggling with since starting to use Bandcamp is the discovery of new music. Originally (in 2011), I used the <a href="https://bandcamp.com/tags" target="_blank" rel="noopener">browse-by-tag</a> feature, but it is often too broad to find music that I like. A newer feature is the <a href="https://bandcamp.com/discover" target="_blank" rel="noopener">Discoverinator</a>, which is meant to emulate the experience of <a href="http://blog.bandcamp.com/2012/06/07/behold-the-glory-of-the-discoverinator/" target="_blank" rel="noopener">browsing through covers at a record store</a> &ndash; sadly, I could never find much stuff I liked using that method. Last year, Bandcamp announced <a href="http://blog.bandcamp.com/2013/01/10/bandcamp-for-fans/" target="_blank" rel="noopener">Bandcamp for fans</a>, which includes the ability to wishlist items and discover new music by stalking/following other fans. In addition, they released a <a href="http://blog.bandcamp.com/2013/10/25/its-over/" target="_blank" rel="noopener">mobile app</a>, which made the music purchased on Bandcamp much easier to access.

All these new features definitely increased my engagement and helped me find more stuff to listen to, but I still feel that Bandcamp music discovery could be much better. Specifically, I would love to be served personalised recommendations and be able to browse music that is similar to specific tracks and albums that I like. Rather than waiting for Bandcamp to implement these features, I decided to do it myself. Visit <a href="http://www.bcrecommender.com" target="_blank" rel="noopener">BCRecommender &ndash; Bandcamp recommendations based on your fan account</a> to see where this effort stands at the moment.

While BCRecommender has already helped me discover new music to add to <a href="https://bandcamp.com/yanir" target="_blank" rel="noopener">my collection</a>, building it gave me many more ideas on how it can be improved, so it's definitely a work in progress. I'll probably tinker with the underlying algorithms as I go, so recommendations may occasionally seem weird (but this always seems to be the case with recommender systems in the real world). In subsequent posts I'll discuss some of the technical details and where I'd like to take this project.

<small><br /> It's probably worth noting that BCRecommender is not associated with or endorsed by Bandcamp, but I doubt they would mind since it was built using publicly-available information, and is full of links to buy the music back on their site.<br /> </small>
