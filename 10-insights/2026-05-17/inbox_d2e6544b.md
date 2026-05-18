---
id: inbox_d2e6544b
date: 2026-05-17
source_ref: "[[00-inbox/.../inbox_d2e6544b]]"
title: "MiroThinker-1.7, an open-weight deep research agent (Qwen3 MoE base) — mini is 30B/3B active, curious what tok/s people get on consumer hardware"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tfsmov/mirothinker17_an_openweight_deep_research_agent/
source: reddit-localllama
published_at: 2026-05-17T15:26:43+00:00
fetched_at: 2026-05-18T04:12:41.961471+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "MiroThinker-1.7 是基於 Qwen3 MoE 架構的開權重深度研究 agent。Mini 版本採 30B 總參數/3B active 配置。官方發佈 6 項 benchmark 結果：BrowseComp (full 74.0% / mini 67.9%)、BrowseComp-ZH (full 75.3% / mini 72.3%)、HLE-Text (42.9% / 36.4%)、GAIA (82.7% / 80.3%)、xbench-DS (62.0% / 57.2%)、SEAL-0 (53.0% / 48.2%)。模型權重已上傳 HuggingFace。作者特別徵求社群在消費級硬體上的實測 token/s 效能反饋與對 sliding window K=5 + episode restart context 管理策略的意見。"
key_points:
  - "MiroThinker-1.7-mini：30B 總參數、3B active，基於 Qwen3 MoE；6 項 benchmark 具體成績已公開"
  - "Sliding window K=5 + episode restart context 管理機制，適應長鏈推理"
  - "開源權重在 HuggingFace；作者徵求消費級硬體 tok/s 實測與 context 策略反饋"
tags: [mirothinker, qwen, moe, deep-research-agent, benchmark, open-weight]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## MiroThinker-1.7, an open-weight deep research agent (Qwen3 MoE base) — mini is 30B/3B active, curious what tok/s people get on consumer hardware

MiroThinker-1.7 是基於 Qwen3 MoE 架構的開權重深度研究 agent。Mini 版本採 30B 總參數/3B active 配置。官方發佈 6 項 benchmark 結果：BrowseComp (full 74.0% / mini 67.9%)、BrowseComp-ZH (full 75.3% / mini 72.3%)、HLE-Text (42.9% / 36.4%)、GAIA (82.7% / 80.3%)、xbench-DS (62.0% / 57.2%)、SEAL-0 (53.0% / 48.2%)。模型權重已上傳 HuggingFace。作者特別徵求社群在消費級硬體上的實測 token/s 效能反饋與對 sliding window K=5 + episode restart context 管理策略的意見。

### 重點
- MiroThinker-1.7-mini：30B 總參數、3B active，基於 Qwen3 MoE；6 項 benchmark 具體成績已公開
- Sliding window K=5 + episode restart context 管理機制，適應長鏈推理
- 開源權重在 HuggingFace；作者徵求消費級硬體 tok/s 實測與 context 策略反饋

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tfsmov/mirothinker17_an_openweight_deep_research_agent/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# MiroThinker-1.7, an open-weight deep research agent (Qwen3 MoE base) — mini is 30B/3B active, curious what tok/s people get on consumer hardware

As usual, disclosure first: I'm on the team that built this. Our MiroThinker-1.7-deepresearch and 1.7-mini-deepresearch API went live, mini is a deep research agent built on Qwen3 MoE (30B total, 3B active for mini). Weights on HuggingFace: huggingface.co/miromind-ai/MiroThinker-1.7 Posting here because the open-weight agent conversation mostly happens in this sub and I'd genuinely like feed because commenting in reddit and discussing did get me some feedback, but it was actually not enough. Tried to load a github APP on our DC server to get PR notified faster but realized there was actually not enough and one was a promo. Benchmarks (arxiv Table 1, cherry-picked to fit a table but full comparison in paper): Model BrowseComp BrowseComp-ZH HLE-Text GAIA xbench-DS SEAL-0 MiroThinker-1.7 74.0 75.3 42.9 82.7 62.0 53.0 MiroThinker-1.7-mini (30B/3B active) 67.9 72.3 36.4 80.3 57.2 48.2 Qwen3.5-397B 78.6 70.3 48.3 – – 46.9 DeepSeek-V3.2 67.6 65.0 40.8 – – 49.5 GPT-5 (closed, for context) 54.9 65.0 35.2 76.4 75.0 51.4 Two things I'd specifically want this sub to push back on: The mini model is only 3B active params — anyone tried running it locally yet? Curious what tok/s people are getting on consumer hardware. Our context management (sliding window K=5 + episode restarts) is opinionated. If you've run long-context agents locally you probably have opinions on this. Paper: arXiv:2603.15726 See y'all in the comments, will reply tomorrow~ please don't downvote me, for a genuinely good open-source project we ARE not getting enough dev feedback and Reddit has been a good source so far. &#32; submitted by &#32; /u/MiroMindAI [link] &#32; [comments]

</details>