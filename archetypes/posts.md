---
title: {{ substr .Name 11 | humanize }}
author: Yanir Seroussi
type: post
date: {{ substr .Name 0 10 }}T00:00:00+00:00
url: /{{ replace (substr .Name 0 10) "-" "/" }}/{{ substr .Name 11 }}/
cover:
  relative: true
  image: TODO
  alt: TODO
summary: TODO
tags:
  - TODO
---
