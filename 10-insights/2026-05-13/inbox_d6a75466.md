---
id: inbox_d6a75466
date: 2026-05-13
source_ref: "[[00-inbox/.../inbox_d6a75466]]"
title: "we really all are going to make it, aren&#39;t we? 2x3090 setup."
url: https://www.reddit.com/r/LocalLLaMA/comments/1tcf2dt/we_really_all_are_going_to_make_it_arent_we/
source: reddit-localllama
published_at: 2026-05-13T22:25:53+00:00
fetched_at: 2026-05-18T03:40:23.834105+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者分享雙 RTX 3090 本地 AI 設置可行性：改用 Ubuntu 原生系統後性能相比 WSL2 提升 10 倍以上（達 4000 pp/s、113 tokens/s），運行 Qwen 3.6 27B（262k context）。使用者表示模型任務效果接近 Claude Sonnet 級別且速度遠超雲端；已用其進行代碼修復與審查。討論未來升級路徑（M5 Ultra 512GB + 4x DGX Spark），反思 12 個月內特定領域小模型是否能達成前沿級效能。"
key_points:
  - "基礎設施選擇影響巨大：Ubuntu 原生 vs WSL2 性能差異 10 倍（4000 pp/s vs ~400 pp/s），無需 NVLink"
  - "消費級硬體性能指標：雙 RTX 3090、48GB VRAM，Qwen 27B 達 113 tokens/s、4000 pp/s"
  - "成本效益新局：本地運行效能接近商用模型級別，成本遠低於雲端，促進開源模型經濟可行性"
tags: [rtx-3090, local-ai, qwen, ubuntu-vs-wsl2, inference-optimization]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## we really all are going to make it, aren't we? 2x3090 setup.

使用者分享雙 RTX 3090 本地 AI 設置可行性：改用 Ubuntu 原生系統後性能相比 WSL2 提升 10 倍以上（達 4000 pp/s、113 tokens/s），運行 Qwen 3.6 27B（262k context）。使用者表示模型任務效果接近 Claude Sonnet 級別且速度遠超雲端；已用其進行代碼修復與審查。討論未來升級路徑（M5 Ultra 512GB + 4x DGX Spark），反思 12 個月內特定領域小模型是否能達成前沿級效能。

### 重點
- 基礎設施選擇影響巨大：Ubuntu 原生 vs WSL2 性能差異 10 倍（4000 pp/s vs ~400 pp/s），無需 NVLink
- 消費級硬體性能指標：雙 RTX 3090、48GB VRAM，Qwen 27B 達 113 tokens/s、4000 pp/s
- 成本效益新局：本地運行效能接近商用模型級別，成本遠低於雲端，促進開源模型經濟可行性

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tcf2dt/we_really_all_are_going_to_make_it_arent_we/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# we really all are going to make it, aren't we? 2x3090 setup.

i'm blown away. i saw someone made a post the other day about &quot;club-3090&quot; and after having sonnet patch some fixes into it, specifically a sse-session drop bug and a bug with tool-calling, it's fair to say that even &quot;budget&quot; setups like myself will have a path forward soon for only-local-ai. reference github: https://github.com/noonghunna/club-3090 (not mine) after getting this running, i was originally using WSL2. fair to say, it was &quot;better&quot; than LM studio but not quite good. t/s was like 30 and pp was around 400....i said fuck it and installed ubuntu as dual boot on the same machien (i'm just not very linux friendly when it's headless, prefer windows RDP) and wow. i'm getting like 4000 pp/s and 113 tk/s with no nvlink. supposedly, nvlink would make it faster..... either way, i'm very excited about this new local future. qwen 3.6 27b with 262k on 48 GB VRAM feels almost-sonnet level, and it's MUCH faster than cloud. and useful! I had it make some monkey patches and they work fantastic, and well as some relatively useful code reviews. im working now on making it work to handle my ssh sessions on my linux computers now. wondering what the next upgrade path could be. i was thinking about m5 ultra 512 GB + 4x DGX Sparks (prompt processing speeeeed) but now I'm wondering if we'll reach frontier class intelligence (maybe only domain specific) in smaller models in the next 12 months? awesome! &#32; submitted by &#32; /u/RedShiftedTime [link] &#32; [comments]

</details>