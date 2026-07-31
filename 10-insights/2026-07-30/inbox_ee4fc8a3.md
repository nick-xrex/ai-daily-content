---
id: inbox_ee4fc8a3
date: 2026-07-30
source_ref: "[[00-inbox/2026-07-30/0107-hermes-agent-releases-hermes-agent-v0-19-1-v2026-7-30-8f28]]"
title: "Hermes Agent v0.19.1 (v2026.7.30)"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.30
source: hermes-agent-releases
published_at: 2026-07-30T23:45:37+00:00
fetched_at: 2026-07-31T01:12:40.816396+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent 发布 v0.19.1 (v2026.7.30)，这是一个补丁版本，整合了自 v0.19.0（7 月 20 日）以来的约 1,000+ 个 PRs，涉及 2,789 个 commits、4,748 个文件变动、442,000 行新增代码和 392,300 行删除代码。这个版本主要聚焦于 gateway、voice 子系统、桌面应用和安装程序的 bug 修复和问题修复。同时还包括 Buzz/Nostr 频道、FLUX3 视频生成与传递、Telegram 媒体可靠性等平台工作。这次更新为下游消费者（Docker 镜像、托管部署、全新安装）提供了稳定的标签版本。完整的发版说明将随 v0.20.0 推出。"
key_points:
  - "1,000+ PRs 整合至稳定版本用于下游消费者（Docker 镜像、托管部署、全新安装）"
  - "2,789 commits 和约 442,000 行新增代码在 10 天内完成，影响 4,748 个文件"
  - "覆盖 gateway、voice subsystem、desktop app 和 installer 等多个子系统的 bug 修复和 salvage waves"
tags: [hermes-agent, release, patch-version, bug-fixes]
topics: []
importance: 3
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.19.1 (v2026.7.30)

Hermes Agent 发布 v0.19.1 (v2026.7.30)，这是一个补丁版本，整合了自 v0.19.0（7 月 20 日）以来的约 1,000+ 个 PRs，涉及 2,789 个 commits、4,748 个文件变动、442,000 行新增代码和 392,300 行删除代码。这个版本主要聚焦于 gateway、voice 子系统、桌面应用和安装程序的 bug 修复和问题修复。同时还包括 Buzz/Nostr 频道、FLUX3 视频生成与传递、Telegram 媒体可靠性等平台工作。这次更新为下游消费者（Docker 镜像、托管部署、全新安装）提供了稳定的标签版本。完整的发版说明将随 v0.20.0 推出。

### 重點
- 1,000+ PRs 整合至稳定版本用于下游消费者（Docker 镜像、托管部署、全新安装）
- 2,789 commits 和约 442,000 行新增代码在 10 天内完成，影响 4,748 个文件
- 覆盖 gateway、voice subsystem、desktop app 和 installer 等多个子系统的 bug 修复和 salvage waves

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.30)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.19.1 (v2026.7.30) 
 Release Date: July 30, 2026 
 
 Patch release. This tag rolls up the ~1,000+ PRs merged since v0.19.0 into a stable tagged release for downstream consumers (Docker images, hosted deployments, fresh installs). 
 
 
 About this release 
 Since v2026.7.20 (v0.19.0, July 20): ~2,789 commits · ~4,748 files changed · ~442,000 insertions · ~392,300 deletions on main . This window is dominated by bug-fix and salvage waves across the gateway, voice subsystem, desktop app, and installer, plus continued platform work (Buzz/Nostr channel, FLUX3 video generation and delivery, Telegram media reliability, voice-mode regressions). 
 Full curated release notes for this window will ship with v0.20.0 , which will document everything from v0.19.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped. 
 Updating 
 hermes update
 # or fresh install: 
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash 
 Full Changelog : v2026.7.20...v2026.7.30

</details>