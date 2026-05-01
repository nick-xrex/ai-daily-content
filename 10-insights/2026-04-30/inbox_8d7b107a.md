---
id: inbox_8d7b107a
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-localllama-follow-up-qwen3-6-27b-on-1-rtx-3090-push-0848]]"
title: "Follow-up: Qwen3.6-27B on 1× RTX 3090 — pushing to ~218K context + ~50–66 TPS, tool calls now stable (PN12 fix)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t07su1/followup_qwen3627b_on_1_rtx_3090_pushing_to_218k/
source: reddit-localllama
published_at: 2026-04-30T20:20:21+00:00
fetched_at: 2026-05-01T13:31:34.607056+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "在單塊 RTX 3090 GPU 上優化 Qwen 3.6-27B 推理的詳細報告。通過修復 vLLM Genesis 補丁 (PN12) 的 anchor drift 問題，解決了長工具輸出（25K tokens）導致的 OOM 崩潰。最終實現 218K context 長度下 50–66 TPS（文本/代碼），加入視覺模型時為 198K context @ 51/68 TPS。優化權衡了高上下文長度、可用吞吐量和工具調用穩定性。"
key_points:
  - "性能指標：218K context @ 50–66 TPS (文本/代碼)，198K+vision @ 51–68 TPS，單塊 3090 實現"
  - "根因修復：Genesis patch PN12 中的 anchor drift 致使長工具輸出(25K token) 觸發 OOM，修復後穩定性大幅提升"
  - "設計選擇：相比先前 125K context 高 TPS，轉向更高上下文但吞吐稍低，以支持實際 agent 工作流穩定性"
tags: [qwen-3.6, vllm-optimization, gpu-inference, tool-calling, context-window]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## Follow-up: Qwen3.6-27B on 1× RTX 3090 — pushing to ~218K context + ~50–66 TPS, tool calls now stable (PN12 fix)

在單塊 RTX 3090 GPU 上優化 Qwen 3.6-27B 推理的詳細報告。通過修復 vLLM Genesis 補丁 (PN12) 的 anchor drift 問題，解決了長工具輸出（25K tokens）導致的 OOM 崩潰。最終實現 218K context 長度下 50–66 TPS（文本/代碼），加入視覺模型時為 198K context @ 51/68 TPS。優化權衡了高上下文長度、可用吞吐量和工具調用穩定性。

### 重點
- 性能指標：218K context @ 50–66 TPS (文本/代碼)，198K+vision @ 51–68 TPS，單塊 3090 實現
- 根因修復：Genesis patch PN12 中的 anchor drift 致使長工具輸出(25K token) 觸發 OOM，修復後穩定性大幅提升
- 設計選擇：相比先前 125K context 高 TPS，轉向更高上下文但吞吐稍低，以支持實際 agent 工作流穩定性

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t07su1/followup_qwen3627b_on_1_rtx_3090_pushing_to_218k/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Following up on our <a href="https://www.reddit.com/r/LocalLLaMA/comments/1stjx29/an_overnight_stack_for_qwen3627b_85_tps_125k/">previous post</a> about running Qwen3.6-27B on a single RTX 3090 (~125K context, higher TPS).</p> <p>We’ve been pushing further on both context length and stability for tool-agent workloads.</p> <p>Current results:</p> <p>- ~218K context @ ~50 / 66 TPS (text, narr/code)</p> <p>- ~198K + vision @ ~51 / 68 TPS</p> <p>- tool calls with ~25K-token outputs now complete without OOM</p> <p>So lower TPS than our earlier config, but significantly higher context + stability under real workloads.</p> <p>---</p> <p>### What changed</p> <p>Previously, long tool outputs (~25K tokens) would consistently crash.</p> <p>This turned out to be related to a Genesis patch (PN12) that was supposed to mitigate a memory issue, but wasn’t actually applying on vLLM dev205+:</p> <p>- `apply_all` reported success</p> <p>- but the underlying code path was unchanged</p> <p>Root cause was anchor drift in the patch.</p> <p>After fixing that, the tool-prefill OOM disappeared and higher context configs became usable.</p> <p>Fix:</p> <p><a href="https://github.com/Sandermage/genesis-vllm-patches">https://github.com/Sandermage/genesis-vllm-patches</a> (PR #13)</p> <p>---</p> <p>### What we’re optimizing for</p> <p>The goal here isn’t just max TPS or max context in isolation, but pushing both together on a single 3090:</p> <p>- high context (200K+)</p> <p>- usable throughput</p> <p>- stable tool-agent workloads</p> <p>---</p> <p>### Notes / limitations</p> <p>- There is still a second memory cliff around ~50–60K for single-prompt workloads on 1 GPU</p> <p>- That one doesn’t apply with tensor parallelism (e.g. 2× 3090)</p> <p>- Results depend heavily on quantization + config</p> <p>---</p> <p>### Repro</p> <p><a href="https://github.com/noonghunna/club-3090">https://github.com/noonghunna/club-3090</a></p> <p>---</p> <p>Curious how others are balancing context vs TPS on 3090/4090 setups.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/AmazingDrivers4u"> /u/AmazingDrivers4u </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t07su1/followup_qwen3627b_on_1_rtx_3090_pushing_to_218k/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t07su1/followup_qwen3627b_on_1_rtx_3090_pushing_to_218k/">[comments]</a></span>

</details>