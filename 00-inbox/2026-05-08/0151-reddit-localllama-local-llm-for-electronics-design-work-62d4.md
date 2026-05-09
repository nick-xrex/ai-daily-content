---
id: inbox_045e60b1
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t7c3p6/local_llm_for_electronics_design_work/"
author: "/u/deafenme"
published_at: 2026-05-08T15:58:08+00:00
fetched_at: 2026-05-09T01:51:59.662568+00:00
content_hash: "62d433470c60b74291b131648d49c1f48e886db44df8ab5975dc87fa7035ef6b"
lang: en
caption_quality: None
raw: true
topics: []
---

# Local LLM for electronics design work?

Another hobby is working on electronics projects ranging from low-voltage control and signal processing to HV tube amp circuits. I design and simulate in LTspice before prototyping. I often use the cloud models for design help; they're great at architecture and topology, but when you get down to the details they start to lose the thread, and in the worst case, start hallucinating and giving patently bad guidance. Qwen3.6 is similar; t gets the big picture fine, but gets lost in the details, *especially* when troubleshooting. It also doesn't understand SPICE netlists as well as the cloud models (obviously). Are there any local LLMs that are optimized for electronics work? My crappy CPU-only rig works for models up to about 27B dense. (Sample prompt for a HV LFO: &quot;Design a wien bridge oscillator circuit using a differential amp built from a pair of DN2540 mosfets and a CCS tail, and a VTL5C2 vactrol as the AGC control element. Power rails are 300V, 0V, -72V. Target frequency is 4Hz. Target output is 20Vpp, driving a 1M load. Start by describing the architecture.&quot;) &#32; submitted by &#32; /u/deafenme [link] &#32; [comments]