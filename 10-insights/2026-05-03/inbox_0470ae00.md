---
id: inbox_0470ae00
date: 2026-05-03
source_ref: "[[00-inbox/.../inbox_0470ae00]]"
title: "Context Is the New Code — Patrick Debois, Tessl"
url: https://www.youtube.com/watch?v=bSG9wUYaHWU
source: youtube-ai-engineer
published_at: 2026-05-03T14:00:06+00:00
fetched_at: 2026-05-04T14:10:45.093530+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Tessl 的 Patrick Debois 提出「Context 是新代碼」的核心論點，引入 Context Development Life Cycle 框架，包括 Generate（生成）、Test（測試）、Distribute（分發）、Observe（觀察）四個階段。Patrick 強調應對 Context Evals 進行測試（類似代碼單元測試），並在 CI/CD 系統中運行，使用錯誤預算管理不確定性。講者討論了 Skills、Registry、Agent.md/Claude.md 等可重用上下文，以及 Context Filter 等安全機制。"
key_points:
  - "Context Development Life Cycle：Generate → Test → Distribute → Observe，與傳統 DevOps 類似的循環優化模式"
  - "Context Evals 需在 CI/CD 中運行，使用錯誤預算而非精確測試（因 LLM 非決定性）"
  - "Skills/Registry 機制使上下文可跨項目、跨團隊複用，需處理依賴衝突及安全掃描（如 Snyk）"
tags: [context-driven, prompt-engineering, agent-development, eval-testing, skills-registry]
topics: [agents.mcp]
importance: 5
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Context Is the New Code — Patrick Debois, Tessl

Tessl 的 Patrick Debois 提出「Context 是新代碼」的核心論點，引入 Context Development Life Cycle 框架，包括 Generate（生成）、Test（測試）、Distribute（分發）、Observe（觀察）四個階段。Patrick 強調應對 Context Evals 進行測試（類似代碼單元測試），並在 CI/CD 系統中運行，使用錯誤預算管理不確定性。講者討論了 Skills、Registry、Agent.md/Claude.md 等可重用上下文，以及 Context Filter 等安全機制。

### 重點
- Context Development Life Cycle：Generate → Test → Distribute → Observe，與傳統 DevOps 類似的循環優化模式
- Context Evals 需在 CI/CD 中運行，使用錯誤預算而非精確測試（因 LLM 非決定性）
- Skills/Registry 機制使上下文可跨項目、跨團隊複用，需處理依賴衝突及安全掃描（如 Snyk）

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=bSG9wUYaHWU)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Context Is the New Code — Patrick Debois, Tessl

</details>