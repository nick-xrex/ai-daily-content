---
id: inbox_99078335
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tgqpa8/qwen_35b_a3b_surprises_me/"
author: "/u/siegevjorn"
published_at: 2026-05-18T15:50:58+00:00
fetched_at: 2026-05-18T18:51:02.683750+00:00
content_hash: "5ea6b7a3b584c51718de0c16d372ffa0db0d67ef33aac43f442dfcc86ed80881"
lang: en
caption_quality: None
raw: true
topics: []
---

# Qwen 35b a3b surprises me

Just wanted to share that I'm pretty happy about Qwen 35b a3b agentic coding performance. I'm running the model in q80 quant, kv cache both q8_0 as well, with 262144 in 4090 + 5060 ti, via llama.cpp backend with claude code pointing to localhost. For demo/data analytics purposes, it works pretty well. I haven't used it for large codebases, but it definitely is better than gemma4 26b in my use case. One thing that surprises me is that it seems to get better outcome in agentic coding, than chat. When using it with just chat UI, i found the code qwen35b provide a bit too clunky. I wonder of others have compared its performance against open source harnesses (Pi / opencode). &#32; submitted by &#32; /u/siegevjorn [link] &#32; [comments]