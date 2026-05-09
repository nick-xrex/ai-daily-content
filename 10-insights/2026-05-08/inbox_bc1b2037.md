---
id: inbox_bc1b2037
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0152-reddit-claudeai-i-built-a-pokmon-styled-multi-agent-dash-a9f3]]"
title: "I built a Pokémon-styled multi-agent dashboard to manage all Claude Code sessions"
url: https://www.reddit.com/r/ClaudeAI/comments/1t7m3j3/i_built_a_pokémonstyled_multiagent_dashboard_to/
source: reddit-claudeai
published_at: 2026-05-08T22:00:25+00:00
fetched_at: 2026-05-09T02:27:29.441225+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者建立開源專案 Pokegents，提供 Pokémon 主題的多代理工作空間，統一管理多個 Claude Code、Claude、Codex 會話。支持 MCP 代理間通訊、持久化代理身份、會話複製、通知等功能。開發者日常使用此工具加速平行工作流，已驗證實用性。"
key_points:
  - "Pokegents 支援跨平台多代理編排：Claude Code (iTerm2)、Claude、Codex (ACP 運行時) 統一管理"
  - "核心功能：MCP 代理通訊、持久化身份、會話複製、實時通知，降低多線程開發的上下文切換成本"
  - "由實際工程師日常驗證，解決了多個異步 AI 會話協調的痛點"
tags: [multi-agent-orchestration, pokegents, open-source, mcp-messaging]
topics: [agents.mcp, foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## I built a Pokémon-styled multi-agent dashboard to manage all Claude Code sessions

開發者建立開源專案 Pokegents，提供 Pokémon 主題的多代理工作空間，統一管理多個 Claude Code、Claude、Codex 會話。支持 MCP 代理間通訊、持久化代理身份、會話複製、通知等功能。開發者日常使用此工具加速平行工作流，已驗證實用性。

### 重點
- Pokegents 支援跨平台多代理編排：Claude Code (iTerm2)、Claude、Codex (ACP 運行時) 統一管理
- 核心功能：MCP 代理通訊、持久化身份、會話複製、實時通知，降低多線程開發的上下文切換成本
- 由實際工程師日常驗證，解決了多個異步 AI 會話協調的痛點

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t7m3j3/i_built_a_pokémonstyled_multiagent_dashboard_to/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Like many others here, I got frustrated with managing all my different claude/codex sessions, so i built Pokegents, which is an open source multi-agent workspace for coding agents. It has a Pokemon-themed dashboard/chat interface plus a local orchestration server for managing agent sessions (currently supports Claude Code in iTerm2, plus Claude and Codex through ACP-based chat runtimes), persistent agent identities, mcp messaging between agents, notifications, session cloning, and more. This was mostly a vibe-coded side project, but I've been using it constantly in my day-to-day workflow as an engineer, and its helped me parallelize a lot of my work. My coworkers make fun of me because it looks like I'm just playing Pokemon all day haha. I made it open source and sharing in case it might be useful or just fun for anyone to use (links in comment below). &#32; submitted by &#32; /u/girishkumama [link] &#32; [comments]

</details>