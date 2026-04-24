---
id: inbox_54580db0
date: 2026-04-22
source_ref: "[[00-inbox/2026-04-22/0246-infoq-architecture-cloudflare-sandboxes-reach-general-avail-95e0]]"
title: "Cloudflare Sandboxes Reach General Availability, Giving AI Agents Persistent Isolated Environments"
url: https://www.infoq.com/news/2026/04/cloudflare-sandboxes-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-04-22T10:00:00+00:00
fetched_at: 2026-04-24T03:01:00.186796+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare Sandboxes 與 Containers 正式進入通用可用性（GA）階段。該服務提供持久隔離的 Linux 環境供 AI agent 使用，新增功能包括：安全認證注入（經代理出口）、PTY 終端支援、持久代碼解釋器、文件系統監視及快照式會話恢復。定價採按使用 CPU 週期計費，避免閒置浪費。此發布標誌著無伺服器隔離環境開始支援有狀態 AI agent 工作負載。"
key_points:
  - "持久隔離 Linux 環境支援有狀態 AI agent（含代碼執行、文件訪問）"
  - "快照恢復與 PTY 支援降低 agent 無狀態時的復雜度"
  - "按實際 CPU 使用計費，適配間歇性 agent 工作負載"
tags: [cloudflare-sandboxes, ai-agents, serverless-compute, sandbox-isolation, persistent-env]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Sandboxes Reach General Availability, Giving AI Agents Persistent Isolated Environments

Cloudflare Sandboxes 與 Containers 正式進入通用可用性（GA）階段。該服務提供持久隔離的 Linux 環境供 AI agent 使用，新增功能包括：安全認證注入（經代理出口）、PTY 終端支援、持久代碼解釋器、文件系統監視及快照式會話恢復。定價採按使用 CPU 週期計費，避免閒置浪費。此發布標誌著無伺服器隔離環境開始支援有狀態 AI agent 工作負載。

### 重點
- 持久隔離 Linux 環境支援有狀態 AI agent（含代碼執行、文件訪問）
- 快照恢復與 PTY 支援降低 agent 無狀態時的復雜度
- 按實際 CPU 使用計費，適配間歇性 agent 工作負載

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/04/cloudflare-sandboxes-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/04/cloudflare-sandboxes-ga/en/headerimage/generatedHeaderImage-1776749566952.jpg" /><p>Cloudflare has released Sandboxes and Containers into general availability, providing persistent isolated Linux environments for AI agent workloads. New capabilities include secure credential injection via egress proxy, PTY terminal support, persistent code interpreters, filesystem watching, and snapshot-based session recovery. Active CPU pricing charges only for used cycles.</p> <i>By Steef-Jan Wiggers</i>

</details>