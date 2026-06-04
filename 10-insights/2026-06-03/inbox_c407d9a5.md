---
id: inbox_c407d9a5
date: 2026-06-03
source_ref: "[[00-inbox/.../inbox_c407d9a5]]"
title: "v0.42.1"
url: https://github.com/rtk-ai/rtk/releases/tag/v0.42.1
source: rtk-releases
published_at: 2026-06-03T12:51:17+00:00
fetched_at: 2026-06-04T00:52:41.733404+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.42.1 發布，修復 openclaw 元件中的 execSync 危險命令執行問題。該修復避免在非同步操作環境中直接呼叫同步執行函式，提高系統穩定性和安全性。"
key_points:
  - "RTK v0.42.1 修復 openclaw execSync 非同步風險"
  - "改善危險命令執行的安全模式"
  - "Commit: 1bb17f4"
tags: [rtk, bug-fix, security, async]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.42.1

RTK v0.42.1 發布，修復 openclaw 元件中的 execSync 危險命令執行問題。該修復避免在非同步操作環境中直接呼叫同步執行函式，提高系統穩定性和安全性。

### 重點
- RTK v0.42.1 修復 openclaw execSync 非同步風險
- 改善危險命令執行的安全模式
- Commit: 1bb17f4

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/v0.42.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.42.1

0.42.1 (2026-06-03) 
 Bug Fixes 
 
 openclaw: no execSync to avoid async dangerous cmds ( 1bb17f4 )

</details>