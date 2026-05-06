---
id: inbox_dcda80f1
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t4s6g2/deepseek_v4_being_17x_cheaper_got_me_to_actually/"
author: "/u/spencer_kw"
published_at: 2026-05-05T20:55:56+00:00
fetched_at: 2026-05-06T10:02:16.851750+00:00
content_hash: "b1ef52912409d2bb32c0e56b6654a2242d3920291254a2e9f8360957a1b7e5ad"
lang: en
caption_quality: None
raw: true
topics: []
---

# DeepSeek V4 being 17x cheaper got me to actually measure what I send to cloud vs what I could run locally. the results are stupid.

<!-- SC_OFF --><div class="md"><p>That foodtruck bench post showing deepseek v4 matching gpt-5.2 at 17x cheaper got me thinking. if frontier cloud models are that overpriced for equivalent quality, how much of my daily work even needs cloud at all?</p> <p>Ran my normal coding workflow for 10 days. every task got logged: what it was, tokens in/out, whether local qwen 3.6 27b (on a 3090) could have done it. didn't use benchmarks, just re-ran a random sample of 150 tasks on both.</p> <p>results:</p> <p>- file reads, project scanning, &quot;explain this code&quot;: local matched cloud 97% of the time. this was 35% of my workload. paying for cloud here is genuinely throwing money away.</p> <p>- test writing, boilerplate, single file edits: local matched 88%. another 30% of tasks. the 12% misses were edge cases i could catch in review.</p> <p>- debugging with multi-file context: local dropped to 61%. cloud still better but not 17x-the-price better. about 20% of my work.</p> <p>- architecture decisions, complex refactors across 5+ files: local at 29%. cloud genuinely needed here. only 15% of my tasks.</p> <p>So 65% of my daily coding work runs identically on a model that costs me electricity. another 20% is close enough that I accept the occasional miss. only 15% actually justifies cloud pricing.</p> <p>Started routing by task type. local for the first two buckets, cloud for the last two. my api bill went from $85/month to about $22 and the 3090 was already sitting there mining nothing.</p> <p>The deepseek post is right that the price gap is insane but the bigger insight is that most of us don't even need cloud for most of what we do. we're just too lazy to measure it.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/spencer_kw"> /u/spencer_kw </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4s6g2/deepseek_v4_being_17x_cheaper_got_me_to_actually/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4s6g2/deepseek_v4_being_17x_cheaper_got_me_to_actually/">[comments]</a></span>