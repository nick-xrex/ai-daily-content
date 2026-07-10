---
id: inbox_bcc19b4a
date: 2026-07-08
source_ref: "[[00-inbox/.../inbox_bcc19b4a]]"
title: "Hermes Agent v0.18.2 (2026.7.7.2)"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.7.2
source: hermes-agent-releases
published_at: 2026-07-08T03:13:14+00:00
fetched_at: 2026-07-10T00:43:20.678716+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent v0.18.2（版本 2026.7.7.2）是 v0.18.1 上的當日補丁（2026-07-08 發布）。核心修正：WhatsApp Baileys 依賴解除 git commit pin（#60643），改用已發布的 npm 版本 7.0.0-rc13，使 npm install 和 Docker 鏡像構建可靠化。詳細更新說明（highlights、feature 區域、完整貢獻者名單）將隨 v0.19.0 發布；本版本優先穩定 Docker 構建等下游消費路徑。"
key_points:
  - "WhatsApp Baileys 依賴從 git commit pin 遷移至已發布 npm 版本 7.0.0-rc13（#60643），修復 Docker 鏡像構建的可靠性"
tags: [whatsapp-bridge, dependency-management, docker-builds]
topics: [agents.mcp]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.18.2 (2026.7.7.2)

Hermes Agent v0.18.2（版本 2026.7.7.2）是 v0.18.1 上的當日補丁（2026-07-08 發布）。核心修正：WhatsApp Baileys 依賴解除 git commit pin（#60643），改用已發布的 npm 版本 7.0.0-rc13，使 npm install 和 Docker 鏡像構建可靠化。詳細更新說明（highlights、feature 區域、完整貢獻者名單）將隨 v0.19.0 發布；本版本優先穩定 Docker 構建等下游消費路徑。

### 重點
- WhatsApp Baileys 依賴從 git commit pin 遷移至已發布 npm 版本 7.0.0-rc13（#60643），修復 Docker 鏡像構建的可靠性

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.7.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Hermes Agent v0.18.2 (2026.7.7.2)

Hermes Agent v0.18.2 (v2026.7.7.2) 
 Release Date: July 7, 2026 
 
 Same-day patch on top of v0.18.1, picking up the WhatsApp Baileys dependency fix needed for tagged-release Docker builds. 
 
 
 What's in this patch 
 
 fix(whatsapp): unpin Baileys from git commit, use published 7.0.0-rc13 ( #60643 ) — the WhatsApp bridge dependency now installs from the published npm release instead of a pinned git commit, making installs and Docker image builds reliable. 
 
 Full curated release notes for the entire post-v0.18.0 window ship with v0.19.0. 
 Updating 
 hermes update # existing installs 
pip install -U hermes-agent 
 Full Changelog : v2026.7.7...v2026.7.7.2

</details>