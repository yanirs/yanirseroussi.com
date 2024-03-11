---
title: Questions to consider when using AI for PDF data extraction
author: Yanir Seroussi
type: post
date: 2024-03-11T00:00:00+00:00
url: /2024/03/11/questions-to-consider-when-using-ai-for-pdf-data-extraction/
cover:
  relative: true
  image: cover.webp
  alt: Decorative image showing a book and flying documents with an AI-themed overlay
summary: Discussing considerations that arise when attempting to automate the extraction of structured data from PDFs and similar documents.
tags:
  - artificial intelligence
  - data science
  - machine learning
  - software engineering
---
The [jagged frontier](https://www.oneusefulthing.org/p/centaurs-and-cyborgs-on-the-jagged) of AI means that you can't always know which tasks are within the capabilities of current models. One such task is the extraction of structured data from PDFs. While this is fully within the capabilities of humans, there are unique challenges in getting off-the-shelf AIs like ChatGPT to do it well. Variants of this task have come up repeatedly in my recent discussions and work, so I put together this summary of my understanding of when it makes sense to try to automate PDF data extraction with AI.

This post is structured as a series of questions I'd ask about a proposed project. Actual answers will depend on the specific project.

## What is your budget?

I assume there is some business value in the extracted data. Therefore, it's possible to estimate the dollar value of automating the manual processes that are used to extract the data. There's a big difference between an extraction process that takes a junior employee a couple of weeks per year and one that keeps data entry specialists busy year-round. The budget determines the tools that can be used: If it's low (e.g., in the thousands), it's probably only worth spending a few days assessing feasibility with off-the-shelf tools like the OpenAI APIs. If it's higher (e.g., hundreds of thousands), paying AI engineers to build a bespoke system becomes an option.

## How sensitive is the data?

If the data you're working with isn't sensitive (e.g., financial statements by public companies), you're in luck: You can use the best AIs available. A month ago, it was GPT-4. Today, [you have a bunch of other proprietary options](https://simonwillison.net/2024/Mar/8/gpt-4-barrier/). Tomorrow, who knows?

If the data is sensitive and can't leave your organisation's systems, your options are more limited. Depending on other aspects of the problem, it may mean you're better off [waiting for better open models](https://www.oneusefulthing.org/p/the-lazy-tyranny-of-the-wait-calculation). However, given the rate of progress in the open source AI ecosystem, assessing feasibility is about as simple as with proprietary solutions. It's just that right now, you won't be using the most capable models.

## How complex are the PDFs?

There's a wide variety of documents out there. If the PDFs you're working with can be converted to text accurately, the AI models have a good chance of being able to extract the data you're after. If the conversion to text is insufficiently accurate, the AIs stand little chance of outperforming data entry specialists &ndash; they just don't see the PDFs as well as we do.

It's worth spending some time on this question. For example, if you're using OpenAI's APIs and much of the data you're looking to extract is contained in tables within PDFs, you can first test whether you can reliably retrieve and display specific tables. Sticking with the example of financial statements, there's a big difference between [this 124-page sample from Grant Thornton](https://www.grantthornton.global/contentassets/5bd3489f6516406d883a7300da904e96/ifrs-example-financial-statements-2022_feb-2023.pdf) and [this seven-page sample from the Australian Fair Work Commission](https://regorgs.fwc.gov.au/sites/default/files/migration/429/fs023-sample-financial-statements.pdf). Prompting GPT-4 (via ChatGPT Plus) to extract a table from the former PDF produced output that was only loosely-connected to the actual content. By contrast, GPT-4 perfectly reproduced tables from the latter PDF.

In general, perfect conversion of PDF tables to text appears to be an unsolved problem. For example, in [a benchmark from last year](https://arxiv.org/pdf/2303.09957.pdf), the best tool tested only had about 50% accuracy when applied to tables in scientific papers. However, the field keeps moving. You may get an accuracy boost by treating PDFs as images and using vision models, as [recommended by the Unstructured library](https://unstructured-io.github.io/unstructured/best_practices/table_extraction_pdf.html). Anecdotally, I found Unstructured's table parsing to be too inaccurate, but when I used GPT-4 Vision on screenshots of the same tables it yielded much better results. It also outperformed OpenAI's default PDF parser. Your mileage will definitely vary.

Things get even more complicated if some of the data you're hoping to extract is in graphs and other figures contained in the PDFs. Verifying that the PDFs are not too complex _for the AI models_ is definitely worth doing before jumping into more elaborate data extraction tasks.

## Can the tokenised PDFs fully fit in the model's context window?

The complexity of the PDFs determines _how well_ the AI models can see them. Their length determines _how much_ of them the models can see at once. There's nuance depending on whether the PDFs are fully converted to text [tokens](https://platform.openai.com/tokenizer) or to text and images, but the number of tokens that can be fed in (i.e., the context window) is limited with the current generation of AI models. Context windows are rapidly expanding, with [Google recently releasing a million-token model](https://blog.google/technology/ai/google-gemini-next-generation-model-february-2024/) (approximately 700,000 words), but there's still a cost per token that you need to consider when building solutions.

If you're working with PDFs that are larger than your context windows, you're probably going to use retrieval-augmented generation, i.e., break the documents into chunks and feed specific chunks into the model based on the query. With some tools and APIs, this may be handled for you (e.g., with OpenAI's Assistants). However, it introduces a source of inaccuracies that may not be acceptable for your use case.

## What is your teaching approach?

Assuming you're satisfied that the AIs can see enough of the PDFs well enough to provide useful answers, it's time to test different ways of teaching them about the data extraction tasks. The question of which approaches you can test is closely tied to your budget. But even with large budgets, it's best to start simple and only attempt more complicated approaches if the simpler ones fail. In order of implementation complexity, key teaching approaches are:

* **Zero-shot:** Describe the task and the expected output, provide a new PDF, and see if you get the expected output.
* **Few-shot:** In addition to describing the task and expected output, also provide examples of past PDFs and their extracted outputs. Given context window limitations, this is only feasible with relatively short PDFs and simple outputs.
* **Fine-tuning:** This goes beyond the sort of prompting that has become accessible to the general population via ChatGPT. The general idea is that you can get better results by teaching the underlying model about your expected inputs and outputs. Even if you don't have machine learning experts on your team, you may get good results by following resources such as [the fine-tuning guide by OpenAI](https://platform.openai.com/docs/guides/fine-tuning/). However, success isn't guaranteed, so it's important to manage expectations and budgets accordingly. It may well be the case that you're better off waiting a few months or years for new AI models, rather than investing in fine-tuning experimentation. New models are likely to make lower-effort zero/few-shot results better.
* **Custom models:** Taking a step beyond fine-tuning, building custom machine learning models may be a good match for your budget and available expertise. However, you definitely won't be doing it to automate a low-cost-low-frequency data entry process.

Implicit in the above is the availability of some training & testing data (i.e., input PDFs and expected outputs). That is, no matter what approach you follow, you'd want to have some confidence that it works beyond [a few test samples](https://jxnl.github.io/blog/writing/2024/02/05/when-to-lgtm-at-k/) &ndash; use a large representative dataset to gain confidence in your solution.

## Can the AI model understand the input structures?

This is closely related to the question of PDF complexity, but worth considering separately. I'm anthropomorphising a bit by talking about AI _understanding_, but just as they can't see the same as we do, their level of understanding may also be unintuitive. For example, [a recent paper](https://arxiv.org/pdf/2310.09263.pdf) that proposed a fine-tuning approach to improve GPT-3.5's table understanding made the case that general language models can't read tables reliably because:

> Natural language texts are (1) one-directional, (2) read left-to-right, where (3) swapping two tokens will generally change the meaning of a sentence. In contrast, relational tables are (1) two-dimensional in nature with both rows and columns, (2) where reading top-to-bottom in the vertical direction for values in the same column, is crucial in many table-tasks. Furthermore, unlike text, (3) tables are largely "invariant" to row and column permutations, where swapping two rows or columns do not generally change the semantic meaning of the table.

This argument is compelling, but given [the emergent abilities of large language models](https://openreview.net/pdf?id=yzkSU5zdwD) and the fact that we no longer know what goes into proprietary models beyond GPT-3.5, I wouldn't bet on these limitations being an issue for _all_ tabular data. Again, experimenting with your specific use case is key. If you encounter issues, it's worth probing the models to check if they exhibit any semantic understanding beyond just reproducing the inputs.

## Can the AI model understand and produce the output structures?

If you're building custom models, it's straightforward to get exactly the output structure you want (e.g., a complex JSON). Otherwise, if you're prompting a language model, you need to ask [nicely](https://arxiv.org/pdf/2402.14531.pdf) and hope for the best. That said, there are strategies to get models to produce the output structures you want, such as using [OpenAI's function calling](https://platform.openai.com/docs/guides/function-calling) or [the Outlines library](https://github.com/outlines-dev/outlines). However, as with the example of tabular inputs, there is a difference between being able to produce an output that conforms to a specific output schema and populating the schema with values that make semantic sense. Breaking down complex outputs to simpler structures and using [prompt chaining](https://www.promptingguide.ai/techniques/prompt_chaining) may be helpful in some cases.

## What is your long-term validation approach?

Assuming you successfully build an AI solution that can replace manual data entry, should you completely stop manual data extraction? As with other questions, it depends on the use case, but it's worth considering a gradual switch to full automation. For example, you can keep the manual process for 10% of new data to verify that the whole system works as expected. This is especially worth doing when working with publicly-available datasets, as there's a non-zero chance that the models you're using have seen the input training data before (though they probably haven't seen your outputs).

## Anything else?

If I missed important questions, please let me know and I will update this post.
