---
id: inbox_296e401c
date: 2026-07-22
source_ref: "[[00-inbox/.../inbox_296e401c]]"
title: "Presentation: From Copy-Paste to Composition: Building Agents Like Real Software"
url: https://www.infoq.com/presentations/agent-software-engineering/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-22T11:57:00+00:00
fetched_at: 2026-07-24T02:39:19.073910+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Jake Mannix 在 InfoQ presentation 中指出，當前 AI agent 架構仍停留在「1970s BASIC」階段（無序、難以維護），主張引入中間層協議來實現 agent 的版本化、封裝及虛擬工具化。該設計透過動態 schema 投影及 runtime taint tracking 主動消除資料外洩風險，同時不犧牲開發速度。這對工程主管構建可管理、安全、可版本控制的 agent 系統提供明確的架構方向。"
key_points:
  - "引入「中間層協議」讓 AI agents 從無序 copy-paste 架構演進到版本化、可封裝的虛擬工具設計"
  - "動態 schema 投影搭配 runtime taint tracking 主動防止資料外洩，無效能代價"
  - "工程化設計框架使 agent 系統變成可測試、可版本控制的真實軟體而非「膠水代碼」"
tags: [agent-architecture, protocol-design, runtime-security, software-engineering]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: From Copy-Paste to Composition: Building Agents Like Real Software

Jake Mannix 在 InfoQ presentation 中指出，當前 AI agent 架構仍停留在「1970s BASIC」階段（無序、難以維護），主張引入中間層協議來實現 agent 的版本化、封裝及虛擬工具化。該設計透過動態 schema 投影及 runtime taint tracking 主動消除資料外洩風險，同時不犧牲開發速度。這對工程主管構建可管理、安全、可版本控制的 agent 系統提供明確的架構方向。

### 重點
- 引入「中間層協議」讓 AI agents 從無序 copy-paste 架構演進到版本化、可封裝的虛擬工具設計
- 動態 schema 投影搭配 runtime taint tracking 主動防止資料外洩，無效能代價
- 工程化設計框架使 agent 系統變成可測試、可版本控制的真實軟體而非「膠水代碼」

**原文：** [infoq-main](https://www.infoq.com/presentations/agent-software-engineering/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Presentation: From Copy-Paste to Composition: Building Agents Like Real Software

Jake Mannix discusses moving AI agents past chaotic "1970s BASIC" architectures. He shares how implementing an intermediate protocol layer allows engineering leaders to build versioned, encapsulated "virtual tools." This design enables interface mapping, dynamic schema projection, and runtime taint tracking to proactively eliminate data exfiltration risks without slowing velocity. By Jake Mannix

</details>