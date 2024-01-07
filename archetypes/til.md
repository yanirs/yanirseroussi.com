---
title: {{ substr .Name 11 | humanize }}
author: Yanir Seroussi
type: til
date: {{ now.UTC.Format "2006-01-02T15:04:05+00:00" }}
url: /til/{{ replace (substr .Name 0 10) "-" "/" }}/{{ substr .Name 11 }}/
summary: TODO
showBreadcrumbs: true
tags:
  - TODO
---
