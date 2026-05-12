---
id: inbox_f0904fcf
date: 2026-05-11
source_ref: "[[00-inbox/.../inbox_f0904fcf]]"
title: "First MCPs, then Skills, now Memories are next"
url: https://www.reddit.com/r/ClaudeAI/comments/1t9p54q/first_mcps_then_skills_now_memories_are_next/
source: reddit-claudeai
published_at: 2026-05-11T01:35:41+00:00
fetched_at: 2026-05-12T01:40:58.788416+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者評論Anthropic的MCPs → Skills → Memories演進路線，提出分散系統問題應用於多agent coordination的深層思考。具體問題包括：(1)當多個agent並行運作時，如何防止「踩腳」(concurrent write conflicts)；(2)哪些分散系統演算法（logical clocks邏輯時鐘、consensus共識、deduplication去重、idempotency冪等性、eventual vs causal consistency最終一致性 vs 因果一致性）被應用；(3)與Karpathy wiki、Serena、SQLite databases等記憶系統的設計是否遵循這些模式。貼文暗示Anthropic工程團隊在設計多agent系統時，應已面臨並解決了分散系統的經典問題。"
key_points:
  - "MCPs → Skills → Memories 的演進路線涉及多 agent 並行協調，需應用 logical clocks、consensus、deduplication、idempotency 等分散系統演算法"
  - "Karpathy wiki、Serena、SQLite databases 等外部記憶系統與多 agent coordination 共享設計問題（concurrent writes、eventually-consistent state）"
  - "Memories 功能的核心挑戰是防止並行 agents 在共享狀態上產生衝突，而非單純的持續化"
tags: [distributed-systems, multi-agent-coordination, memory-architecture, consensus-algorithms, mcp-design]
topics: [agents.mcp]
importance: 3
novelty: 4
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## First MCPs, then Skills, now Memories are next

使用者評論Anthropic的MCPs → Skills → Memories演進路線，提出分散系統問題應用於多agent coordination的深層思考。具體問題包括：(1)當多個agent並行運作時，如何防止「踩腳」(concurrent write conflicts)；(2)哪些分散系統演算法（logical clocks邏輯時鐘、consensus共識、deduplication去重、idempotency冪等性、eventual vs causal consistency最終一致性 vs 因果一致性）被應用；(3)與Karpathy wiki、Serena、SQLite databases等記憶系統的設計是否遵循這些模式。貼文暗示Anthropic工程團隊在設計多agent系統時，應已面臨並解決了分散系統的經典問題。

### 重點
- MCPs → Skills → Memories 的演進路線涉及多 agent 並行協調，需應用 logical clocks、consensus、deduplication、idempotency 等分散系統演算法
- Karpathy wiki、Serena、SQLite databases 等外部記憶系統與多 agent coordination 共享設計問題（concurrent writes、eventually-consistent state）
- Memories 功能的核心挑戰是防止並行 agents 在共享狀態上產生衝突，而非單純的持續化

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t9p54q/first_mcps_then_skills_now_memories_are_next/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# First MCPs, then Skills, now Memories are next

This was a really good talk, especially for anyone who's built things like the Karpathy wiki, Serena, or SQLite databases as memory for Claude. For any senior devs out there, are you spotting the solutions already implemented in distributed systems being reused? If many agents are working in parallel, how do you get them from stepping on each others toes? I can imagine logical clocks, consensus, deduplication, idempotency, and eventual vs causal consistency being applied. If you're on the Anthropic team, I'm curious how much different distributed systems algos were experimented with. &#32; submitted by &#32; /u/fsharpman [link] &#32; [comments]

</details>