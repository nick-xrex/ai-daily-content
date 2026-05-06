---
id: inbox_dcda80f1
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_dcda80f1]]"
title: "DeepSeek V4 being 17x cheaper got me to actually measure what I send to cloud vs what I could run locally. the results are stupid."
url: https://www.reddit.com/r/LocalLLaMA/comments/1t4s6g2/deepseek_v4_being_17x_cheaper_got_me_to_actually/
source: reddit-localllama
published_at: 2026-05-05T20:55:56+00:00
fetched_at: 2026-05-06T13:38:45.271833+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者通過測量 10 天的實際編碼工作流發現，65% 的日常任務用本地 Qwen 3.6 27B（3090 GPU）達成 97% 或 88% 的相符率，只有 15% 的工作（架構決策、複雜重構）確實需要雲端模型。具體而言，檔案閱讀和解釋代碼時本地達成 97% 匹配率（35% 工作量），測試編寫達成 88%（30% 工作量），但多檔案除錯時本地只有 61%。採用分類路由策略後，API 帳單從 $85/月降至 $22/月，揭示大多數開發者盲目過度使用雲端模型。"
key_points:
  - "65% 日常編碼工作在本地模型上達 97%-88% 相符率；API 成本從 $85/月降至 $22/月"
  - "任務分類：簡單任務（檔案讀取、單檔編輯）本地足夠；複雜任務（多檔除錯 61%、架構決策 29%）才需雲端"
  - "核心模式：按任務複雜度分類部署比盲目使用雲端便宜 4 倍"
tags: [local-inference, cost-optimization, model-routing, qwen, deepseek]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## DeepSeek V4 being 17x cheaper got me to actually measure what I send to cloud vs what I could run locally. the results are stupid.

開發者通過測量 10 天的實際編碼工作流發現，65% 的日常任務用本地 Qwen 3.6 27B（3090 GPU）達成 97% 或 88% 的相符率，只有 15% 的工作（架構決策、複雜重構）確實需要雲端模型。具體而言，檔案閱讀和解釋代碼時本地達成 97% 匹配率（35% 工作量），測試編寫達成 88%（30% 工作量），但多檔案除錯時本地只有 61%。採用分類路由策略後，API 帳單從 $85/月降至 $22/月，揭示大多數開發者盲目過度使用雲端模型。

### 重點
- 65% 日常編碼工作在本地模型上達 97%-88% 相符率；API 成本從 $85/月降至 $22/月
- 任務分類：簡單任務（檔案讀取、單檔編輯）本地足夠；複雜任務（多檔除錯 61%、架構決策 29%）才需雲端
- 核心模式：按任務複雜度分類部署比盲目使用雲端便宜 4 倍

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t4s6g2/deepseek_v4_being_17x_cheaper_got_me_to_actually/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# DeepSeek V4 being 17x cheaper got me to actually measure what I send to cloud vs what I could run locally. the results are stupid.

<!-- SC_OFF --><div class="md"><p>That foodtruck bench post showing deepseek v4 matching gpt-5.2 at 17x cheaper got me thinking. if frontier cloud models are that overpriced for equivalent quality, how much of my daily work even needs cloud at all?</p> <p>Ran my normal coding workflow for 10 days. every task got logged: what it was, tokens in/out, whether local qwen 3.6 27b (on a 3090) could have done it. didn't use benchmarks, just re-ran a random sample of 150 tasks on both.</p> <p>results:</p> <p>- file reads, project scanning, &quot;explain this code&quot;: local matched cloud 97% of the time. this was 35% of my workload. paying for cloud here is genuinely throwing money away.</p> <p>- test writing, boilerplate, single file edits: local matched 88%. another 30% of tasks. the 12% misses were edge cases i could catch in review.</p> <p>- debugging with multi-file context: local dropped to 61%. cloud still better but not 17x-the-price better. about 20% of my work.</p> <p>- architecture decisions, complex refactors across 5+ files: local at 29%. cloud genuinely needed here. only 15% of my tasks.</p> <p>So 65% of my daily coding work runs identically on a model that costs me electricity. another 20% is close enough that I accept the occasional miss. only 15% actually justifies cloud pricing.</p> <p>Started routing by task type. local for the first two buckets, cloud for the last two. my api bill went from $85/month to about $22 and the 3090 was already sitting there mining nothing.</p> <p>The deepseek post is right that the price gap is insane but the bigger insight is that most of us don't even need cloud for most of what we do. we're just too lazy to measure it.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/spencer_kw"> /u/spencer_kw </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4s6g2/deepseek_v4_being_17x_cheaper_got_me_to_actually/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4s6g2/deepseek_v4_being_17x_cheaper_got_me_to_actually/">[comments]</a></span>

</details>