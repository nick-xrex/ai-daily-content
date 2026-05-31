---
id: inbox_36ae316a
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/0039-simon-willison-how-we-contain-claude-across-products-b487]]"
title: "How we contain Claude across products"
url: https://simonwillison.net/2026/May/30/how-we-contain-claude/#atom-everything
source: simon-willison
published_at: 2026-05-30T21:36:24+00:00
fetched_at: 2026-05-31T00:47:58.093099+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Anthropic 發表詳細文檔說明跨產品沙盒策略：Claude.ai 採 gVisor；Claude Code（本地運行）用 macOS Seatbelt + Linux Bubblewrap；Claude Cowork 運行完整 VM（macOS Apple Virtualization 框架、Windows HCS）。關鍵防禦原則為「credential 不入沙盒即不可外洩」，採用 process sandbox、VM、filesystem 邊界、egress 控制分層隔離。文檔同步揭示過去遺漏的風險（如 api.anthropic.com/v1/files 外洩向量），推動持續迭代改進。"
key_points:
  - "分層沙盒架構：Claude.ai gVisor / Claude Code Seatbelt+Bubblewrap / Cowork 完整 VM，各自應對不同信任邊界和部署模式"
  - "防禦原則：credential 永不入沙盒 → credential 無法外洩（無視模型創意路徑或攻擊向量），設計哲學層級的硬邊界"
  - "過往風險教訓：api.anthropic.com/v1/files 外洩向量等過去遺漏案例，促使文檔發表與持續安全審計"
tags: [sandbox, security, claude-code, egress-control, defense-in-depth]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## How we contain Claude across products

Anthropic 發表詳細文檔說明跨產品沙盒策略：Claude.ai 採 gVisor；Claude Code（本地運行）用 macOS Seatbelt + Linux Bubblewrap；Claude Cowork 運行完整 VM（macOS Apple Virtualization 框架、Windows HCS）。關鍵防禦原則為「credential 不入沙盒即不可外洩」，採用 process sandbox、VM、filesystem 邊界、egress 控制分層隔離。文檔同步揭示過去遺漏的風險（如 api.anthropic.com/v1/files 外洩向量），推動持續迭代改進。

### 重點
- 分層沙盒架構：Claude.ai gVisor / Claude Code Seatbelt+Bubblewrap / Cowork 完整 VM，各自應對不同信任邊界和部署模式
- 防禦原則：credential 永不入沙盒 → credential 無法外洩（無視模型創意路徑或攻擊向量），設計哲學層級的硬邊界
- 過往風險教訓：api.anthropic.com/v1/files 外洩向量等過去遺漏案例，促使文檔發表與持續安全審計

**原文：** [simon-willison](https://simonwillison.net/2026/May/30/how-we-contain-claude/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

How we contain Claude across products 
A complaint I often have about sandboxing products is that they are rarely thoroughly documented , and in the absence of detailed documentation it's hard to know how much I can trust them. 
 Anthropic just published a fantastic overview of how their various sandbox techniques work across Claude.ai , Claude Code, and Cowork. 
 
 We constrain where and how an agent can act with process sandboxes, VMs, filesystem boundaries, and egress controls. The goal is to set a hard boundary on what an agent can reach. For example, if credentials never enter the sandbox, they can't be exfiltrated, regardless of whether the cause is a user, a model finding a “creative” path, or an attacker. 
 
 Claude.ai uses gVisor. Claude Code, run locally, uses Seatbelt on macOS and Bubblewrap on Linux. Claude Cowork runs a full VM (Apple's Virtualization framework on macOS, HCS on Windows). 
 There's a lot in here, including some interesting stories of risks they missed such as the api.anthropic.com/v1/files exfiltration vector covered here previously . 
 This reminded me it's time I took another look at Anthropic's open source srt (Anthropic Sandbox Runtime) tool - it's mature enough know that I'm ready to give it a proper go.

 Tags: sandboxing , security , ai , generative-ai , llms , anthropic , claude , claude-code

</details>