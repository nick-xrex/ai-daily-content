---
id: inbox_f8451bc9
date: 2026-05-18
source_ref: "[[00-inbox/2026-05-18/0308-medium-tag-claude-building-deep-agents-skill-md-with-claud-5331]]"
title: "Building Deep Agents + SKILL.md with Claude SDK"
url: https://abvijaykumar.medium.com/building-deep-agents-skill-md-with-claude-sdk-11d8bf47754b?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-18T01:17:58+00:00
fetched_at: 2026-05-18T03:14:07.040008+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "繼續深度智能體系列教程，演示使用 Claude SDK（前稱 Claude Code SDK）搭配 SKILL.md 模式構建完整智能體應用。關鍵創新：SKILL.md 是「特定領域專家手冊」，智能體於需要時才動態加載，保持 context window 潔淨，避免即興演出導致品質波動。提出分層架構：AGENTS.md（專案通用規則）+ SKILL.md（特定任務專家手冊）+ SDK（執行時）。包含完整環境配置指引（uv Python + npm 安裝）與實踐目錄結構（code-reviewer / commit-generator / security-audit 等技能資料夾）。"
key_points:
  - "SKILL.md 按需加載機制：動態載入特定領域技能，避免無謂 context bloat 與品質不穩定（對 PDF/安全審查等特殊任務尤其有效）"
  - "分層架構設計：AGENTS.md (通用規則) + SKILL.md (專家手冊) + SDK (runtime)，讓智能體在清潔 context 下發揮專業能力"
  - "實踐範例：完整的 Python 環境配置 (uv) + .claude 資料夾結構、skill 子資料夾組織、references 與 scripts 配置"
tags: [claude-sdk, deep-agents, skill-md, agent-architecture, context-management]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: true
deep_dive_approved: false
---

## Building Deep Agents + SKILL.md with Claude SDK

繼續深度智能體系列教程，演示使用 Claude SDK（前稱 Claude Code SDK）搭配 SKILL.md 模式構建完整智能體應用。關鍵創新：SKILL.md 是「特定領域專家手冊」，智能體於需要時才動態加載，保持 context window 潔淨，避免即興演出導致品質波動。提出分層架構：AGENTS.md（專案通用規則）+ SKILL.md（特定任務專家手冊）+ SDK（執行時）。包含完整環境配置指引（uv Python + npm 安裝）與實踐目錄結構（code-reviewer / commit-generator / security-audit 等技能資料夾）。

### 重點
- SKILL.md 按需加載機制：動態載入特定領域技能，避免無謂 context bloat 與品質不穩定（對 PDF/安全審查等特殊任務尤其有效）
- 分層架構設計：AGENTS.md (通用規則) + SKILL.md (專家手冊) + SDK (runtime)，讓智能體在清潔 context 下發揮專業能力
- 實踐範例：完整的 Python 環境配置 (uv) + .claude 資料夾結構、skill 子資料夾組織、references 與 scripts 配置

**原文：** [medium-tag-claude](https://abvijaykumar.medium.com/building-deep-agents-skill-md-with-claude-sdk-11d8bf47754b?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Continuing the series on Deep Agents, in this blog, we will build a complete deep agent application that uses SKILL.md, to respond to the&#x2026; Continue reading on Medium »

</details>