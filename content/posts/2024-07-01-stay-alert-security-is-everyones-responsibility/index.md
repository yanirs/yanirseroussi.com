---
title: Stay alert! Security is everyone's responsibility
author: Yanir Seroussi
type: post
date: 2024-07-01T02:00:00+00:00
url: /2024/07/01/stay-alert-security-is-everyones-responsibility/
cover:
  relative: true
  image: putting-on-shoes-to-outrun-others.webp
  alt: a man putting on shoes to outrun other people (not the tiger)
summary: Questions to assess the security posture of a startup, focusing on basic hygiene and handling of sensitive data.
tags:
  - security
  - software engineering
  - startups
---
Security. Trust. Compliance.

...

Have I lost you yet?

If you're building a startup, you may find the above words boring and corporate. But security gaps can destroy your business.

While few startups have security experts on the founding team, everyone should have a basic level of security awareness these days.

I'm not a security expert myself, yet I've included a Security & Compliance section in [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/). The questions from this section can't replace a professional audit, as they only prod for common issues. However, it's never a bad time to learn more and improve your security posture. This is the goal of the health check section and this post.

Throughout my career, I've spotted many security issues and have either addressed or escalated them &ndash; despite never having "security" as part of my formal job description. Still, I know I have a lot to learn about security &ndash; especially as the threat landscape keeps shifting.

If you're a founder, you want to [foster a culture](https://yanirseroussi.com/2024/05/20/question-startup-culture-before-accepting-a-data-to-ai-role/) where security issues are escalated and addressed promptly. Otherwise, you may end up with expensive data breaches that can destroy customer trust and your reputation. For example, [the Optus data breach in 2022 occurred because of trivial mistakes](https://www.upguard.com/blog/how-did-the-optus-data-breach-happen). Meanwhile, [Optus Glassdoor reviews](https://www.glassdoor.com.au/Reviews/Optus-Reviews-E9784.htm) highlight serious cultural issues that may have prevented such trivial mistakes from being escalated.

Unfortunately, such examples abound in the corporate world. But your startup can do better.

The rest of this post presents the questions from the Security & Compliance section, along with short explanations. If you think I've missed any critical questions, [please let me know](https://yanirseroussi.com/contact/).

## Basic hygiene for everyone

Any modern human should give an affirmative answer to the first three questions. Unfortunately, [this still isn't the case (as of 2024)](https://bitwarden.com/resources/world-password-day/). Even if you don't run a startup, you [should practise basic hygiene and secure your digital life](https://digital-defense.io/). It's on the same level as brushing your teeth.

> * Q1: Does everyone on the team use a password manager to generate unique long passwords and share credentials?
> * Q2: Does everyone on the team use two-factor authentication on all key accounts?
> * Q3: Is everyone on the team aware of phishing risks, including novel attacks that use AI for impersonation?

## Basic hygiene for system admins

Early in a startup's life, system administration is a hat, not a full-time role. This hat is often worn poorly, e.g., it may _seem_ easier to grant excessive access to speed up execution than keep a tight control on accounts and adhere to the principle of least privilege. However, it's _much_ easier to start with secure admin practices with a handful of people than revoke access and disrupt the workflows of dozens of people later on.

You'd also sleep better at night if the answers to all the following questions imply that you're securing things to the best of your abilities.

> * Q4: Is [the principle of least privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege) enforced on all entities? That is, do human and non-human accounts have only the minimal privileges needed to do their job?
> * Q5: Do you follow [zero trust principles](https://en.wikipedia.org/wiki/Zero_trust_security_model)?
> * Q6: Are all company devices encrypted? Are they kept up to date and protected from common threats like malware?
> * Q7: Is any work done on non-company devices? If so, are they secured as well as company devices?

**Least privilege is key.** Last year, I participated in [a reading group](https://forum.effectivealtruism.org/posts/zxrBi4tzKwq2eNYKm/ea-infosec-skill-up-in-or-make-a-transition-to-infosec-via) of [the book _Building Secure and Reliable Systems_](https://www.google.com/books/edition/Building_Secure_and_Reliable_Systems/Kn7UxwEACAAJ). The moderator &ndash; who has over 10 years of security experience with Google &ndash; referred to the chapter on least privilege as _"the meat and potatoes"_ of the whole book. Ignore at your own risk.

## Basic hygiene for developers

While system administration is an early-stage hat, tech startups typically have developers shipping software as their primary role. Unfortunately, basic security hygiene is frequently overlooked by developers. And even if developers know what they _should_ do, they may cut corners under the pressure of deadlines.

Fortunately, early-stage startups are rarely an interesting target for hackers, so there's time to improve your security posture around these four questions:

> * Q8: Are all API keys stored appropriately (e.g., in a cloud provider's secret store rather than in source code)?
> * Q9: Are developers aware of [the OWASP top ten security risks](https://owasp.org/www-project-top-ten/)?
> * Q10: Do you keep up with vulnerability reports and promptly apply security patches to your product (including updates of third-party dependencies)?
> * Q11: If you're building with large language models, are you aware of the new class of threats they introduce (like [prompt injections](https://simonwillison.net/series/prompt-injection/))? How do you mitigate those risks?

## Confidence in current security posture

When it comes to security, what you don't know _can_ hurt you. Continuous learning on threats and best practices is key. However, it can't replace professional audits and proactive improvement and monitoring of your systems. This is the focus of the next three questions:

> * Q12: Were any security audits done by a third party?
> * Q13: Were there any security incidents? How were they handled?
> * Q14: Do you have the instrumentation in place to be confident that there isn't a breach right now? How confident are you on a scale of 1 to 5?

## Data-specific questions

The best protection from data breaches and compliance issues is to avoid collecting any sensitive data. However, [as business value often comes from proprietary data](https://yanirseroussi.com/2024/06/10/startup-data-health-starts-with-healthy-event-tracking/), this isn't a practical solution. Instead, keep the following questions in mind as you build and run your startup:

> * Q15: Do you handle any sensitive data?
> * Q16: Are you aware of and comply with all relevant legislation around the data you handle and retain?
> * Q17: How do you secure data at rest and in flight?
> * Q18: What systems do you have for mitigating and recovering from data loss? How likely is a catastrophic data loss (e.g., reliant on one person or a single data centre)? How long will it take you to recover?

## Data-to-AI health beyond security & compliance

This post is part of a series on [my Data-to-AI Health Check for Startups](https://yanirseroussi.com/data-to-ai-health-check/). Previous posts:

* [Assessing a startup's data-to-AI health: Overview and motivation](https://yanirseroussi.com/2024/04/22/assessing-a-startups-data-to-ai-health/)
* [Business questions to ask before taking a startup data role](https://yanirseroussi.com/2024/05/06/business-questions-to-ask-before-taking-a-startup-data-role/)
* [Probing the People aspects of an early-stage startup](https://yanirseroussi.com/2024/05/13/probing-the-people-aspects-of-an-early-stage-startup/)
* [Question startup culture before accepting a data-to-AI role](https://yanirseroussi.com/2024/05/20/question-startup-culture-before-accepting-a-data-to-ai-role/)
* [Plumbing, Decisions, and Automation: De-hyping Data & AI](https://yanirseroussi.com/2024/05/27/plumbing-decisions-and-automation-de-hyping-data-and-ai/)
* [How to avoid startups with poor development processes](https://yanirseroussi.com/2024/06/03/how-to-avoid-startups-with-poor-development-processes/)
* [Startup data health starts with healthy event tracking](https://yanirseroussi.com/2024/06/10/startup-data-health-starts-with-healthy-event-tracking/)
* [AI ain't gonna save you from bad data](https://yanirseroussi.com/2024/06/17/ai-aint-gonna-save-you-from-bad-data/)
* [Is your tech stack ready for data-intensive applications?](https://yanirseroussi.com/2024/06/24/is-your-tech-stack-ready-for-data-intensive-applications/)

[You can download a guide containing all the questions as a PDF](https://yanirseroussi.com/data-to-ai-health-check/). As this turned out to be an epic (and fun) project, I may also publish a post on distilling the top questions and running an efficient health check. Feedback is always welcome!
