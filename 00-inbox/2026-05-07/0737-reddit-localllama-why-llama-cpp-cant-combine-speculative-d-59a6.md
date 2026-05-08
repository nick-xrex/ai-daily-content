---
id: inbox_86e15356
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t63snn/why_llamacpp_cant_combine_speculative_decode/"
author: "/u/Qwoctopussy"
published_at: 2026-05-07T07:53:13+00:00
fetched_at: 2026-05-08T07:37:41.355536+00:00
content_hash: "59a635610f66cce8ad4e71b31e87ca054552b06e0b9cf2f0e0f1434e88054a49"
lang: en
caption_quality: None
raw: true
topics: []
---

# why llama.cpp can’t combine speculative decode methods?

dicking around with the new mtp speculative decode with qwen3.6 27b, and it’s great. but for agentic coding i’ve seen significant improvements from ngram, because a decent fraction of the time (e.g. calling edit tool) the model is just repeating verbatim a section of code that it has already seen before. ngram can speculate on a lot of tokens reeaallly fast in comparison. it’d be great if we could combine them by using them both at the same time, but it looks like if i add them both to the command line arguments, only ngram is active. is there any reason both can’t be used simultaneously? fundamental limitation, or just an implementation limit with a fix on the horizon? EDIT: just looked at the PR again and PmNz8 asked the same question like two hours before i posted this. go give it an updoot! https://github.com/ggml-org/llama.cpp/pull/22673#issuecomment-4394544777 &#32; submitted by &#32; /u/Qwoctopussy [link] &#32; [comments]