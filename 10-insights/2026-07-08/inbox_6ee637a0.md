---
id: inbox_6ee637a0
date: 2026-07-08
source_ref: "[[00-inbox/.../inbox_6ee637a0]]"
title: "Hermes Agent v0.18.1 (2026.7.7)"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.7
source: hermes-agent-releases
published_at: 2026-07-08T01:16:58+00:00
fetched_at: 2026-07-10T00:43:20.679373+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent v0.18.1（2026.7.7）是基礎設施驅動的穩定化補丁標籤，累計自 v0.18.0（2026-07-01）以來 ~660 PRs、667 commits 跨 ~990 個檔案（+89.5k/−10.4k 行代碼）的六日積累。核心改進包含 Windows installer/updater 自修復、dashboard 與 gateway 穩定性修復、WhatsApp dashboard 配對、MCP 與 provider 修復、大量穩定性加固工作。此版本優先穩定下游消費者（Docker 鏡像、hosted 部署、PyPI 安裝），完整的策劃更新說明（highlights、feature 區域、貢獻者名單）延遲至 v0.19.0 發布；所有變更均已記錄，僅文檔整理在下個 minor。"
key_points:
  - "累計規模：~660 PRs / 667 commits / ~990 files touched / +89.5k−10.4k 行，六日內的大規模穩定化工作"
  - "核心改進：Windows installer/updater 自修復、dashboard/gateway 穩定性、WhatsApp pairing、MCP/provider 加固"
  - "發布策略：基礎設施驅動的標籤化（供 Docker/PyPI/hosted 下游消費），完整文檔整合於 v0.19.0，確保版本間一致性"
tags: [stability-patch, windows-hardening, mcp-provider-fixes, infrastructure-release]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.18.1 (2026.7.7)

Hermes Agent v0.18.1（2026.7.7）是基礎設施驅動的穩定化補丁標籤，累計自 v0.18.0（2026-07-01）以來 ~660 PRs、667 commits 跨 ~990 個檔案（+89.5k/−10.4k 行代碼）的六日積累。核心改進包含 Windows installer/updater 自修復、dashboard 與 gateway 穩定性修復、WhatsApp dashboard 配對、MCP 與 provider 修復、大量穩定性加固工作。此版本優先穩定下游消費者（Docker 鏡像、hosted 部署、PyPI 安裝），完整的策劃更新說明（highlights、feature 區域、貢獻者名單）延遲至 v0.19.0 發布；所有變更均已記錄，僅文檔整理在下個 minor。

### 重點
- 累計規模：~660 PRs / 667 commits / ~990 files touched / +89.5k−10.4k 行，六日內的大規模穩定化工作
- 核心改進：Windows installer/updater 自修復、dashboard/gateway 穩定性、WhatsApp pairing、MCP/provider 加固
- 發布策略：基礎設施驅動的標籤化（供 Docker/PyPI/hosted 下游消費），完整文檔整合於 v0.19.0，確保版本間一致性

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.7)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Hermes Agent v0.18.1 (2026.7.7)

Hermes Agent v0.18.1 (v2026.7.7) 
 Release Date: July 7, 2026 
 
 Patch release. This tag rolls up the ~660 PRs merged since v0.18.0 (July 1) — bug fixes, hardening, and in-progress feature work — into a stable tagged release for downstream consumers (Docker images, hosted deployments, PyPI installs). 
 
 
 About this release 
 This is an infrastructure-driven patch tag rather than a fully curated release. Since v0.18.0 shipped six days ago, main has accumulated roughly 667 commits across ~990 files (+89.5k/−10.4k lines) , including installer/updater self-healing on Windows, dashboard and gateway fixes, WhatsApp dashboard pairing, MCP and provider fixes, and a large volume of stability work. 
 Full curated release notes for this window will ship with v0.19.0 , which will document everything from v0.18.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped; it's documented in the next minor release. 
 Updating 
 hermes update # existing installs 
pip install -U hermes-agent 
 Full Changelog : v2026.7.1...v2026.7.7

</details>