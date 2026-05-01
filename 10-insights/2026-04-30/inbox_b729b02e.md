---
id: inbox_b729b02e
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-infoq-architecture-cloudflare-announces-agent-memory-a-mana-3ba4]]"
title: "Cloudflare Announces Agent Memory, a Managed Persistent Memory Service for AI Agents"
url: https://www.infoq.com/news/2026/04/cloudflare-agent-memory-beta/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-04-30T10:10:00+00:00
fetched_at: 2026-05-01T13:12:35.432230+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 宣布 Agent Memory 服務進入私密測試，這是一項專為 AI agent 設計的託管持久記憶服務。系統從 agent 對話中提取結構化記憶，透過五通道並行檢索與 Reciprocal Rank Fusion（RRF）融合結果，確保檢索準確度。支援共享記憶檔案機制，讓多個 agent 存取共同知識庫。市場競爭者包括 Mem0、Zep、LangMem 和 Letta，表明該領域快速成熟。此服務針對需要長期上下文保留與多 agent 協作的應用場景。"
key_points:
  - "五通道並行檢索 + Reciprocal Rank Fusion，提升記憶檢索準確度與相關性"
  - "共享記憶檔案機制，支援多 agent 協作與共同知識存取"
  - "競爭格局明朗：Mem0、Zep、LangMem、Letta 等五家玩家，市場邁向標準化"
tags: [cloudflare, agent-memory, ai-agents, rag, persistent-memory]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Announces Agent Memory, a Managed Persistent Memory Service for AI Agents

Cloudflare 宣布 Agent Memory 服務進入私密測試，這是一項專為 AI agent 設計的託管持久記憶服務。系統從 agent 對話中提取結構化記憶，透過五通道並行檢索與 Reciprocal Rank Fusion（RRF）融合結果，確保檢索準確度。支援共享記憶檔案機制，讓多個 agent 存取共同知識庫。市場競爭者包括 Mem0、Zep、LangMem 和 Letta，表明該領域快速成熟。此服務針對需要長期上下文保留與多 agent 協作的應用場景。

### 重點
- 五通道並行檢索 + Reciprocal Rank Fusion，提升記憶檢索準確度與相關性
- 共享記憶檔案機制，支援多 agent 協作與共同知識存取
- 競爭格局明朗：Mem0、Zep、LangMem、Letta 等五家玩家，市場邁向標準化

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/04/cloudflare-agent-memory-beta/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/04/cloudflare-agent-memory-beta/en/headerimage/generatedHeaderImage-1777209282399.jpg" /><p>Cloudflare announced Agent Memory in private beta, a managed service that extracts structured memories from AI agent conversations and retrieves them on demand using five-channel parallel retrieval with Reciprocal Rank Fusion. Shared memory profiles let teams of agents access common knowledge. Competitors include Mem0, Zep, LangMem, and Letta.</p> <i>By Steef-Jan Wiggers</i>

</details>