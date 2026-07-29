---
id: inbox_d3e76489
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_d3e76489]]"
title: "AWS Launches Amazon GuardDuty Investigation Agent to Automate Threat Triage"
url: https://www.infoq.com/news/2026/07/guardduty-investigation-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-28T07:14:00+00:00
fetched_at: 2026-07-29T03:41:28.059430+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 發布了 GuardDuty Investigation Agent 的公開預覽版本，能夠自動關聯安全發現、90 天活動日誌和資源拓撲資訊。該代理生成包含風險評級、信心分數和 MITRE ATT&CK 框架分類的結構化威脅報告。結構化報告格式便於機器解析，支援被其他代理工具透過 AWS MCP Server 自動調用。此整合使無人安全調查工作流成為可能，減少了安全團隊的手動分類負擔。預覽期間的配額限制為每帳戶每日 10 次調查，這對於試點部署和驗證效果是合理的限制。"
key_points:
  - "GuardDuty Investigation Agent 自動關聯多源資料（安全發現、90 天日誌、資源拓撲）生成結構化報告"
  - "整合 MITRE ATT&CK 框架分類和風險評級，提供機器可讀的威脅情報"
  - "通過 AWS MCP Server 暴露，支援被代理工具自動調用進行無人安全調查"
tags: [aws, guardduty, threat-investigation, security, mcp]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Launches Amazon GuardDuty Investigation Agent to Automate Threat Triage

AWS 發布了 GuardDuty Investigation Agent 的公開預覽版本，能夠自動關聯安全發現、90 天活動日誌和資源拓撲資訊。該代理生成包含風險評級、信心分數和 MITRE ATT&CK 框架分類的結構化威脅報告。結構化報告格式便於機器解析，支援被其他代理工具透過 AWS MCP Server 自動調用。此整合使無人安全調查工作流成為可能，減少了安全團隊的手動分類負擔。預覽期間的配額限制為每帳戶每日 10 次調查，這對於試點部署和驗證效果是合理的限制。

### 重點
- GuardDuty Investigation Agent 自動關聯多源資料（安全發現、90 天日誌、資源拓撲）生成結構化報告
- 整合 MITRE ATT&CK 框架分類和風險評級，提供機器可讀的威脅情報
- 通過 AWS MCP Server 暴露，支援被代理工具自動調用進行無人安全調查

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/guardduty-investigation-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# AWS Launches Amazon GuardDuty Investigation Agent to Automate Threat Triage

AWS released a public preview of the GuardDuty investigation agent, which correlates findings, 90-day activity logs, and resource topologies into structured reports with risk ratings, confidence scores, and MITRE ATT&amp;CK classification. It is reachable through the AWS MCP Server, so investigations can run from agentic tooling. Preview quotas cap usage at 10 investigations per account per day. By Steef-Jan Wiggers

</details>