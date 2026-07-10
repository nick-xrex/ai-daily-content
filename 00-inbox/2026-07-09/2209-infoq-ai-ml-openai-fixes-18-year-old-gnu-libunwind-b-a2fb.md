---
id: inbox_b30eac19
source: infoq-ai-ml
source_type: rss
url: "https://www.infoq.com/news/2026/07/openai-libunwind-core-dumps/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering"
author: "Steef-Jan Wiggers"
published_at: 2026-07-09T10:15:00+00:00
fetched_at: 2026-07-09T22:09:55.931910+00:00
content_hash: "a2fbab273431b65ae7c202f2d20cd3b8ef3886cd00c69afcaee9d2bfe579983d"
lang: en
caption_quality: None
raw: true
topics: []
---

# OpenAI Fixes 18-Year-Old GNU libunwind Bug by Treating Crash Debugging Like Epidemiology

OpenAI found two unrelated bugs masquerading as one in ChatGPT's data infrastructure. Silent hardware corruption on one Azure host and an 18-year-old race condition in GNU libunwind's setcontext function with a one-instruction vulnerability window. The breakthrough came from switching to population-level crash analysis rather than examining individual core dumps. By Steef-Jan Wiggers