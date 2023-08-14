---
title: Email notifications on public GitHub commits
author: Yanir Seroussi
type: til
date: 2023-08-14T05:15:00+00:00
url: /til/2023/08/14/email-notifications-on-public-github-commits/
summary: GitHub publishes an Atom feed, which means you can use any RSS reader to follow commits.
showBreadcrumbs: true
tags:
  - productivity
  - Reef Life Survey
---

I have a daily data processing workflow that runs as a GitHub Actions cron job on [the `rls-data` repository](https://github.com/yanirs/rls-data/). The workflow turns some public [Reef Life Survey](https://reeflifesurvey.com/) data into JSONs that are used by tools on the Reef Life Survey website. Given that the repository is public, running the workflow is free.

When I first implemented the workflow, it was running once a week, so I used GitHub's settings to get notified every time _any_ Actions workflow ran. This included successful runs, which wasn't too noisy. However, I received many other emails due to Actions that ran on other projects I was working on.

It was on my list to figure out a better way, but I only got around to it when I increased the flow's frequency to daily. I still wanted to receive an email if the flow failed or made changes to the output JSONs, but there was no need for an email if it ran successfully without committing any changes.

While GitHub supports getting emails on new pull requests by watching a repository, it doesn't appear to support subscribing to commits. Fortunately, [Stack Overflow has the answer for watching commits](https://stackoverflow.com/questions/9845655/how-do-i-get-notifications-for-commits-to-a-github-repository): Use the built-in RSS feed by appending `/commits/<branch>.atom` to the repository's URL. In `rls-data`'s case, it is [https://github.com/yanirs/rls-data/commits/master.atom](https://github.com/yanirs/rls-data/commits/master.atom), which I turned to emails using [Blogtrottr](https://blogtrottr.com/).

Problem solved! Now I only get emails on commits via Blogtrottr, along with emails on workflow failures directly from GitHub. 
