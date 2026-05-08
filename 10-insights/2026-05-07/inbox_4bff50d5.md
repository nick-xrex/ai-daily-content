---
id: inbox_4bff50d5
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-localllama-9700-pro-users-undervolting-nets-crazy-c-10f3]]"
title: "9700 pro users, undervolting nets crazy clocks"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t6d9la/9700_pro_users_undervolting_nets_crazy_clocks/
source: reddit-localllama
published_at: 2026-05-07T15:06:26+00:00
fetched_at: 2026-05-08T08:05:33.125504+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AMD Radeon 9700 Pro 用戶分享了透過降壓 (undervolting) 和時鐘鎖定達到的效能提升。上週驅動程式解鎖了新 Vulkan 路徑和解鎖時鐘支援，使用戶能在 225W 功率限制下日常達到 3.3–3.58 GHz（突發最高 4 GHz，但不穩定）。用戶確認性能隨時鐘線性提升而非時鐘拉伸，並指出對 LLM 推理工作負載的效能提升。"
key_points:
  - "降壓後 9700 Pro 日常時鐘達 3.3–3.58 GHz @ 225W，突發可達 4 GHz"
  - "上週驅動程式解鎖新 Vulkan 路徑和解鎖時鐘功能"
  - "性能提升確認為線性隨時鐘提升，而非時鐘拉伸"
tags: [amd, gpu-optimization, undervolting, radeon-9700, hardware]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## 9700 pro users, undervolting nets crazy clocks

AMD Radeon 9700 Pro 用戶分享了透過降壓 (undervolting) 和時鐘鎖定達到的效能提升。上週驅動程式解鎖了新 Vulkan 路徑和解鎖時鐘支援，使用戶能在 225W 功率限制下日常達到 3.3–3.58 GHz（突發最高 4 GHz，但不穩定）。用戶確認性能隨時鐘線性提升而非時鐘拉伸，並指出對 LLM 推理工作負載的效能提升。

### 重點
- 降壓後 9700 Pro 日常時鐘達 3.3–3.58 GHz @ 225W，突發可達 4 GHz
- 上週驅動程式解鎖新 Vulkan 路徑和解鎖時鐘功能
- 性能提升確認為線性隨時鐘提升，而非時鐘拉伸

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t6d9la/9700_pro_users_undervolting_nets_crazy_clocks/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

During my burn tests for my llm's, managed to snag 4ghz boost and 3.72ghz sustained (obviously not stable, very far from it) but heard from a birdy that last week's drivers for these cards fully unlock new vulkan paths and allowed unlocked clocks. This is a god bin yes but more users are reporting large boost in clocks aswell. Daily clocks now are 3.3-3.58ghz at 225 watts limit. Undervolting unlocks this. Try it, have fun. Performance is scaling so no, this is not clock stretching. 3.720ghz did not not much more performance, as it was highly unstable but wanted to see what the card can do. 4ghz micro burst on ambient blower cooler is now doable on the 9700's. &#32; submitted by &#32; /u/psychoOC [link] &#32; [comments]

</details>