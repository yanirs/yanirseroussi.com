---
title: Nudging ChatGPT to invent books you have no time to read
author: Yanir Seroussi
type: post
date: 2024-02-12T05:00:00+00:00
url: /2024/02/12/nudging-chatgpt-to-invent-books-you-have-no-time-to-read/
cover:
  relative: true
  image: chatgpt-plus-road-trip.webp
  alt: Cars on the road with a mountain in the background
  caption: Road trips are more fun with ChatGPT Plus
summary: Getting ChatGPT Plus to elaborate on possible book content and produce a PDF cheatsheet, with the goal of learning about its capabilities.
tags:
  - artificial intelligence
  - software engineering
---

Large language models like ChatGPT have a wide range of capabilities. One way to discover use cases is to [spend time chatting with the bots](https://www.oneusefulthing.org/i/137082758/inside-the-jagged-frontier). Sometimes, by asking them to do things that may seem unnatural, you discover new useful capabilities. Here is a quick story demonstrating this sort of exploration.

## Inventing a book summary

On a longish drive from Visalia to Los Angeles, I read [Chris Riccomini's thought-provoking post on database disassembly and its implications](https://materializedview.io/p/databases-are-falling-apart). At the bottom of the post, there's a short promotional blurb that says:

> Support this newsletter by purchasing [The Missing README: A Guide for the New Software Engineer](https://www.amazon.com/Missing-README-Guide-Software-Engineer/dp/1718501838) for yourself or gifting it to someone.

While my new software engineer days are in the distant past, fresh takes on the basics can be worth reviewing. In addition, my brother [Uri Seroussi](https://www.uriseroussi.com/) &ndash; who is a new software engineer &ndash; was sitting right next to me. So I followed the link, read the overview, skimmed the reviews, and recommended the book to Uri.

But... it was a long drive. I figured it'd be fun to get ChatGPT Plus to summarise the book for us &ndash; without it having access to the actual book. In response to the initial prompt, it ran a web search, which resulted in a high-level summary that wasn't very useful (see [the full transcript](https://chat.openai.com/share/bfe9c803-5cf9-4618-b06a-a6a3e7196c8f) for details). I then asked it to go deeper on the first lesson, to which it replied:

> It seems that the specific details of the first practical lesson from "The Missing README: A Guide for the New Software Engineer" are not readily available in the search results. The book covers a wide range of essential skills, techniques, and heuristics necessary for effective software engineering, focusing on the realities of the workplace that are not typically taught in school or bootcamps. For a detailed dive into the first practical lesson, it would be best to consult the book directly, as it appears to be structured in a way that sequentially builds on the knowledge and skills crucial for a new software engineer's success in the industry.

Useless again...

I asked it to tell me what it knows without searching the web, to which it replied with a summary that was only loosely connected to the stated contents of the book.

Not good enough!

I threw the full summary from Amazon at it, which includes these points:

> You'll learn:
> * How to use the legacy code change algorithm, and leave code cleaner than you found it
> * How to write operable code with logging, metrics, configuration, and defensive programming
> * How to write deterministic tests, submit code reviews, and give feedback on other people's code
> * The technical design process, including experiments, problem definition, documentation, and collaboration
> * What to do when you are on-call, and how to navigate production incidents
> * Architectural techniques that make code change easier
> * Agile development practices like sprint planning, stand-ups, and retrospectives

**Then I asked it to go deep on the first point, and it delivered a proper summary that seemed legit!**

As Uri was driving, I got the ChatGPT app to read out each summary. This continued with subsequent points, with me prompting ChatGPT with "OK, next point", it inventing some stuff that sounded about right, Uri and me discussing the output, and so on.

Should Uri still read the book? Probably. Reading well-written books helps lessons sink in better than listening to made up summaries. That said, the summaries did provide a good overview of the book topics, and they were educational.

While I probably wouldn't have had this conversation if it wasn't for the long drive, I still find this use case interesting. **It's not the first time I got ChatGPT to elaborate on specific allusions &ndash; and obtained informative results.** The general pattern is giving it some text and asking _"what might they mean by X?"_

## The cheatsheet game

There was still time on the drive, so I thought it would be fun to get ChatGPT to turn the summaries into a cheatsheet for quick reference. While I could ask for a cheatsheet-like summary and then format it myself, **asking for things that aren't strictly necessary is a good way to learn about ChatGPT's capabilities.**

I made this request:

> Can you create a pretty cheatsheet summarising the main lessons? Run code if needed to do stuff like putting text in multiple columns so it fits on a single page.

Unfortunately, the result of the first attempt was horrible &ndash; too much text, too little content, and illegible:

<style>
.post-content figure.cheatsheet img {
  max-height: 500px;
  border: solid 1px;
}
</style>

{{< figure src="cheatsheet-first-attempt.png" alt="ChatGPT's first cheatsheet attempt (pretty bad)" class="cheatsheet" >}}

The second attempt was even worse. It misunderstood my intention when I asked it to _cram as much useful info as possible into a single page_. This resulted in completely unreadable text on a mostly-blank page:

{{< figure src="cheatsheet-second-attempt.png" alt="ChatGPT's second cheatsheet attempt (worse than the first)" class="cheatsheet" >}}

Getting it to produce something useful required moving it away from creating an image with the Pillow package. I told it to produce HTML and export it to PDF with code, which put it on the right track.

From that point, it was a matter of telling it to tweak formatting and wording, and we ended up with [a usable PDF cheatsheet](cheatsheet-for-new-software-engineers-final.pdf):

{{< figure src="cheatsheet-final-pdf-attempt.webp" alt="ChatGPT's final cheatsheet attempt (screenshot of the PDF)" link="cheatsheet-for-new-software-engineers-final.pdf" class="cheatsheet" >}}

Unfortunately, the cheatsheet partly lost touch with the book summary, but the bits ChatGPT decided to add aren't terrible. Also, the drive was over, so it was time to bring the cheatsheet game to an end.

## Conclusion

While this may seem like a pointless exercise, I'm pleased with these outcomes:
* Relearning that getting ChatGPT to elaborate on summary bullet points can be useful &ndash; or at least somewhat entertaining.
* Coming up with the HTML to PDF export path as a way to get ChatGPT to produce nice-looking PDFs.
* Producing a lovely cheatsheet that contains some sound advice.

Overall, I still find ChatGPT mind-blowing. My usage of it reduced a bit last year, but since I got the Plus subscription, it's a completely different story. And the really amazing thing is that it's still early days for this technology. Exciting times!
