---
title: Making a TIL section with Hugo and PaperMod
author: Yanir Seroussi
type: til
date: 2023-07-17T00:06:15+00:00
url: /til/2023/07/17/making-a-til-section-with-hugo-and-papermod/
summary: How I added a Today I Learned section to my Hugo site with the PaperMod theme.
showBreadcrumbs: true
tags:
  - blogging
  - Hugo
  - web development
---

I started following [Simon Willison](https://simonwillison.net/) as a way of getting informed about practical applications of large language models. It turns out that Simon is also an incredibly prolific blogger and open source contributor, with posts dating back to 2002. He recently gave an interview titled [The Data Enthusiast's Toolkit](https://www.youtube.com/watch?v=zI43eaPc59Q), where he discussed his [Datasette project](https://datasette.io/) and a bit about his approach to writing online. In addition to his main blog, he maintains [a separate TIL subdomain](https://til.simonwillison.net/), where shares things he's learned in quick rough posts.

Most of [my main website posts](https://yanirseroussi.com/) take a while to write, so I post infrequently. I enjoy the process of learning about topics through public writing, as I often start out thinking things are a certain way, and then make new discoveries when I search for references. However, I liked the idea of sharing more through quicker posts, so I decided to add a TIL section to my site.

[I made the switch from WordPress.com to Hugo almost two years ago](https://yanirseroussi.com/2021/11/10/migrating-from-wordpress-com-to-hugo-on-github-cloudflare/) and haven't looked back. I love the extra control that it gives me, though it sometimes requires a bit of tinkering. However, adding a TIL section was a breeze thanks to [a post by Jacob Kaplan-Moss](https://jacobian.org/til/how-to-make-a-til-section/). Since I use the PaperMod theme and my site is set up differently, I followed slightly different steps (links are to [commits in the PR that added the TIL section](https://github.com/yanirs/yanirseroussi.com/pull/7)):

1. [Copied the PaperMod's `archives.html` to `layout/til/list.html`](https://github.com/yanirs/yanirseroussi.com/pull/7/commits/a2eb33e3d9b96e6c3eca1ad9475471e60765b019) to serve as [the base list layout under `/til/`](https://yanirseroussi.com/til/).
2. [Tweaked the new `list.html` to only show posts of type `til`](https://github.com/yanirs/yanirseroussi.com/pull/7/commits/b0859b5b1f5a936d0e73ce98a6b1565cb36b4832), and removed counts and drafts.
3. [Added `content/til/_index.md` with the section's title and description](https://github.com/yanirs/yanirseroussi.com/pull/7/commits/e6ce0aed4bb7bcbbdbe913db0e786447b6497076), which are shown at the top of the list view and in meta tags.
4. [Added my first TIL post](https://github.com/yanirs/yanirseroussi.com/pull/7/commits/3841a1009f3749a208b1a53200fb0484951f2ca8) with [a lovely quote from _How to Speak Whale_](https://yanirseroussi.com/til/2023/07/11/you-cant-save-time/).

Unlike Jacob, I don't mind TIL posts showing up in the main RSS feed. It's enough for me that they don't show up on the main page, which didn't require any configuration tweaks in my case.

When I push changes to the website, I like checking the `gh-pages` branch to see what got deployed. Recently [I added an additional `gh-pages-unminified` branch](https://github.com/yanirs/yanirseroussi.com/commit/485a4e9960d513ad53a06774ba01daae349b409c) to produce a more human-friendly diff. You can see the human-friendly result of merging the PR that added the TIL section [here](https://github.com/yanirs/yanirseroussi.com/commit/ed3a7ab3df061c2ddce95ff3803674ee67941e06).

That's it for now. If I post TILs consistently, I will probably link to it from the top-level menu and tweak the `/til/` page to also show posts by tag. For now, I like the idea of a quiet low-effort place to post publicly. 
