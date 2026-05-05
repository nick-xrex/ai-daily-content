---
id: inbox_820a2bdf
date: 2026-05-04
source_ref: "[[00-inbox/2026-05-04/youtube/0819-youtube-ai-engineer-skill-issue-how-we-used-ai-to-make-agent-b05c]]"
title: "Skill Issue: How We Used AI to Make Agents Actually Good at Supabase — Pedro Rodrigues, Supabase"
url: https://www.youtube.com/watch?v=GmAQKINjv1E
source: youtube-ai-engineer
published_at: 2026-05-04T16:00:06+00:00
fetched_at: 2026-05-05T08:27:19.522306+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Supabase 的 Pedro Rodrigues 详解编写高效 Agent Skills 的核心方法论：写 Skills 易，但写能真正提升 agent 性能的 Skills 难。通过 MCP + CLI 工具 + Braintrust eval harness 构建、测试、迭代的闭环，演示常见陷阱（Skills 未被调用、指令误导、外表看好但不实用）。强调量化验证 > 猜测。"
key_points:
  - "Skills 评估的关键工具：MCP、CLI tooling、Braintrust eval harness"
  - "常见失败模式：Skills 未被使用、指令表述不当、表面优化无实效"
  - "核心方法论：write → eval → inspect → iterate 的闭环验证"
tags: [agent-skills, mcp, evaluation-framework, supabase, braintrust]
topics: [agents.mcp]
importance: 4
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Skill Issue: How We Used AI to Make Agents Actually Good at Supabase — Pedro Rodrigues, Supabase

Supabase 的 Pedro Rodrigues 详解编写高效 Agent Skills 的核心方法论：写 Skills 易，但写能真正提升 agent 性能的 Skills 难。通过 MCP + CLI 工具 + Braintrust eval harness 构建、测试、迭代的闭环，演示常见陷阱（Skills 未被调用、指令误导、外表看好但不实用）。强调量化验证 > 猜测。

### 重點
- Skills 评估的关键工具：MCP、CLI tooling、Braintrust eval harness
- 常见失败模式：Skills 未被使用、指令表述不当、表面优化无实效
- 核心方法论：write → eval → inspect → iterate 的闭环验证

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=GmAQKINjv1E)