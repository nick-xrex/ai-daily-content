---
id: inbox_3fb5561a
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t2t1w4/gemma_4_e2b_runs_surprisingly_well_on_my_8gb/"
author: "/u/Effective-Drawer9152"
published_at: 2026-05-03T18:17:28+00:00
fetched_at: 2026-05-04T13:38:38.114718+00:00
content_hash: "8fc91529faedf4aa9a393e4ac4e32a3de4c5b4aeab0e6449f9f342d6a2af6bc0"
lang: en
caption_quality: None
raw: true
topics: []
---

# Gemma 4 E2B runs surprisingly well on my 8GB Android phone, so I built a private voice notes app around it.

<!-- SC_OFF --><div class="md"><p>Been running Gemma 4 E2B locally on my OnePlus CE 5 (8GB RAM) for a few months. Chat quality is fine for the size. What surprised me was JSON output. Short input, give it a structured prompt, you get clean parse able JSON back. Way better than I expected from a 2.4GB model on a phone.</p> <p>Got me thinking about voice notes. You ramble for a few seconds, &quot;call the dentist tomorrow at 3, also buy milk on the way home&quot;, and Gemma can split that into separate items, tag each one (reminder, buy), resolve the time. Tried it for a few weeks. Categorization is actually decent on real notes, not just the toy ones I started with.</p> <p>Built an Android app around it. Whisper Small (244MB) for transcription via Sherpa-ONNX, Gemma 4 E2B (2.4GB) for the splitting and categorization via LiteRT-LM. Both run on the phone, no cloud, no account.</p> <p>End-to-end on the CE 5, a typical 10-15 second voice note takes about 12-15s. Whisper does transcription in ~5s, Gemma categorizes in ~8-10s, rest is model load + Room writes + UI hop. </p> <p>At search time( for eacmple -&gt; &quot;what did I say about the dentist last week&quot;) it does query expansion, rewriting the user's question into keywords plus hypothetical example items before retrieval. Multiple FTS lanes get merged with reciprocal rank fusion, then there's an optional Gemma reranker pass over the top-K with a 15s timeout and fallback to RRF order if it doesn't finish.</p> <p>Curious what people here are doing with local LLMs on their phones lately. Any other good models to try out for local device.<br /> If anyone wants to try it on their own device and share feedback, happy to share it . Mostly looking to know if the categorization holds up on real notes and any weirdness on first model</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Effective-Drawer9152"> /u/Effective-Drawer9152 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2t1w4/gemma_4_e2b_runs_surprisingly_well_on_my_8gb/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2t1w4/gemma_4_e2b_runs_surprisingly_well_on_my_8gb/">[comments]</a></span>