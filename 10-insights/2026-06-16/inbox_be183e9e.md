---
id: inbox_be183e9e
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-simon-willison-quoting-georgi-gerganov-8540]]"
title: "Quoting Georgi Gerganov"
url: https://simonwillison.net/2026/Jun/16/georgi-gerganov/#atom-everything
source: simon-willison
published_at: 2026-06-16T16:04:59+00:00
fetched_at: 2026-06-16T22:08:51.870669+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GGML 組織維護者 Georgi Gerganov 分享了在 M2 Ultra 和 RTX 5090 上使用 Qwen3.6-27B 進行日常開發工作的實踐經驗。該本地模型被證實在代碼審查和維護任務中相當有效，儘管他大部分時間花在 PR 審查上。他使用輕量級的 pi agent（去除所有功能）配合簡短系統提示來對齊工作風格。"
key_points:
  - "Qwen3.6-27B 在 M2 Ultra 和 RTX 5090 上可穩定用於開發"
  - "用於代碼審查和維護任務，已在 GGML 組織驗證"
  - "輕量級 harness（pi -nc --offline）配短系統提示即可滿足實際需求"
tags: [local-llms, qwen, ai-coding, developer-experience]
topics: []
importance: 2
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Georgi Gerganov

GGML 組織維護者 Georgi Gerganov 分享了在 M2 Ultra 和 RTX 5090 上使用 Qwen3.6-27B 進行日常開發工作的實踐經驗。該本地模型被證實在代碼審查和維護任務中相當有效，儘管他大部分時間花在 PR 審查上。他使用輕量級的 pi agent（去除所有功能）配合簡短系統提示來對齊工作風格。

### 重點
- Qwen3.6-27B 在 M2 Ultra 和 RTX 5090 上可穩定用於開發
- 用於代碼審查和維護任務，已在 GGML 組織驗證
- 輕量級 harness（pi -nc --offline）配短系統提示即可滿足實際需求

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/16/georgi-gerganov/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I can 100% attest to the fact that Qwen3.6-27B is a very capable local model for coding tasks. Over the last month and a half I've been using it almost daily, either on my M2 Ultra or on my RTX 5090 box. I use it for small mundane tasks at ggml-org - nothing really impressive, but definitely a helpful tool for a maintainer. I think I would be using it much more, if I didn't have to spend a lot of my time on reviewing PRs. Currently, I have a very lightweight harness - the pi agent with everything stripped ( pi -nc --offline ) and a short system prompt to align it a bit with my style. 
 &mdash; Georgi Gerganov , Hacker News comment on Running local models is good now by Boykis 

 Tags: georgi-gerganov , llms , ai , generative-ai , pi , ai-assisted-programming , local-llms , qwen , coding-agents

</details>