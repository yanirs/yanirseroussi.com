---
title: "Analysis strategies in online A/B experiments: Intention-to-treat, per-protocol, and other lessons from clinical trials"
author: Yanir Seroussi
type: post
date: 2022-01-14T00:05:40+00:00
url: /2022/01/14/analysis-strategies-in-online-a-b-experiments/
cover:
  relative: true
  image: online-drug-experiment.jpg
summary: Epidemiologists analyse clinical trials to estimate the intention-to-treat and per-protocol effects. This post applies their strategies to online experiments.
tags:
  - causal inference
  - data science
  - marketing
  - split testing
  - statistics

---

{{< blockquote author="Benjamin Brewster" >}}
  In theory, there is no difference between theory and practice. In practice, there is.
{{< /blockquote >}}

Many discussions of online A/B experiments deal with the sunny day scenario: You randomly assign users to groups A and B, expose group A to the control variant and group B to the treatment variant, run statistical tests on your chosen metrics, and assume that metric differences between the groups that aren't explained by randomness are due to exposure to the treatment.

However, it's not always a sunny day for the online experimenter. Challenges include dealing with bot traffic and malicious users, and implementation realities that may make users experience both variants or neither of them. While many of these problems have parallels in clinical trials, I haven't found many resources that explore these parallels. In this post, I share some lessons I learned from the rich clinical trial literature while building [Automattic's experimentation platform](https://data.blog/category/experimentation-platform/), focusing on analysis strategies that deal with deviations from the ideal experiment scenario. 

## Reminder: Why we run A/B experiments

{{< figure src="uncontrolled-versus-controlled-experiment.svg" caption="Uncontrolled versus controlled experiment" >}}

While the practice of running online A/B experiments is now commonplace, it's worth reflecting on why such experiments work. Why can't we just roll out any treatments we think of, measure the metric changes, and assume that differences beyond what we expect from random variation are due to the genius (or folly) of our implemented treatments?

Well, it's not that simple because the world isn't static. Even if we don't make any changes, [we're likely to see different outcomes from month to month and day to day](https://www.linkedin.com/pulse/how-identify-your-marketing-lies-start-telling-truth-tiberio-caetano/), as the world and our user population change. This is represented by the top part of the diagram above: While we're interested in the causal impact of the `Treatment` on the `Outcome`, many `Unknowns` may affect both. That is, without an A/B experiment, the `Unknowns` act as confounders that make it impossible to estimate the causal effect without [further assumptions](https://yanirseroussi.com/2016/05/15/diving-deeper-into-causality-pearl-kleinberg-hill-and-untested-assumptions/).

With an ideal A/B experiment, we make exposure to the `Treatment` depend only on our randomisation mechanism &ndash; the `Assigner` on the bottom part of the diagram. Assuming everything goes to plan, we end up with two distinct groups for which exposure to the `Treatment` is only due to our randomisation mechanism. This allows us to conclude that any differences in the `Outcome` across the groups beyond what's expected from randomness are due to the `Treatment`.

However, reality is often different from this ideal scenario.    

## Running example

To make things more concrete, let's take a simple example: You run a crypto exchange, and you want to maximise signups from one of your landing pages. The current call-to-action text is _"sign up"_. You're wondering whether changing it to _"sign up today!"_ would instill a sense of urgency and increase the signup conversion rate (signups divided by unique visitors).

<figure>
  <a class="comment-button" href="#" onclick="alert('This is variant A: control')" style="float: unset">sign up</a>
  <small>OR</small>
  <a class="comment-button" href="#" onclick="alert('This is variant B: treatment')" style="float: unset">sign up today!</a>

  <figcaption>
    <p>A simplified mockup of the variants. Which one would you choose?</p>
  </figcaption>
</figure>

Placing this scenario into the above diagram, if we were to simply change the text, i.e., apply the `Treatment` to everyone, we wouldn't be able to confidently tell whether the text change was the _cause_ of any observed difference in the conversion rate. For example, if our release coincided with a surge of interest in cryptocurrency, this surge may be one of the `Unknowns` that would cause more motivated users to come to our exchange and sign up. That is, the surge would affect both exposure to the `Treatment` and the `Outcome`.

When we run an ideal A/B experiment, we don't have this problem. Factors like a surge of interest in crypto don't affect the assignment of users to the control group A (_"sign up"_) and the treatment group B (_"sign up today!"_). We can compare the conversion rates across the groups, estimate random variability with [our favourite A/B testing calculator](https://yanirseroussi.com/2016/06/19/making-bayesian-ab-testing-more-accessible/), and rejoice. Right?

Well, not so fast...

## Problems, problems...

In the ideal scenario, all the users that were assigned to one of the experiment groups experience their assigned variant and produce a measurable outcome. In our running example, the groups are `A: control` and `B: treatment` with a simple exposure of seeing _"sign up"_ for the former and _"sign up today!"_ for the latter. The outcome is a successful signup or an absence of a signup. To make the outcome well-defined, it's often a good idea to limit outcome measurement to events that happen (or don't happen) within a reasonable _attribution window_ from exposure or assignment. In our example, a reasonable attribution window is probably on the order of hours, as we don't expect the call-to-action text to have long-lasting effects.

Potential deviations from the ideal scenario include:

* **Assignment of ineligible users.** In our running example, these may be bots or users that already have an account. If we include many ineligible users in our analysis, we may underestimate the effect size even if their distribution across groups is uniform.
* **Crossovers.** These are users that manage to experience both variants. For example, they may come across our site on mobile with the _"sign up today!"_ text, and then switch to desktop and see the _"sign up"_ message. Depending on the instrumentation we have in place, we may not be able to detect such users, or we may only detect them if they sign up on one device and then log in on the other device.
* **Assignment without exposure.** Due to implementation constraints, we may not be guaranteed that assigned users are actually exposed to the treatment and control. In our running example, it may be that the assignment is done on the backend while exposure happens conditionally and asynchronously on the frontend &ndash; some users may bounce in the gap between assignment and exposure, and never see the call-to-action text.
* **Multiple exposures.** Once a user has been assigned, they may get exposed to the treatment and control multiple times (without crossing over). In our example, they may visit the landing page repeatedly and see the _"sign up"_ or _"sign up today!"_ text multiple times before deciding to sign up. 

## Epidemiologist jargon and analysis strategies

While clinical trials are more tightly controlled than online A/B experiments, they are also susceptible to problems like assignment of ineligible patients and non-adherence to treatment (e.g., crossover, non-exposure, and multiple exposures). Hence, much has been written on addressing these problems at the analysis stage. However, when researching the topic, overcoming the domain-specific language barrier was a bit of a challenge, as the terminology used by online experimenters is different from the terminology used by epidemiologists. Fortunately, I came across the term _intention-to-treat_ at some point, which opened the door to decades of research on the topic.

Two papers I found useful are [_Intention-to-treat concept: A review_](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3159210/) (Gupta, 2011) and [_Guidelines for estimating causal effects in pragmatic randomized trials_](https://arxiv.org/abs/1911.06030) (Murray, Swanson, and Hernán, 2019). Seeing [Miguel Hernán](https://www.hsph.harvard.edu/miguel-hernan/) on the author list was an especially positive signal for me, as he is responsible for [some of my favourite resources on causal inference](https://yanirseroussi.com/causal-inference-resources/), including [the most practical book I've read on the topic](https://yanirseroussi.com/2018/12/24/the-most-practical-causal-inference-book-ive-read-is-still-a-draft/).

The definitions and guidelines from these two papers provide a solid foundation for thinking about problems of ineligibility and non-adherence. Specifically, Gupta defines intention-to-treat as an analysis strategy _"that includes all randomized patients in the groups to which they were randomly assigned, regardless of their adherence with the entry criteria, regardless of the treatment they actually received, and regardless of subsequent withdrawal from treatment or deviation from the protocol."_

There are often good reasons to exclude some randomised participants from analysis. Depending on the exclusions, this may or may not bias the results. The use of conservative exclusions can be described as modified intention-to-treat, which according to Gupta _"allows the exclusion of some randomized subjects in a justified way (such as patients who were deemed ineligible after randomization or certain patients who never started treatment). However, the definition given to the modified ITT (mITT) in randomized controlled trials has been found to be irregular and arbitrary because there is a lack of consistent guidelines for its application. The mITT analysis allows a subjective approach in entry criteria, which may lead to confusion, inaccurate results and bias."_

Exclusions and further adjustments are usually an attempt to estimate the per-protocol effect, which is defined by Murray, Swanson, and Hernán as _"the effect of receiving the assigned treatment strategies throughout the follow-up as specified in the study protocol."_ Unfortunately, obtaining a valid estimate of the per-protocol effect isn't trivial: _"To validly estimate the per-protocol effect, baseline variables which predict adherence and are prognostic for the outcome need to be accounted for, either through direct adjustment or via an instrumental variable analysis. Yet two commonly used analytic approaches do not incorporate any such adjustment: (1) Naïve per-protocol analysis, that is, restricting the analytic subset to adherent individuals; and (2) As-treated analysis, that is, comparing individuals based on the treatment they choose."_ In other words, if we're not careful, the per-protocol analysis may become analogous to an uncontrolled experiment, as depicted at the top of the diagram above.

## What should be done in practice?

From my reading of the clinical trial literature, the tendency is to use multiple analysis strategies. For example, the first guideline noted by Murray, Swanson, and Hernán is: _"To adequately guide decision making by all stakeholders, report estimates of both the intention-to-treat effect and the per-protocol effect, as well as methods and key conditions underlying the estimation procedures."_ This echoes [the 1988 US FDA guidelines](https://www.fda.gov/regulatory-information/search-fda-guidance-documents/format-and-content-clinical-and-statistical-sections-application) that require applicants to provide an intention-to-treat analysis in addition to the applicant's preferred per-protocol analyses. Similarly, [the 1998 European Medicines Agency guidelines](https://www.ema.europa.eu/en/documents/scientific-guideline/ich-e-9-statistical-principles-clinical-trials-step-5_en.pdf) provide more details on the intention-to-treat, modified intention-to-treat, and per-protocol strategies, stating that: _"In general, it is advantageous to demonstrate a lack of sensitivity of the principal trial results to alternative choices of the set of subjects analysed. [...] When the full analysis set and the per protocol set lead to essentially the same conclusions, confidence in the trial results is increased, bearing in mind, however, that the need to exclude a substantial proportion of subjects from the per protocol analysis throws some doubt on the overall validity of the trial."_

While the stakes in online experiments are typically much lower than in human drug approval, I believe that applying multiple analysis strategies is still a great idea. We did that for Automattic's experimentation platform, where we flagged discrepancies between the strategies if they led to conflicting conclusions. One downside of this approach is that it complicates the presentation of results in comparison to using a single strategy. If you face the same challenge, you may draw inspiration from seeing how it's addressed by the [open source frontend of Automattic's experimentation platform](https://github.com/Automattic/abacus).

Going back to our running example, we can perform the following analyses to deal with the deviations noted above:

* **Intention-to-treat.** Includes all users based on their initial group assignment, regardless of what variant they were exposed to.
* **Modified intention-to-treat: No ineligible users.** This applies to cases where we detect the ineligibility after assignment, but the eligibility criteria are based on factors that could have been known before the experiment. Hence, it _should_ be safe to exclude the ineligible users after the fact. In our example, excluding bots and existing users should increase the observed effect size, but not change the preferred variant.
* **Modified intention-to-treat: No crossovers.** If we have a mechanism to detect _some_ crossovers, excluding them and comparing the results to the intention-to-treat analysis may uncover implementation bugs. It's worth noting that crossovers shouldn't occur in cases where we can uniquely identify users at all stages of the experiment &ndash; it is a problem that is more likely to occur when dealing with anonymous users, as in our landing page example. As such, and given the inability to detect all crossovers, A/B experiments should be avoided when users are highly motivated to cross over. For example, displaying different price levels based on anonymous and transient identifiers like cookies is often a bad idea.
* **Naive per-protocol: Exposed users.** For this analysis, we'd only include users that were exposed to the control and treatment texts. As noted by Murray, Swanson, and Hernán, this is naive because we _should_ adjust our estimates based on variables that predict exposure. However, if missing exposures are only due to the inherent limitations of online experiments, this falls more under the modified intention-to-treat criterion noted by Gupta, of excluding _"patients who never started treatment"_. Things get more complicated if we wish to use each exposure as a distinct starting point for measuring multiple assignment windows (the _multiple exposures_ scenario above), which is akin to patients choosing their own dosage &ndash; far from a controlled experiment. For automated analysis, it's better to use the first exposure as the attribution window start, as it should be unaffected by the experiment variants.

For all analysis approaches, it's critical to verify that there is no _sample ratio mismatch_ in the analysed population, i.e., that the distribution of users across variants matches what we expect from a random assignment. If this isn't the case, manual analysis by a qualified data scientist is needed. The result of this manual analysis may be that the results should be discarded, as sample ratio mismatches are a common indicator of implementation bugs. This is discussed in detail in the book [_Trustworthy Online Controlled Experiments_](https://experimentguide.com/), which also includes a chapter on exposure-based analysis (called _triggering_ in the book). Among other recommendations, the authors suggest analysing the _unexposed_ users. If everything goes as expected, metrics for the assigned-but-unexposed populations would behave like A/A experiment metrics, i.e., any differences between the groups should be due to random variability.

Having rigorous consistency checks in place and falling back to manual analysis when any discrepancies are detected should help avoid the pitfalls of unsafe user exclusions that'd bias the results. Given the need for careful adjustments to get a valid per-protocol estimate in case anything goes wrong, it is often best to fix any underlying issues and rerun the experiment. Usually, this is much cheaper to do in an online setting than in clinical trials.

## Closing thoughts and further reading

Once you move from the theory of experimentation to the practice of running experiments in the real world, you discover the many complexities involved in doing it well. This applies whether you're an epidemiologist or an online experimenter. As noted in the preface to the trustworthy experiments book: _"Getting numbers is easy; getting numbers you can trust is hard!"_

This post only scratched the surface of one area of experimentation: Deciding what population to analyse once the experiment was run. There is, of course, a lot more to online experimentation and causal inference than what I could cover here. But I hope that this message is clear: **Approach experimentation with humility, and aim to learn from a broad set of teachers rather than limit yourself to the relatively-recent developments in online experiments.**

As mentioned above, some resources that are worth reading to learn more include [my favourite causal inference book](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/), [the trustworthy experiments book](https://experimentguide.com/), and [the guidelines for pragmatic trials](https://arxiv.org/abs/1911.06030). There are also a bunch of resources on [my causal inference list](https://yanirseroussi.com/causal-inference-resources/), and [my post on Bayesian A/B testing](https://yanirseroussi.com/2016/06/19/making-bayesian-ab-testing-more-accessible/) should be of interest if you made it to this point. Finally, I'm always happy to discuss these topics, so feel free to [contact me](https://yanirseroussi.com/about/) or leave a comment with your thoughts.

---

<small>Cover image by [Tumisu from Pixabay](https://pixabay.com/photos/online-pharmacy-pills-click-3962209/)</small>
