---
id: inbox_2ca272a7
source: hackernews
source_type: hn
url: "https://news.ycombinator.com/item?id=49026810"
author: "adam_rida"
published_at: 2026-07-23T19:26:01+00:00
fetched_at: 2026-07-27T01:24:46.700938+00:00
content_hash: "a4bda1b32ad3786c1051ef80043c57402ec97a09c05666c1d4eae63e67d8d9a4"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: Echo – Fable-level results at 1/3 the cost using open-weight models

I’ve been building Echo ( https:&#x2F;&#x2F;echo.tracerml.ai&#x2F; ), an experiment in making one AI system out of a pool of open-weight models rather than choosing a single model and using it for every task. It started with a simple experiment. I took a group of models, including GLM-5.2, Kimi K2.7 and others, and ran them on the same evaluations. Then I measured what would happen if, for each problem, you somehow knew in advance which models would be useful and how their outputs should be combined. That hypothetical system performed substantially better than any individual model in the pool. Of course, it is not something you can actually deploy because it relies on knowing which decisions were good after seeing the result. Echo is my attempt to recover some of that advantage without having that information in advance. For each request, Echo decides how much computation to allocate, which models should participate, and how their work should be combined. Some prompts may only need a relatively small amount of inference, while others benefit from multiple models working on different parts of the problem. One thing that surprised me while building it was how complementary the models are. A model that is clearly weaker overall can still be extremely useful on particular problems or as part of a combination. On my first evaluation mix, Echo consistently performed better than the best individual model in its pool. It also reached roughly the same aggregate result as Fable, which I used as one of the stronger comparison systems, at around one third of the inference cost. There are still some cases where Echo makes the wrong allocation or combination decision. I’m currently spending a lot of time understanding those failures, as well as testing whether the same approach holds up on coding and agentic tasks where measuring the quality of each decision becomes much harder. I built a chat interface (echo.tracerml.ai) and an OpenAI-compatible API ( https:&#x2F;&#x2F;echo.tracerml.ai&#x2F;docs&#x2F;api ) so the system can be tested outside the evaluation setup. Here is a short&#x2F;high level video on how it works: https:&#x2F;&#x2F;www.youtube.com&#x2F;watch?v=lJFJSvOdXhg I wrote up the evaluation methodology, individual model results, costs and current limitations here: https:&#x2F;&#x2F;echo.tracerml.ai&#x2F;eval I would love for you to try it! Especially if you hit any weird failure cases or places where the allocation looks unintuitive.