---
id: inbox_c67bb0e4
date: 2026-06-01
source_ref: "[[00-inbox/2026-06-01/2246-infoq-ai-ml-badhost-vulnerability-exposes-ai-agents-973e]]"
title: "BadHost Vulnerability Exposes AI Agents, Evaluators, and LLM Gateways"
url: https://www.infoq.com/news/2026/06/badhost-ai-systems-vulnerability/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-06-01T14:00:00+00:00
fetched_at: 2026-06-01T22:54:44.495859+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "BadHost 為 Starlette（Python 框架，週下載量 325M）的高嚴重性認證繞過漏洞。攻擊者可使用格式不正確的 HTTP Host header 繞過基於路徑的存取控制，進而入侵 AI agent 基礎設施及其他系統。漏洞根源在於 Host header 驗證缺陷，使路徑型授權失效。"
key_points:
  - "Starlette Host header 驗證缺陷：malformed Host header 繞過路徑型存取控制"
  - "影響範圍：Starlette 週下載 325M，廣泛應用於 AI agent 基礎設施"
  - "攻擊方法：使用格式不當的 Host header，使授權檢查失敗"
tags: [security, starlette, host-header-bypass, authentication, cve]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## BadHost Vulnerability Exposes AI Agents, Evaluators, and LLM Gateways

BadHost 為 Starlette（Python 框架，週下載量 325M）的高嚴重性認證繞過漏洞。攻擊者可使用格式不正確的 HTTP Host header 繞過基於路徑的存取控制，進而入侵 AI agent 基礎設施及其他系統。漏洞根源在於 Host header 驗證缺陷，使路徑型授權失效。

### 重點
- Starlette Host header 驗證缺陷：malformed Host header 繞過路徑型存取控制
- 影響範圍：Starlette 週下載 325M，廣泛應用於 AI agent 基礎設施
- 攻擊方法：使用格式不當的 Host header，使授權檢查失敗

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/06/badhost-ai-systems-vulnerability/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

BadHost is a high-severity authentication bypass vulnerability in the widely used Python web framework Starlette, with 325 million weekly downloads. The flaw allows attackers to use malformed HTTP Host headers to bypass path-based access controls and access sensitive AI agent infrastructure, among other systems. By Sergio De Simone

</details>