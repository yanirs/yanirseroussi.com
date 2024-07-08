---
title: Exploring an AI product idea with the latest ChatGPT, Claude, and Gemini
author: Yanir Seroussi
type: post
date: 2024-07-08T02:45:00+00:00
url: /2024/07/08/exploring-an-ai-product-idea-with-the-latest-chatgpt-claude-and-gemini/
cover:
  relative: true
  image: chatbot-arena-leaderboard-2024-07-08.webp
  alt: screenshot of the top of ChatBot Arena leaderboard, showing GPT-4o, Claude 3.5 Sonnet, and Gemini 1.5 
summary: Asking identical questions about my MagicGrantMaker idea yielded near-identical responses from the top chatbot models. 
tags:
  - artificial intelligence
  - business
  - productivity
  - startups
---
With the hype around new AI models and tools, I often feel like I'm missing out on something amazing. For example, the excitement around Claude 3.5 Sonnet has been especially notable, despite it being ranked below ChatGPT-4o on [the LMSYS Chatbot Arena Leaderboard](https://chat.lmsys.org/?leaderboard).

The best way to get a feel for a model is to play with it yourself (though [you'd need more than that to take language models to production](https://yanirseroussi.com/2024/04/15/ai-does-not-obviate-the-need-for-testing-and-observability/)). To this end, I had near-identical chats with Claude 3.5 Sonnet, ChatGPT-4o, and Gemini 1.5 Pro.

**My conclusion:** The leaderboard and benchmarks don't lie, the top three models _feel_ about the same (but your mileage will vary by task and prompt).

As [I've recently opined on LinkedIn](https://www.linkedin.com/posts/yanirseroussi_anthropic-build-with-claude-to-win-10k-activity-7213670215367184384-5hBB), it seems likely that the top models will keep improving but remain roughly equivalent. In the long term, the real competition is around deriving business value from the models, which comes down to building products and distribution.

Commercialisation is an area where players like Google have a massive advantage. For example, Google is running a competition for Gemini applications where the rewards include over $1M in cash and an electric DeLorean. Meanwhile, Anthropic is running a competition for Claude applications where the reward is $10k in Claude API credits. The difference is stark.

Google's competition made me consider MagicGrantMaker &ndash; an AI product idea that could rely on Gemini. In short, it's about helping niche organisations find and apply for grants. This has been on my mind recently, as I've had discussions with Reef Life Survey around collaboration on AI grants to support [automation of aspects of their marine biodiversity monitoring](https://yanirseroussi.com/2024/04/01/artificial-intelligence-automation-and-the-art-of-counting-fish/). However, I haven't had much time to find suitable grants.

My primary chatbot is ChatGPT-4o. Assessing the viability of MagicGrantMaker was a good opportunity to take the latest Claude and Gemini for a spin. 

The rest of this post presents the MagicGrantMaker idea, along with a comparison of highlights from the chat transcripts.

## Setting the scene

I like starting chats by ensuring that the chatbot and I are on the same page when it comes to background knowledge:

> **YS:** Hey, have you heard of Reef Life Survey?

Unsurprisingly, the three bots gave near-identical answers. Here are the first two sentences from each response:

> **ChatGPT:** Yes, I'm familiar with the Reef Life Survey (RLS). It's a global marine biodiversity monitoring program that enlists the help of trained volunteer divers to collect data on reef species and habitats. [...]

> **Claude:** Yes, I have heard of Reef Life Survey. It's an international program that involves trained volunteer divers collecting data on marine life and habitats in coastal areas around the world. [...]

> **Gemini:** Yes, I have heard of Reef Life Survey (RLS). It is a world-renowned marine monitoring program that uses trained recreational SCUBA divers to collect data on reef fish, invertebrates, and habitats. [...]

They all kept going with extra details, and ended their response with a suggestion to provide more information.

## The product idea

Once the scene was set, I hit the bots with the big idea. I sent the three the following message:

> **YS:** I'm deeply familiar with the organisation, as I'm an RLS volunteer.
>
> What I'm after today is this: I have an idea for a web app that'd help organisations like RLS find grant opportunities and apply for them. As it relies on recent improvements in LLMs / AI (specifically text summarisation and generation), I call it MagicGrantMaker (MGM).
>
> The main value proposition for RLS is that it'd:
>
> 1. Surface new grant opportunities
> 2. Draft grant applications
>
> That is, it'd save them time and help them increase their funding.
>
> One key strength of MGM is in its focus on a specific niche for the MVP (Australian marine ecology researchers). Beyond the MVP, the idea is to keep finding under-served niches and deliver an exceptional experience to *specific* grant seekers.
>
> The second niche would be Australian renewable energy startups that may be able to get funding from the likes of ARENA.
>
> The third niche may be startups like MGM itself: supporters of climate tech and nature conservation.
>
> If this proves to be a viable product beyond a prototype, it'd follow a freemium model:
>
> * Free: Search for grants using keywords and a natural language interface
> * Paid tier 1: Create an organisation profile (much of it can be scaffolded automatically from websites and LinkedIn), and get personalised grant opportunities emailed to you.
> * Paid tier 2: Draft grant applications based on your org profile with AI.
>
> Viability would depend on data quality, coupled with the quality of the AI implementation. Then it's all up to effective marketing. The idea is that if the search works well (again, depends on getting a unique dataset), then the free part would be valuable enough to lure people in.
>
> I haven't spoken to any potential customers yet. The next step is finding grant sources to assess the viability of the search engine for the initial niche.
>
> What do you think? Please be brutally honest.

Despite my request for the bots to be brutally honest, they still felt too gentle. What I found most interesting is that they all followed the same response structure: intro, strengths, weaknesses, next steps, and conclusion. Given the length of my prompt, I expected more divergence.

For brevity, I'll summarise their key points rather than provide the full transcripts.

**Strengths:**
- **[All three]** Niche focus
- **[All three]** Freemium model
- **[ChatGPT & Claude]** Scalability
- **[ChatGPT]** Value proposition
- **[Claude]** Time-saving potential
- **[Gemini]** Addresses a real pain point
- **[Gemini]** Leverages AI effectively

**Challenges:**
- **[All three]** Data quality and access
- **[All three]** Competition
- **[All three]** AI limitations
- **[ChatGPT & Gemini]** Marketing and user acquisition
- **[ChatGPT]** Customer validation
- **[Claude]** Customer adoption
- **[Claude]** Regulatory compliance
- **[Claude]** Pricing strategy
- **[Gemini]** Freemium conversion

**Next steps:**
- **[ChatGPT]** (1) customer interviews, (2) prototype development, (3) data partnerships, (4) AI and UX testing, (5) marketing plan.
- **[Claude]** (1) market research, (2) grant source assessment, (3) MVP development, (4) legal considerations.
- **[Gemini]** (1) data validation, (2) prototype and testing, (3) competitive analysis, (4) talk to potential customers.

Apart from Claude being a bit too concerned about legal issues, the outputs are essentially the same. I suppose it's not too surprising: The current generation of general-purpose chatbots excel at surfacing generic advice. Often, generic advice is all you need. And as with coaching, it's the coachee who needs to do most of the work.

## Grant sources

My main motivation for the chat was to surface data sources and assess how hard it'd be to collect the required data. I proceeded to ask about:
- Grant sources for RLS
- Grant sources for applying AI to RLS work
- Grant sources for Australian renewable energy startups

As with the beginning of the chats, all three recommended pretty much the same funding bodies. No surprises there!

One thing I found interesting was the number of potential grant sources, which was in the dozens. These were all valid &ndash; I was either already familiar with them, or verified that they had funded RLS's work before.

The number and diversity of grant sources has supported my suspicion that keeping on top of grants is a non-trivial problem. In fact, I found a potential grant to apply for as part of this work. However, this isn't enough evidence that MagicGrantMaker is a viable business idea &ndash; I'd need to talk with potential customers if I were to pursue it. Still, given the existence of similar companies in the space (e.g., a couple of startups are helping American companies get climate tech grants), I do believe that with the right niches and execution, MagicGrantMaker could be a thing.

## Conclusion

Paraphrasing [the words of an OpenAI engineer](https://nonint.com/2023/06/10/the-it-in-ai-models-is-the-dataset/): _"AI model behaviour is determined by your dataset, nothing else"_. Therefore, it is somewhat unsurprising to see ChatGPT, Claude, and Gemini converging to near-identical outputs. The main dataset is the open web, but a lot of additional proprietary data comes from [fine-tuning the base models on human feedback](https://huyenchip.com/2023/05/02/rlhf.html) (the part that turns auto-complete language models into friendly chatbots).

You'd expect the proprietary data to make a difference, but companies like Anthropic and OpenAI source at least some of their proprietary data from the same providers (like [Scale](https://scale.com/)). The fact that all models compete on beating the same benchmarks also contributes to their sameness.

While my comparative analysis is anecdotal, it has helped reaffirm my suspicion that when it comes to the top general-purpose models, it's fine to just choose one with a convenient UI and tooling. I believe that we'll keep seeing advancements, but that the top players will keep catching up with each other. This is similar to what happens in [Kaggle competitions](https://yanirseroussi.com/tags/kaggle/) and other sports, where simply knowing that a score is attainable causes all competitors to put in extra effort to attain it.

It's a different story when it comes to special-purpose AI tools that are trained on proprietary data. MagicGrantMaker is an example of such a tool: its value would come from being hyper-niche and collecting a unique dataset from specific customers. It's simple, but not easy. And the hardest part is execution over time rather than coming up with new ideas.
