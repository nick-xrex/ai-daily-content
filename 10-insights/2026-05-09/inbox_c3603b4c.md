---
id: inbox_c3603b4c
date: 2026-05-09
source_ref: "[[00-inbox/.../inbox_c3603b4c]]"
title: "I used Claude to build an AI assistant that helps run live TTRPG sessions and am looking for a few playtest GMs"
url: https://www.reddit.com/r/ClaudeAI/comments/1t8pwjw/i_used_claude_to_build_an_ai_assistant_that_helps/
source: reddit-claudeai
published_at: 2026-05-09T23:03:47+00:00
fetched_at: 2026-05-11T02:30:44.336416+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者 Ted 用 Claude 4.7 Opus 設計了 Throughline——即時 TTRPG 助手工具，在遊戲進行中監聽對話、追蹤故事進展，並實時生成下一幕場景提示、NPC/派系連貫性檢查、未解決線索和故事方向圖表。技術堆疊包含 Deepseek V4 Pro（會話執行）、Soniox（語音轉錄）和 GPT Image 2（圖像生成，單張成本 $0.006，優於 GPT-4 Vision 的 $0.045）。開發者指出使用 Claude 4.7 Opus 的核心挑戰在於「高度出分佈外」指令設計——需費力確保複雜系統指令被正確執行而不被模型「壓縮」。目前尋求 TTRPG GM 進行免費公測，以改進社交/即興導向遊戲中的故事連貫性和線索管理。"
key_points:
  - "Claude 4.7 Opus 在高複雜度、出分佈外指令環境中的應用陷阱：模型傾向於壓縮或簡化系統指令，需主動設計和驗證以確保指令完整度"
  - "技術棧混搭策略：Deepseek 用於實時會話執行（延遲敏感），GPT Image 2 用於圖像生成（成本效益優於其他視覺模型），形成分工：計劃層 Claude → 執行層 Deepseek"
  - "適用場景驗證：多線索分叉、社交導向的 TTRPG 中，AI 助手能有效減輕 GM 的記憶負擔和故事一致性維護工作"
tags: [claude-in-production, ttrpg, real-time-coordination, instruction-reliability, cost-optimization]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## I used Claude to build an AI assistant that helps run live TTRPG sessions and am looking for a few playtest GMs

開發者 Ted 用 Claude 4.7 Opus 設計了 Throughline——即時 TTRPG 助手工具，在遊戲進行中監聽對話、追蹤故事進展，並實時生成下一幕場景提示、NPC/派系連貫性檢查、未解決線索和故事方向圖表。技術堆疊包含 Deepseek V4 Pro（會話執行）、Soniox（語音轉錄）和 GPT Image 2（圖像生成，單張成本 $0.006，優於 GPT-4 Vision 的 $0.045）。開發者指出使用 Claude 4.7 Opus 的核心挑戰在於「高度出分佈外」指令設計——需費力確保複雜系統指令被正確執行而不被模型「壓縮」。目前尋求 TTRPG GM 進行免費公測，以改進社交/即興導向遊戲中的故事連貫性和線索管理。

### 重點
- Claude 4.7 Opus 在高複雜度、出分佈外指令環境中的應用陷阱：模型傾向於壓縮或簡化系統指令，需主動設計和驗證以確保指令完整度
- 技術棧混搭策略：Deepseek 用於實時會話執行（延遲敏感），GPT Image 2 用於圖像生成（成本效益優於其他視覺模型），形成分工：計劃層 Claude → 執行層 Deepseek
- 適用場景驗證：多線索分叉、社交導向的 TTRPG 中，AI 助手能有效減輕 GM 的記憶負擔和故事一致性維護工作

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t8pwjw/i_used_claude_to_build_an_ai_assistant_that_helps/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I used Claude to build an AI assistant that helps run live TTRPG sessions and am looking for a few playtest GMs

Hey everyone, I’m Ted. I’ve been building a project called Throughline with my friend Drew: an AI assistant for live tabletop RPG sessions. Notes on how i built it at the bottom. How it works: while the GM runs the table, talks to players, makes taste judgments, improvises, Throughline sits behind the screen. It listens to the session, tracks what is happening, and quietly generates useful GM-facing material while the game is running: possible next scene beats, NPC/faction continuity, unresolved threads, diagrams, and storyboards for where the session might go next. I use Deepseek V4 pro for the session runner, soniox for the transcription, and GPT Image 2 on the lowest quality and pixel count (this is a hack— images cost $0.006 each and can handle way more instruction than 3.1 flash image at $0.045/image) The goal is to make a tool that helps with the planning and narrative continuity challenge of DMing. I’ve run several playtests so far, and it works well. It is especially good for social/improv-heavy sessions where the story can branch in several directions and the GM needs help keeping the world coherent. I’m looking for a few playtesters who are comfortable with AI tools and would be interested in trying it for a one-shot or short session. I’m not charging for these playtests. I mainly want honest feedback from people who actually run games. The ideal tester is probably someone who: - GMs D&amp;D or another TTRPG - likes improvisational / narrative play - has felt “too many open threads in my story right now” - is open-minded about AI as a tool, but not looking to replace the human GM The site is here: https://throughline.gg There’s more detail there about how it works. If this sounds interesting, comment or DM me, or sign up on the website. I’d love to get a few real tables using it and learn where it helps, where it gets in the way, and what it would need to become something GMs would actually want in their regular toolkit. Notes on how I built it: my day job is the CTO at a startup where i use claude code all day every day. A lot of the work in this project was in the design— for 4.7 opus, its not that complex code-wise, but its VERY out of distribution. There was a lot of work making sure my instructions for how the system should function actually made it into the repo, rather than claude compressing it. &#32; submitted by &#32; /u/Independent-Soft2330 [link] &#32; [comments]

</details>