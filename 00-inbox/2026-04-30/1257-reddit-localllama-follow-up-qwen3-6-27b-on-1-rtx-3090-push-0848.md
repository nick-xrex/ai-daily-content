---
id: inbox_8d7b107a
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t07su1/followup_qwen3627b_on_1_rtx_3090_pushing_to_218k/"
author: "/u/AmazingDrivers4u"
published_at: 2026-04-30T20:20:21+00:00
fetched_at: 2026-05-01T12:57:17.645212+00:00
content_hash: "0848e2ce63d4ab0f4f692f7cb19067ae8a5f8df7b4893895c3cc0aa1202b1403"
lang: en
caption_quality: None
raw: true
topics: []
---

# Follow-up: Qwen3.6-27B on 1× RTX 3090 — pushing to ~218K context + ~50–66 TPS, tool calls now stable (PN12 fix)

<!-- SC_OFF --><div class="md"><p>Following up on our <a href="https://www.reddit.com/r/LocalLLaMA/comments/1stjx29/an_overnight_stack_for_qwen3627b_85_tps_125k/">previous post</a> about running Qwen3.6-27B on a single RTX 3090 (~125K context, higher TPS).</p> <p>We’ve been pushing further on both context length and stability for tool-agent workloads.</p> <p>Current results:</p> <p>- ~218K context @ ~50 / 66 TPS (text, narr/code)</p> <p>- ~198K + vision @ ~51 / 68 TPS</p> <p>- tool calls with ~25K-token outputs now complete without OOM</p> <p>So lower TPS than our earlier config, but significantly higher context + stability under real workloads.</p> <p>---</p> <p>### What changed</p> <p>Previously, long tool outputs (~25K tokens) would consistently crash.</p> <p>This turned out to be related to a Genesis patch (PN12) that was supposed to mitigate a memory issue, but wasn’t actually applying on vLLM dev205+:</p> <p>- `apply_all` reported success</p> <p>- but the underlying code path was unchanged</p> <p>Root cause was anchor drift in the patch.</p> <p>After fixing that, the tool-prefill OOM disappeared and higher context configs became usable.</p> <p>Fix:</p> <p><a href="https://github.com/Sandermage/genesis-vllm-patches">https://github.com/Sandermage/genesis-vllm-patches</a> (PR #13)</p> <p>---</p> <p>### What we’re optimizing for</p> <p>The goal here isn’t just max TPS or max context in isolation, but pushing both together on a single 3090:</p> <p>- high context (200K+)</p> <p>- usable throughput</p> <p>- stable tool-agent workloads</p> <p>---</p> <p>### Notes / limitations</p> <p>- There is still a second memory cliff around ~50–60K for single-prompt workloads on 1 GPU</p> <p>- That one doesn’t apply with tensor parallelism (e.g. 2× 3090)</p> <p>- Results depend heavily on quantization + config</p> <p>---</p> <p>### Repro</p> <p><a href="https://github.com/noonghunna/club-3090">https://github.com/noonghunna/club-3090</a></p> <p>---</p> <p>Curious how others are balancing context vs TPS on 3090/4090 setups.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/AmazingDrivers4u"> /u/AmazingDrivers4u </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t07su1/followup_qwen3627b_on_1_rtx_3090_pushing_to_218k/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t07su1/followup_qwen3627b_on_1_rtx_3090_pushing_to_218k/">[comments]</a></span>