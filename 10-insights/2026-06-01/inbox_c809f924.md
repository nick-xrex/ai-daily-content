---
id: inbox_c809f924
date: 2026-06-01
source_ref: "[[00-inbox/2026-06-01/2246-infoq-main-badhost-vulnerability-exposes-ai-agents-66f8]]"
title: "BadHost Vulnerability Exposes AI Agents, Evaluators, and LLM Gateways"
url: https://www.infoq.com/news/2026/06/badhost-ai-systems-vulnerability/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-01T14:00:00+00:00
fetched_at: 2026-06-01T22:53:40.537614+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "BadHost 是 Starlette（Python web 框架）的高嚴重度認證繞過漏洞。周下載量 325 百萬，直接威脅 AI agents、evaluators 和 LLM gateways。攻擊者利用格式錯誤的 HTTP Host headers 繞過路徑型訪問控制。取得敏感 AI 基礎設施的訪問權限。依賴 Starlette 構建 AI 系統的開發者需立即關注與升級。"
key_points:
  - "BadHost 漏洞（認證繞過）影響 Starlette 框架，周下載 325 百萬"
  - "攻擊向量：格式錯誤 Host headers 繞過路徑型訪問控制"
  - "直接威脅 AI agents、LLM gateways 等敏感基礎設施，需緊急升級"
tags: [security, vulnerability, starlette, authentication-bypass, ai-infrastructure]
topics: []
importance: 4
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## BadHost Vulnerability Exposes AI Agents, Evaluators, and LLM Gateways

BadHost 是 Starlette（Python web 框架）的高嚴重度認證繞過漏洞。周下載量 325 百萬，直接威脅 AI agents、evaluators 和 LLM gateways。攻擊者利用格式錯誤的 HTTP Host headers 繞過路徑型訪問控制。取得敏感 AI 基礎設施的訪問權限。依賴 Starlette 構建 AI 系統的開發者需立即關注與升級。

### 重點
- BadHost 漏洞（認證繞過）影響 Starlette 框架，周下載 325 百萬
- 攻擊向量：格式錯誤 Host headers 繞過路徑型訪問控制
- 直接威脅 AI agents、LLM gateways 等敏感基礎設施，需緊急升級

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/badhost-ai-systems-vulnerability/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

BadHost is a high-severity authentication bypass vulnerability in the widely used Python web framework Starlette, with 325 million weekly downloads. The flaw allows attackers to use malformed HTTP Host headers to bypass path-based access controls and access sensitive AI agent infrastructure, among other systems. By Sergio De Simone

</details>