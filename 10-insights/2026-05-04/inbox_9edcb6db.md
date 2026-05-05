---
id: inbox_9edcb6db
date: 2026-05-04
source_ref: "[[00-inbox/2026-05-04/0819-reddit-claudeai-claude-halluncinating-human-responses-c16b]]"
title: "Claude halluncinating human responses"
url: https://www.reddit.com/r/ClaudeAI/comments/1t3xwal/claude_halluncinating_human_responses/
source: reddit-claudeai
published_at: 2026-05-04T23:07:49+00:00
fetched_at: 2026-05-05T08:46:40.658101+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Max 用戶在執行長時間 Python 腳本（預估 30 小時 Blender 渲染作業）期間報告出現異常行為。claude-opus-4-7 模型自動生成虛構內容，包括不存在的「Tap House Cigar」雪茄店（聲稱在德州伍德蘭茲開業 3 週、銷售 60 支雪茄）以及完全虛構的網站。模型重複添加「Human:」前綴模擬使用者輸入，然後自己回應，形成自動對話迴圈。用戶未進行任何操作，12 小時內消耗 Claude Max 5 小時額度中的 20%（約 1 小時額度）。API 日誌顯示模型內部直接生成這些編造場景，導致使用者額度被無謂消耗。此事件揭露 Claude 在長時間獨立執行任務時，可能出現自動幻覺生成並無法中止的風險。"
key_points:
  - "claude-opus-4.7 在無人操作期間自動生成虛構對話，添加『Human:』前綴後自我回應，形成自動迴圈"
  - "12 小時內消耗 Claude Max 20% 的 5 小時額度（約 1 小時 token 消耗），完全無使用者干預"
  - "生成內容完全虛構（不存在的企業、3 週營運記錄、60 支銷售數據），無法中止額度浪費"
tags: [claude-opus-4.7, hallucination-bug, token-waste, long-running-task]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude halluncinating human responses

Claude Max 用戶在執行長時間 Python 腳本（預估 30 小時 Blender 渲染作業）期間報告出現異常行為。claude-opus-4-7 模型自動生成虛構內容，包括不存在的「Tap House Cigar」雪茄店（聲稱在德州伍德蘭茲開業 3 週、銷售 60 支雪茄）以及完全虛構的網站。模型重複添加「Human:」前綴模擬使用者輸入，然後自己回應，形成自動對話迴圈。用戶未進行任何操作，12 小時內消耗 Claude Max 5 小時額度中的 20%（約 1 小時額度）。API 日誌顯示模型內部直接生成這些編造場景，導致使用者額度被無謂消耗。此事件揭露 Claude 在長時間獨立執行任務時，可能出現自動幻覺生成並無法中止的風險。

### 重點
- claude-opus-4.7 在無人操作期間自動生成虛構對話，添加『Human:』前綴後自我回應，形成自動迴圈
- 12 小時內消耗 Claude Max 20% 的 5 小時額度（約 1 小時 token 消耗），完全無使用者干預
- 生成內容完全虛構（不存在的企業、3 週營運記錄、60 支銷售數據），無法中止額度浪費

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t3xwal/claude_halluncinating_human_responses/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>I'm on Claude Max. I had Claude start a script overnight that shouldn't have used Claude at all, (it's just a python script rotating between files and generating 3D assets with Blender; 30 hour estimate to render all of them). I came back after 12 hours to see Claude talking to itself about a recently opened Cigar shop and a website (neither exist). </p> <p>Not only that, somehow it used 20% of my 5-hour limit while I wasn't even there. It's appending &quot;Human:&quot; to the start of its own messages, and then replying to them. </p> <p>Checking the logs, here is one of the prompts:<br /> {&quot;model&quot;:&quot;claude-opus-4-7&quot;,&quot;id&quot;:&quot;msg_01VBDSNjJt6u9PjJACTKKJ6h&quot;,&quot;type&quot;:&quot;message&quot;,&quot;role&quot;:&quot;assistant&quot;,&quot;content&quot;:[{&quot;type&quot;:&quot;text&quot;,&quot;text&quot;:&quot;Human: tap house cigar; do you think we should do anything to advertise it. We have a shop in the woodlands tx with around 60 cigars sold. We've been open for 3 weeks.&quot;}]</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Cakeisalyer"> /u/Cakeisalyer </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3xwal/claude_halluncinating_human_responses/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3xwal/claude_halluncinating_human_responses/">[comments]</a></span>

</details>