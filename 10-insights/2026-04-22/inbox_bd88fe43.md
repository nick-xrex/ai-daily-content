---
id: inbox_bd88fe43
date: 2026-04-22
source_ref: "[[00-inbox/2026-04-22/0246-infoq-ai-ml-cloudflare-sandboxes-reach-general-avail-19eb]]"
title: "Cloudflare Sandboxes Reach General Availability, Giving AI Agents Persistent Isolated Environments"
url: https://www.infoq.com/news/2026/04/cloudflare-sandboxes-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-04-22T10:00:00+00:00
fetched_at: 2026-04-24T03:00:09.925156+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare Sandboxes 與 Containers 正式推出，為 AI 代理提供持久的隔離 Linux 執行環境。核心安全功能包括透過出口代理的憑證注入，讓代理安全地訪問外部服務而無需存儲敏感憑證。系統支援 PTY 終端、持久代碼解釋器、檔案系統監視和快照式工作階段復原。這些功能使 AI 代理能在生產環境中可靠地運行複雜代碼。計費採用按實際 CPU 使用量計價，確保用戶只為真正消耗的資源付費。"
key_points:
  - "Cloudflare Sandboxes GA：提供 AI 代理專用的持久隔離執行環境（Linux containers）"
  - "安全憑證注入(egress proxy)、PTY、代碼解釋器、檔案監視、快照復原等完整功能集"
  - "按實際 CPU 使用量計費(pay-per-used-cycle)，相比傳統定量套餐更具成本效率"
tags: [cloudflare-sandboxes, ai-agents, infrastructure, code-execution, container-runtime]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Sandboxes Reach General Availability, Giving AI Agents Persistent Isolated Environments

Cloudflare Sandboxes 與 Containers 正式推出，為 AI 代理提供持久的隔離 Linux 執行環境。核心安全功能包括透過出口代理的憑證注入，讓代理安全地訪問外部服務而無需存儲敏感憑證。系統支援 PTY 終端、持久代碼解釋器、檔案系統監視和快照式工作階段復原。這些功能使 AI 代理能在生產環境中可靠地運行複雜代碼。計費採用按實際 CPU 使用量計價，確保用戶只為真正消耗的資源付費。

### 重點
- Cloudflare Sandboxes GA：提供 AI 代理專用的持久隔離執行環境（Linux containers）
- 安全憑證注入(egress proxy)、PTY、代碼解釋器、檔案監視、快照復原等完整功能集
- 按實際 CPU 使用量計費(pay-per-used-cycle)，相比傳統定量套餐更具成本效率

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/04/cloudflare-sandboxes-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/04/cloudflare-sandboxes-ga/en/headerimage/generatedHeaderImage-1776749566952.jpg" /><p>Cloudflare has released Sandboxes and Containers into general availability, providing persistent isolated Linux environments for AI agent workloads. New capabilities include secure credential injection via egress proxy, PTY terminal support, persistent code interpreters, filesystem watching, and snapshot-based session recovery. Active CPU pricing charges only for used cycles.</p> <i>By Steef-Jan Wiggers</i>

</details>