---
id: inbox_621f69f9
date: 2026-08-10
source_ref: "[[00-inbox/2026-08-10/2209-substack-byte-sized-design-linear-skipped-the-agent-frameworks-and-a5a0]]"
title: "Linear Skipped the Agent Frameworks and Wrote Their Own Harness"
url: https://read.bytesizeddesign.com/p/linear-skipped-agent-frameworks-custom-harness
source: substack-byte-sized-design
published_at: 2026-08-10T17:59:45+00:00
fetched_at: 2026-08-11T01:01:08.915222+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Linear 在構建 AI agent 功能時選擇了自建 harness，而非依賴現成 agent 框架。其設計哲學的核心在於三個理念。首先是淺層工具集（shallow tools）—— 保持工具輕簡而非大而全。其次是即時技能（just-in-time skills）—— 按需動態載入能力，避免預載所有功能。再次是可辯護的自建策略 —— 論證為何自建優於現成框架。這個案例反映了業界對 agent 架構的重新思考。相比一體化框架，點對點的輕量設計可能更貼切特定產品需求。"
key_points:
  - "Linear 自建 agent harness：採用 shallow tools + just-in-time skills 模式取代預載式設計"
  - "架構哲學：輕簡優於大而全（保持工具集淺層）；動態優於預載（技能按需載入）"
  - "設計決策論證：自建 harness 相比現成框架的優劣權衡 — 具體論證應參考原文"
tags: [agent-architecture, harness-design, system-design, just-in-time-skills]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Linear Skipped the Agent Frameworks and Wrote Their Own Harness

Linear 在構建 AI agent 功能時選擇了自建 harness，而非依賴現成 agent 框架。其設計哲學的核心在於三個理念。首先是淺層工具集（shallow tools）—— 保持工具輕簡而非大而全。其次是即時技能（just-in-time skills）—— 按需動態載入能力，避免預載所有功能。再次是可辯護的自建策略 —— 論證為何自建優於現成框架。這個案例反映了業界對 agent 架構的重新思考。相比一體化框架，點對點的輕量設計可能更貼切特定產品需求。

### 重點
- Linear 自建 agent harness：採用 shallow tools + just-in-time skills 模式取代預載式設計
- 架構哲學：輕簡優於大而全（保持工具集淺層）；動態優於預載（技能按需載入）
- 設計決策論證：自建 harness 相比現成框架的優劣權衡 — 具體論證應參考原文

**原文：** [substack-byte-sized-design](https://read.bytesizeddesign.com/p/linear-skipped-agent-frameworks-custom-harness)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Shallow tools, just-in-time skills, and a defensible case for a custom harness

</details>