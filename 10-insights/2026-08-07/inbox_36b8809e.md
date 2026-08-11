---
id: inbox_36b8809e
date: 2026-08-07
source_ref: "[[00-inbox/.../inbox_36b8809e]]"
title: "Moonlight &amp; Mayhem (Raccoon Heist by Codex + GPT-5.6 Sol Ultra)"
url: https://simonwillison.net/2026/Aug/7/moonlight-mayhem/#atom-everything
source: simon-willison
published_at: 2026-08-07T19:18:09+00:00
fetched_at: 2026-08-11T01:19:12.685667+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 對比 Claude Fable 5 與 GPT-5.6 Sol Ultra 在遊戲開發上的表現，兩者都基於同一則 4 年前的 Raccoon Heist 概念。GPT-5.6 Sol Ultra（激進使用 sub-agents）產出品質更高的遊戲版本：博物館盜竊情節、可堆疊浣熊隊員組隊機制，相比 Fable 5 的單隻浣熊後院遊戲更符合原始「heisty」主題。Codex 耗時 52 分鐘完成此項目。開發過程中發現視覺 bug（浣熊眼球放大成懸浮球體），Codex 未在審視截圖時自動偵測，但用簡單兩步 prompt（「為什麼...？」+「修復」）成功修正。作者提及希望 Claude Code 提供 Codex 的「複製為 Markdown」功能。"
key_points:
  - "GPT-5.6 Sol Ultra 激進使用 sub-agents 產出更符合遊戲設定的結果（博物館堆疊浣熊機制）vs Claude Fable 5（後院收集），視覺創意更豐富"
  - "Codex 耗時 52 分鐘完成全套專案含 gpt-image-2 影像生成；簡潔指向 prompt +修復指令快速解決視覺異常無需重新生成"
  - "Sub-agents 分工策略改善執行品質；人工導向審視反饋（基於截圖提示修正）有效性高於自動檢測"
tags: [gpt-5.6-sol-ultra, claude-fable-5, sub-agents, game-development, codex]
topics: [foundation_models.claude, foundation_models.gpt]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Moonlight & Mayhem (Raccoon Heist by Codex + GPT-5.6 Sol Ultra)

Simon Willison 對比 Claude Fable 5 與 GPT-5.6 Sol Ultra 在遊戲開發上的表現，兩者都基於同一則 4 年前的 Raccoon Heist 概念。GPT-5.6 Sol Ultra（激進使用 sub-agents）產出品質更高的遊戲版本：博物館盜竊情節、可堆疊浣熊隊員組隊機制，相比 Fable 5 的單隻浣熊後院遊戲更符合原始「heisty」主題。Codex 耗時 52 分鐘完成此項目。開發過程中發現視覺 bug（浣熊眼球放大成懸浮球體），Codex 未在審視截圖時自動偵測，但用簡單兩步 prompt（「為什麼...？」+「修復」）成功修正。作者提及希望 Claude Code 提供 Codex 的「複製為 Markdown」功能。

### 重點
- GPT-5.6 Sol Ultra 激進使用 sub-agents 產出更符合遊戲設定的結果（博物館堆疊浣熊機制）vs Claude Fable 5（後院收集），視覺創意更豐富
- Codex 耗時 52 分鐘完成全套專案含 gpt-image-2 影像生成；簡潔指向 prompt +修復指令快速解決視覺異常無需重新生成
- Sub-agents 分工策略改善執行品質；人工導向審視反饋（基於截圖提示修正）有效性高於自動檢測

**原文：** [simon-willison](https://simonwillison.net/2026/Aug/7/moonlight-mayhem/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Moonlight & Mayhem (Raccoon Heist by Codex + GPT-5.6 Sol Ultra)

Moonlight &amp; Mayhem (Raccoon Heist by Codex + GPT-5.6 Sol Ultra) 
On Wednesday I wrote about One-shotting a Raccoon Heist game using Claude Fable 5 , where I had Claude Fable 5 build a full working game from a premise I generated with GPT-3 and DALL-E four years ago . 
 I decided to pose the exact same prompt to Codex Desktop running GPT-5.6 Sol Ultra - the mode where Sol makes aggressive use of sub-agents - to see how it would do. 
 It produced a much better game! Here's Moonlight &amp; Mayhem - GitHub repository here , including the textures and prompts it generated using gpt-image-2 . 
 
 
 Your browser does not support HTML5 video.
 
 

 The original GPT-3 generated game description included: 
 
 In “Raccoon Heist”, you and your team of thieving raccoons are tasked with pulling off a series of daring heists. From robbing banks to stealing priceless art, no job is too big or too small for your furry crew. 
 
 Fable's version had you as a single raccoon running around a back yard collecting coins and fish. GPT-5.6 Sol has you in a museum, rescuing your two other raccoon crewmates in order to stack on top of each other and bust the golden sardine out of its case. 
 Much more heisty! 
 There was one catch though: the version produced from the one-shot prompt had a bug where each raccoon had an eyeball that was enlarged to the size of a giant sphere floating over their head! 
 
 You can play that version here . 
 Despite reviewing screenshots during development Codex failed to spot and correct this bug. 
 I fixed it by prompting: 
 
 Why do the raccoons have huge black spheres on them? 
 
 And then: 
 
 Fix it 
 
 Which resulted in this fix . 
 I shared the full Codex transcript in the repository - I wish Claude Code had the same "copy as Markdown" feature. 
 Codex spent 52 minutes on the project. Here's the AgentsView cost estimate for that session if I had been paying full API prices as opposed to using my monthly Codex subscription: 
 

 Tags: game-design , ai , openai , generative-ai , llms , coding-agents , codex , gpt

</details>