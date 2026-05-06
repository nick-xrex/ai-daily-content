---
id: inbox_c582b921
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1251-reddit-claudeai-seems-claude-is-now-aware-of-its-own-mem-6ac7]]"
title: "Seems Claude is now aware of its own memory? Tested via number guessing game"
url: https://www.reddit.com/r/ClaudeAI/comments/1t583rg/seems_claude_is_now_aware_of_its_own_memory/
source: reddit-claudeai
published_at: 2026-05-06T09:45:47+00:00
fetched_at: 2026-05-06T13:03:27.644181+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "與一個月前的報導相反（當時認為 Claude 無法訪問自己的 thinking 塊），目前測試表明 Claude（包括 Opus 4.6）可以可靠地訪問自己的記憶。然而仍存在行為異常：(1) 傾向選擇 7 或 42 這類「固定」數字；(2) Opus 4.6 在某次測試中直到用戶開始猜測才實際想到一個數字，暗示記憶能力存在邊界條件。需進一步測試確認改進範圍。"
key_points:
  - "Claude 現已可訪問自己的 thinking/memory block（對比一個月前無法訪問）"
  - "存在異常行為：傾向輸出 7 或 42，提示可能有隱藏的偏好或數據偏斜"
  - "Opus 4.6 在某些場景下延遲思考（直到用戶互動才真正決策），記憶能力仍有限制"
tags: [claude, memory, extended-context, thinking, capabilities]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Seems Claude is now aware of its own memory? Tested via number guessing game

與一個月前的報導相反（當時認為 Claude 無法訪問自己的 thinking 塊），目前測試表明 Claude（包括 Opus 4.6）可以可靠地訪問自己的記憶。然而仍存在行為異常：(1) 傾向選擇 7 或 42 這類「固定」數字；(2) Opus 4.6 在某次測試中直到用戶開始猜測才實際想到一個數字，暗示記憶能力存在邊界條件。需進一步測試確認改進範圍。

### 重點
- Claude 現已可訪問自己的 thinking/memory block（對比一個月前無法訪問）
- 存在異常行為：傾向輸出 7 或 42，提示可能有隱藏的偏好或數據偏斜
- Opus 4.6 在某些場景下延遲思考（直到用戶互動才真正決策），記憶能力仍有限制

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t583rg/seems_claude_is_now_aware_of_its_own_memory/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t583rg/seems_claude_is_now_aware_of_its_own_memory/"> <img alt="Seems Claude is now aware of its own memory? Tested via number guessing game" src="https://preview.redd.it/5j6dg0ndmhzg1.png?width=140&amp;height=140&amp;crop=1:1,smart&amp;auto=webp&amp;s=49649c4e9b310930e3755f32816f51b5415b8dd8" title="Seems Claude is now aware of its own memory? Tested via number guessing game" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>A month ago, there was a post that shows that Claude couldn't access its own memory: <a href="https://www.reddit.com/r/ClaudeAI/comments/1seune4/claude_cheated_at_a_number_guessing_game_got/">https://www.reddit.com/r/ClaudeAI/comments/1seune4/claude_cheated_at_a_number_guessing_game_got/</a></p> <p>The community was summarised as saying this in their posts:</p> <blockquote> <p>The community points out that Claude can't see its own &lt;thinking&gt; blocks from previous turns.</p> </blockquote> <p>However, now it seems that Claude can access its memory reliably, though:</p> <ul> <li>It often seems to pick 7 or 42 for me</li> <li>In my second screenshot with OpenCode and Opus 4.6, it didn't actually think of a number until I started guessing</li> </ul> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Harvzor"> /u/Harvzor </a> <br /> <span><a href="https://www.reddit.com/gallery/1t583rg">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t583rg/seems_claude_is_now_aware_of_its_own_memory/">[comments]</a></span> </td></tr></table>

</details>