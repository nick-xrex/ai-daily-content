---
id: inbox_234ada51
date: 2026-04-13
source_ref: "[[00-inbox/.../inbox_234ada51]]"
title: "AWS Distinguished Eng: Learnings From 3000 Incidents And How Engineering Is Changing | Marc Brooker"
url: https://www.developing.dev/p/aws-distinguished-eng-learnings-from
source: substack-developing-dev
published_at: 2026-04-13T09:01:24+00:00
fetched_at: 2026-04-21T07:07:26.695397+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS Distinguished Engineer Marc Brooker分享來自3000個雲端系統事後檢討的學習。優質事後檢討應深入理解實際發生的事（透過完善log）並多層級追問「為什麼」、進而跨事件提取模式以構建服務而非單純修補。Brooker任職on-call 15年，因「我在實踐中關於如何建構分佈式系統的多數知識來自on-call和深度事後檢討分析」。緩存造成危險的「metastable failure」（系統在快速和宕機間振盪，因後端無法承載無緩存流量而無法復原），他發現此類失敗是大多數重大行業故障的根本原因。建議優先採用「完整具體化視圖」或可擴展後端（DynamoDB、DSQL）而非部分緩存。軟體仍供應受限、AI/代理開發機會龐大。Junior工程師應早期理解用戶、商業context和經濟學；Senior工程師必須保持hands-on經驗，否則意見淪為「本質上虛構」。"
key_points:
  - "事後檢討文化：深度logging、多層級Why分析、跨事件模式提取（不只修補）"
  - "緩存 metastable failure：系統在快速/宕機間振盪、後端無法恢復——「是大多數重大outage的根本原因」"
  - "優先完整具體化視圖或可擴展後端 vs 部分緩存；軟體供應受限、AI/代理機會巨大"
tags: [distributed-systems, postmortem-culture, caching-failures, aws]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Distinguished Eng: Learnings From 3000 Incidents And How Engineering Is Changing | Marc Brooker

AWS Distinguished Engineer Marc Brooker分享來自3000個雲端系統事後檢討的學習。優質事後檢討應深入理解實際發生的事（透過完善log）並多層級追問「為什麼」、進而跨事件提取模式以構建服務而非單純修補。Brooker任職on-call 15年，因「我在實踐中關於如何建構分佈式系統的多數知識來自on-call和深度事後檢討分析」。緩存造成危險的「metastable failure」（系統在快速和宕機間振盪，因後端無法承載無緩存流量而無法復原），他發現此類失敗是大多數重大行業故障的根本原因。建議優先採用「完整具體化視圖」或可擴展後端（DynamoDB、DSQL）而非部分緩存。軟體仍供應受限、AI/代理開發機會龐大。Junior工程師應早期理解用戶、商業context和經濟學；Senior工程師必須保持hands-on經驗，否則意見淪為「本質上虛構」。

### 重點
- 事後檢討文化：深度logging、多層級Why分析、跨事件模式提取（不只修補）
- 緩存 metastable failure：系統在快速/宕機間振盪、後端無法恢復——「是大多數重大outage的根本原因」
- 優先完整具體化視圖或可擴展後端 vs 部分緩存；軟體供應受限、AI/代理機會巨大

**原文：** [substack-developing-dev](https://www.developing.dev/p/aws-distinguished-eng-learnings-from)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# AWS Distinguished Eng: Learnings From 3000 Incidents And How Engineering Is Changing | Marc Brooker

Where caching is bad, thoughts on the industry, and learnings across his career

</details>