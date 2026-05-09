---
id: inbox_dc2390f0
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t7et9q/testing_local_llms_in_practice_code_generation/"
author: "/u/Icy_Programmer7186"
published_at: 2026-05-08T17:33:26+00:00
fetched_at: 2026-05-09T01:51:59.661743+00:00
content_hash: "44498fa3f5e85b8aca515094add22e8f8f087eef6b17ceee14008f4978c4f2f9"
lang: en
caption_quality: None
raw: true
topics: []
---

# Testing Local LLMs in Practice: Code Generation, Quality vs. Speed

Hello, I spent the last few months building an AI agent that autonomously writes Go code using local LLMs. The primary use case is log parser generation for SIEM pipelines. A large part of the work ended up being evaluation itself: how do you objectively measure whether a model is actually useful for autonomous coding tasks? So I built a harness that (1) lets agents generate real Go parsers, (2) compiles the Go code, (3) validates extracted fields and types, (4) measures parsing quality against expected schemas, (5) and tracks throughput/speed over longer runs. Given the current release cadence of open-weight models, the results are interesting. I published the first public version of the benchmark and methodology here: https://ndocs.teskalabs.com/logman.io/blog/2026/04/14/testing-local-llms-in-practice-code-generation-quality-vs-speed/ Feedback is very welcome. Also: which model should I test next? &#32; submitted by &#32; /u/Icy_Programmer7186 [link] &#32; [comments]