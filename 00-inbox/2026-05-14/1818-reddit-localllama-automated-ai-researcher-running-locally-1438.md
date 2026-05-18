---
id: inbox_d9c6eca4
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tcu5r8/automated_ai_researcher_running_locally_with/"
author: "/u/lewtun"
published_at: 2026-05-14T10:32:04+00:00
fetched_at: 2026-05-14T18:18:30.429310+00:00
content_hash: "1438ae1cd417f0b14d8d491622d64b7a4d18fa19f289a34bfe2a19cb44b84d9e"
lang: en
caption_quality: None
raw: true
topics: []
---

# Automated AI researcher running locally with llama.cpp

Hi everyone, I'm happy to share ml-intern, which is a harness for agents to have tighter integration with Hugging Face's open-source libraries (transformers, datasets, trl, etc) and Hub infrastructure: https://github.com/huggingface/ml-intern The harness is quite simple (basically tools + system prompt) and we built it initially for Claude Opus. However, now that open models are getting really good at agentic workflows, I just added support for running ml-intern with local models via llama.cpp or ollama. As you can see in the video, Qwen3.6-35B-A3B is able to SFT a model end-to-end by orchestrating CPU/GPU sandboxes and jobs on the Hub. I find this pretty neat because we can now have an AI researcher running 24/7 on a laptop, without maxing out token limits :) Anyway, I hope this is useful to the community and please let me know if there are any features that you'd like us to include. &#32; submitted by &#32; /u/lewtun [link] &#32; [comments]