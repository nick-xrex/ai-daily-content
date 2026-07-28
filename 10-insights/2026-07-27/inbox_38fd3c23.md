---
id: inbox_38fd3c23
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_38fd3c23]]"
title: "An opinionated guide to which AI to use to do stuff"
url: https://simonwillison.net/2026/Jul/27/an-opinionated-guide-to-which-ai-to-use-to-do-stuff/#atom-everything
source: simon-willison
published_at: 2026-07-27T21:55:53+00:00
fetched_at: 2026-07-28T01:17:34.816213+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 剖析 Ethan Mollick 《AI 工具選擇指南》的演變：過去主焦 chat 模式（ChatGPT、Claude、Gemini），今轉向 agent 模式。ChatGPT 提供 Work 與 Codex 雙 agent 模式，Claude 提供 Cowork 與 Code；命名混亂且功能差異大——ChatGPT mobile Work 獨家獲得互聯網訪問，desktop 版本則無。Gemini 因缺乏對標 agent 級競品（Spark 未驗證）而掉隊。此觀點標誌 AI 決策從模型忠誠度轉向 capability 與執行能力。"
key_points:
  - "典範轉移：AI 工具選擇從『chat 模型』(ChatGPT/Claude/Gemini) 升級為『agent 能力』(ChatGPT Work/Codex、Claude Cowork/Code)"
  - "互聯網訪問權限分化：ChatGPT mobile Work 獨有；Codex/Cowork/Code 無此限制；命名極具迷惑性"
  - "Gemini 出局：Google 缺乏建立的 agent 級競品；Spark 尚未驗證市場地位"
tags: [ai-tools, agentic-systems, claude, chatgpt, tool-comparison]
topics: [foundation_models.claude, foundation_models.gpt]
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## An opinionated guide to which AI to use to do stuff

Simon Willison 剖析 Ethan Mollick 《AI 工具選擇指南》的演變：過去主焦 chat 模式（ChatGPT、Claude、Gemini），今轉向 agent 模式。ChatGPT 提供 Work 與 Codex 雙 agent 模式，Claude 提供 Cowork 與 Code；命名混亂且功能差異大——ChatGPT mobile Work 獨家獲得互聯網訪問，desktop 版本則無。Gemini 因缺乏對標 agent 級競品（Spark 未驗證）而掉隊。此觀點標誌 AI 決策從模型忠誠度轉向 capability 與執行能力。

### 重點
- 典範轉移：AI 工具選擇從『chat 模型』(ChatGPT/Claude/Gemini) 升級為『agent 能力』(ChatGPT Work/Codex、Claude Cowork/Code)
- 互聯網訪問權限分化：ChatGPT mobile Work 獨有；Codex/Cowork/Code 無此限制；命名極具迷惑性
- Gemini 出局：Google 缺乏建立的 agent 級競品；Spark 尚未驗證市場地位

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/27/an-opinionated-guide-to-which-ai-to-use-to-do-stuff/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# An opinionated guide to which AI to use to do stuff

An opinionated guide to which AI to use to do stuff 
It's interesting watching the evolution of Ethan Mollick's guide over time. 
 A year ago it was still all about chat - ChatGPT, Claude, Gemini - with o3, Claude 4 Opus, and Gemini 2.5 Pro as the models and Deep Research as a useful alternative mode. 
 Today it's much more about agentic systems - "where the AI is capable of doing the equivalent of many hours of real human work in one go". 
 Gemini has fallen off Ethan's list, since Google still doesn’t have an established entry in the Codex/ChatGPT Work/Cowork category. Gemini Spark has yet to prove itself! 
 Ethan offers a useful explanation of the ways you can give ChatGPT or Claude a computer to use: 
 
 To use the computers provided by the AI companies, the mode you want is called ChatGPT Work in ChatGPT, and Cowork in Claude (the naming will not get less confusing, I am sorry to say). [...] 
 The most powerful way to use AI is to give it access to your computer. You do that by downloading the ChatGPT or Claude apps and picking a mode to use. ChatGPT's two agent modes are Work and Codex; Claude's are Cowork and Code. The names do not map onto each other in any way that will help you remember them. And yes, these use the same names as the Work and Cowork modes we discussed above, but operate differently, and have more features and capabilities because they can access your computer. 
 
 I think the difference between ChatGPT Work on a mobile device and ChatGPT Work inside the desktop app (where it's effectively a less intimidating skin on top of Codex) is spectacularly unintuitive. 
 Short version: if you flip ChatGPT mobile from "Chat" to "Work" mode you get a version where its Code Interpreter container is no longer restricted from accessing the internet!

 Tags: ai , generative-ai , llms , ethan-mollick , code-interpreter , general-agents

</details>