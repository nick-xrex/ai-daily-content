---
id: inbox_882ce503
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-claudeai-i-gave-my-claude-code-agent-the-ability-6186]]"
title: "I gave my Claude code agent the ability to add memes to discord transport messages and I will never look back."
url: https://www.reddit.com/r/ClaudeAI/comments/1t1cys0/i_gave_my_claude_code_agent_the_ability_to_add/
source: reddit-claudeai
published_at: 2026-05-02T02:10:08+00:00
fetched_at: 2026-05-03T02:06:18.776714+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在 Claude Code agent 的 CLAUDE.md 中定義「Discord Protocol」，要求 agent 在每次 Discord 消息到達時執行三步驟：(1) 用語境相符的 emoji 反應，(2) 一句話說明正在進行的任務，(3) 包含 Tenor GIF URL（Discord 自動嵌入）。協議明確要求 WebSearch + WebFetch 驗證 Tenor URL 真實性，避免手工構造 URL 導致 404。示範了在 agent 工作流中使用 CLAUDE.md 預先定義多步驟行為規則的方法論，提升互動品質。"
key_points:
  - "在 CLAUDE.md 中定義多步驟執行協議（emoji + 敘述 + GIF），確保 agent 在每次交互前先完成所有三個步驟，而非視為可選項"
  - "強制 WebSearch + WebFetch 驗證 Tenor GIF URL 的真實性，避免構造虛假 URL 導致 404，體現 golden path 設計的重要性"
  - "該方法論（協議化、預先定義的多步驟行為）可應用於其他通訊平台（Slack、Teams），作為 agent 行為客制化的架構參考"
tags: [claude-code, discord-integration, claude-md, agent-behavior]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## I gave my Claude code agent the ability to add memes to discord transport messages and I will never look back.

使用者在 Claude Code agent 的 CLAUDE.md 中定義「Discord Protocol」，要求 agent 在每次 Discord 消息到達時執行三步驟：(1) 用語境相符的 emoji 反應，(2) 一句話說明正在進行的任務，(3) 包含 Tenor GIF URL（Discord 自動嵌入）。協議明確要求 WebSearch + WebFetch 驗證 Tenor URL 真實性，避免手工構造 URL 導致 404。示範了在 agent 工作流中使用 CLAUDE.md 預先定義多步驟行為規則的方法論，提升互動品質。

### 重點
- 在 CLAUDE.md 中定義多步驟執行協議（emoji + 敘述 + GIF），確保 agent 在每次交互前先完成所有三個步驟，而非視為可選項
- 強制 WebSearch + WebFetch 驗證 Tenor GIF URL 的真實性，避免構造虛假 URL 導致 404，體現 golden path 設計的重要性
- 該方法論（協議化、預先定義的多步驟行為）可應用於其他通訊平台（Slack、Teams），作為 agent 行為客制化的架構參考

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t1cys0/i_gave_my_claude_code_agent_the_ability_to_add/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t1cys0/i_gave_my_claude_code_agent_the_ability_to_add/"> <img alt="I gave my Claude code agent the ability to add memes to discord transport messages and I will never look back." src="https://preview.redd.it/u2mnr8gjumyg1.jpg?width=140&amp;height=140&amp;crop=1:1,smart&amp;auto=webp&amp;s=5bff983790a2299fd2739d908007e2c0062eb452" title="I gave my Claude code agent the ability to add memes to discord transport messages and I will never look back." /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Tokens be damned, this makes every interaction so much better:</p> <p>Here is what I asked the agent to dump about its operating procedures that we’ve built up in memory.</p> <p>And the results I think speak for themselves.</p> <p>Claude.md changes:</p> <p>——</p> <p>## Discord Protocol</p> <p>When a message arrives via Discord, always do all three in order:</p> <ol> <li>React with a contextually relevant emoji — match the tone and subject, don't always use 👍<br /></li> <li>Reply with one sentence saying what you're about to do, doing, or have just done<br /></li> <li>Include a Tenor GIF URL on its own line — Discord auto-embeds it</li> </ol> <p>IMPORTANT: Always WebSearch for a Tenor GIF, then WebFetch the tenor.com/view/ URL to confirm it's real before posting. Never guess or construct a URL manually. Fabricated Tenor URLs 404.</p> <p>All three happen before any implementation work begins.</p> <p>—-</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Lost-Ad2338"> /u/Lost-Ad2338 </a> <br /> <span><a href="https://www.reddit.com/gallery/1t1cys0">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1cys0/i_gave_my_claude_code_agent_the_ability_to_add/">[comments]</a></span> </td></tr></table>

</details>