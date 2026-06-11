---
id: inbox_704712dc
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_704712dc]]"
title: "v13.5.2"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.5.2
source: claude-mem-releases
published_at: 2026-06-10T04:49:49+00:00
fetched_at: 2026-06-11T00:23:32.321899+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.5.2 新增平台與工具鏈遙測以診斷 install→live-worker 啟動漏斗。每個事件現攜帶 os_version（區分 Windows 10 vs 11、macOS 版本）、is_wsl、node_version。install_completed 報告 interactive（TTY vs 腳本化）、install_method（npm/bun/pnpm/yarn）、檢測 bun_version、uv_version、claude_code_version。install_failed 攜帶相同裝置背景。新欄位同作 person properties，解鎖按 OS 版本、WSL、安裝方法細分的啟動漏斗與留存世代分析。"
key_points:
  - "平台診斷深化：os_version (Windows/macOS 版本) / is_wsl / node_version 三大欄位，支援細分啟動漏斗按作業系統版本與 WSL 狀態"
  - "工具鏈檢測：install_completed/install_failed 新增 install_method (5 種包管理工具) 與 bun_version / uv_version / claude_code_version，啟用工具鏈版本世代分析"
  - "Person properties 啟用：新欄位全作為使用者屬性，DAU/WAU 與留存世代可按 OS/WSL/install_method 細分，啟動漏斗可見工具鏈組合影響"
tags: [telemetry-instrumentation, platform-diagnostics, install-funnel, toolchain-detection]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.5.2

claude-mem v13.5.2 新增平台與工具鏈遙測以診斷 install→live-worker 啟動漏斗。每個事件現攜帶 os_version（區分 Windows 10 vs 11、macOS 版本）、is_wsl、node_version。install_completed 報告 interactive（TTY vs 腳本化）、install_method（npm/bun/pnpm/yarn）、檢測 bun_version、uv_version、claude_code_version。install_failed 攜帶相同裝置背景。新欄位同作 person properties，解鎖按 OS 版本、WSL、安裝方法細分的啟動漏斗與留存世代分析。

### 重點
- 平台診斷深化：os_version (Windows/macOS 版本) / is_wsl / node_version 三大欄位，支援細分啟動漏斗按作業系統版本與 WSL 狀態
- 工具鏈檢測：install_completed/install_failed 新增 install_method (5 種包管理工具) 與 bun_version / uv_version / claude_code_version，啟用工具鏈版本世代分析
- Person properties 啟用：新欄位全作為使用者屬性，DAU/WAU 與留存世代可按 OS/WSL/install_method 細分，啟動漏斗可見工具鏈組合影響

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.5.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.5.2

What's New in 13.5.2 
 Platform and toolchain telemetry to diagnose the install → live-worker activation dropoff (anonymous, opt-out — see npx claude-mem telemetry ): 
 
 Every event now carries os_version (kernel release — distinguishes Windows 10 vs 11, macOS releases), is_wsl , and node_version alongside the existing os / arch / runtime fields. 
 install_completed now reports interactive (TTY vs scripted), install_method (npm / bun / pnpm / yarn), and detected bun_version , uv_version , and claude_code_version . 
 install_failed carries the same install context so aborted installs are sliceable by platform too. 
 New fields are person properties as well, so activation funnels can be broken down by OS version, WSL, and install method. 
 Scrub whitelist, consent screen, docs, and tests updated for every new property. 
 
 🤖 Generated with Claude Code

</details>