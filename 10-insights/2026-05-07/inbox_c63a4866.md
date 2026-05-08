---
id: inbox_c63a4866
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-claudeai-things-i-wish-i-knew-earlier-about-claud-91a5]]"
title: "Things I wish I knew earlier about Claude token usage"
url: https://www.reddit.com/r/ClaudeAI/comments/1t6asgc/things_i_wish_i_knew_earlier_about_claude_token/
source: reddit-claudeai
published_at: 2026-05-07T13:36:35+00:00
fetched_at: 2026-05-08T08:11:13.754954+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者分享 Claude 代幣使用最佳化心法，發現大部分代幣消耗非來自模型答覆而是上下文設置。核心技巧包括：(1) 不相關任務開啟新對話，避免長對話重複傳送完整歷史；(2) 將多個小問題合併成一條訊息，減少重複的上下文加載；(3) 保持 CLAUDE.md 簡潔，改為索引指向相關檔案，每回合模型都會重讀此檔案；(4) 精確指定檔案引用而非傳全部代碼，節省 30–50k 代幣探索成本；(5) 每 15–20 訊息後要求摘要並在新對話重啟；(6) 針對輕度工作（草稿、重新格式化、解釋）使用更輕量的模型。這些實踐來自使用者數周的觀察與測試。"
key_points:
  - "長對話重複傳送完整歷史是主要代幣消耗源；40 訊息的對話會在已不相關的 20 訊息前內容上燒錄代幣"
  - "精確的檔案引用（指向單一函數而非整個代碼庫）可省 30–50k 代幣的盲目探索"
  - "輕量模型分流（草稿、重新格式化、解釋）可節省大模型的配額；CLAUDE.md 每回合都被重讀，應維持簡潔索引形式"
tags: [token-optimization, claude-usage, context-management, cost-reduction, workflow-tips]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Things I wish I knew earlier about Claude token usage

使用者分享 Claude 代幣使用最佳化心法，發現大部分代幣消耗非來自模型答覆而是上下文設置。核心技巧包括：(1) 不相關任務開啟新對話，避免長對話重複傳送完整歷史；(2) 將多個小問題合併成一條訊息，減少重複的上下文加載；(3) 保持 CLAUDE.md 簡潔，改為索引指向相關檔案，每回合模型都會重讀此檔案；(4) 精確指定檔案引用而非傳全部代碼，節省 30–50k 代幣探索成本；(5) 每 15–20 訊息後要求摘要並在新對話重啟；(6) 針對輕度工作（草稿、重新格式化、解釋）使用更輕量的模型。這些實踐來自使用者數周的觀察與測試。

### 重點
- 長對話重複傳送完整歷史是主要代幣消耗源；40 訊息的對話會在已不相關的 20 訊息前內容上燒錄代幣
- 精確的檔案引用（指向單一函數而非整個代碼庫）可省 30–50k 代幣的盲目探索
- 輕量模型分流（草稿、重新格式化、解釋）可節省大模型的配額；CLAUDE.md 每回合都被重讀，應維持簡潔索引形式

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t6asgc/things_i_wish_i_knew_earlier_about_claude_token/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A few weeks ago, I shared some tips on my Claude Code workflow. In the comments, quite a few people mentioned that they were burning through their tokens super fast and tbh I could totally relate. This is something I particularly struggled with at the beginning, which pushed me to take a closer look at it. Turns out most of my token usage wasn't coming from Claude's answers, but from the setup. Things I actually use: Start a new chat for unrelated tasks. Every message in a long conversation resends the full history. That's not obvious until I realize a 40-message thread is burning tokens on context I stopped caring about 20 messages ago. Group your small questions into one message. Sending three quick follow-ups instead of one combined message means three full context loads. I group them now and it adds up fast. Keep your CLAUDE.md short and use it as an index. I used to dump everything in there. The problem is Claude rereads it every single turn. Now it points to separate files and only loads what's relevant to the task. Things I try to implement as much as possible: Be precise with file references. I used to say &quot;here's the whole codebase, figure it out.&quot; Claude would spend 30-50k tokens just exploring before doing anything useful. Now I point it at the one function or module that actually matters. Summarize and restart after 15-20 messages. I ask Claude for a quick summary of where things stand, paste it into a fresh thread. I lose nothing and stop dragging dead context around. Use lighter models for lighter work. Not everything needs the heaviest model. Drafting, reformatting, explaining. I route those elsewhere and save the big model for the reasoning-heavy stuff. What are your go-to tricks for keeping usage under control? &#32; submitted by &#32; /u/Marmelab [link] &#32; [comments]

</details>