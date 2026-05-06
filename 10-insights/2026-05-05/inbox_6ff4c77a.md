---
id: inbox_6ff4c77a
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_6ff4c77a]]"
title: "Computer Use is 45x more expensive than structured APIs"
url: https://reflex.dev/blog/computer-use-is-45x-more-expensive-than-structured-apis/
source: hackernews
published_at: 2026-05-05T16:34:48+00:00
fetched_at: 2026-05-06T13:33:53.290646+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reflex 团队的成本基准测试揭示 vision agents（计算机操作）相比结构化 API 成本高 45 倍。测试在同一管理后台应用上让 Claude Sonnet 分别驱动 UI（视觉模式，使用浏览器自动化）和直接调用 HTTP endpoint。API agent 8 次工具调用完成任务，而 vision agent 需 400-750k input tokens、14-22 分钟执行时间，且需显式 14 步 UI 导航提示才能成功（无提示则漏掉分页内容）。关键发现：vision agents 面对未呈现的内容无法主动探索，导致隐形工程成本（详细提示编写）；API agent 直接读取结构化响应，成本与性能均优化。这给 internal tools 自动化的方案选择提供了量化决策依据。"
key_points:
  - "Vision agents 成本高 45 倍：API agent 8 次调用 vs Vision agent 400-750k tokens + 14-22 分钟，成本差异来自 screenshot-reason-click 非确定性循环"
  - "Vision agents 无信号问题：当页面内容被截断（如分页控制），agent 无法判断数据不完整，需明确 UI 导航提示才能避免漏掉工作；API agent 直接读取完整结果集"
  - "工程成本隐形：每个 vision agent 部署都需投入特定的详细提示工程，这项成本不算入 token count 但代表真实劳动"
tags: [vision-agents, computer-use, cost-analysis, structured-apis, internal-tools]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Computer Use is 45x more expensive than structured APIs

Reflex 团队的成本基准测试揭示 vision agents（计算机操作）相比结构化 API 成本高 45 倍。测试在同一管理后台应用上让 Claude Sonnet 分别驱动 UI（视觉模式，使用浏览器自动化）和直接调用 HTTP endpoint。API agent 8 次工具调用完成任务，而 vision agent 需 400-750k input tokens、14-22 分钟执行时间，且需显式 14 步 UI 导航提示才能成功（无提示则漏掉分页内容）。关键发现：vision agents 面对未呈现的内容无法主动探索，导致隐形工程成本（详细提示编写）；API agent 直接读取结构化响应，成本与性能均优化。这给 internal tools 自动化的方案选择提供了量化决策依据。

### 重點
- Vision agents 成本高 45 倍：API agent 8 次调用 vs Vision agent 400-750k tokens + 14-22 分钟，成本差异来自 screenshot-reason-click 非确定性循环
- Vision agents 无信号问题：当页面内容被截断（如分页控制），agent 无法判断数据不完整，需明确 UI 导航提示才能避免漏掉工作；API agent 直接读取完整结果集
- 工程成本隐形：每个 vision agent 部署都需投入特定的详细提示工程，这项成本不算入 token count 但代表真实劳动

**原文：** [hackernews](https://reflex.dev/blog/computer-use-is-45x-more-expensive-than-structured-apis/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Computer Use is 45x more expensive than structured APIs

</details>