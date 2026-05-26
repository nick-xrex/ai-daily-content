---
id: inbox_d8a9e2bb
date: 2026-05-23
source_ref: "[[00-inbox/2026-05-23/0014-rtk-releases-v0-41-0-48b9]]"
title: "v0.41.0"
url: https://github.com/rtk-ai/rtk/releases/tag/v0.41.0
source: rtk-releases
published_at: 2026-05-23T07:50:22+00:00
fetched_at: 2026-05-26T00:25:55.652067+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.41.0 是一次重要維護發佈，共修複 20+ 項 bug 與新增多項功能。最關鍵改進是將 git push 改為串流輸出，避免大型操作中遇到的 30 秒超時問題（issue #963）。另移除 git status 的 -uall 標誌，防止輸出尺寸超過限制。新增尾部提示功能、改進激進過濾機制、強化 Docker/Kubernetes 相容性。重要安全修複：拒絕含路徑穿越的存檔提取（issue #1250），防止被惡意檔案利用。"
key_points:
  - "Git push streaming：改用串流輸出避免 30 秒超時（#963，commit d6c5647）"
  - "Git status -uall 移除：防止輸出超過原始大小限制（commit 7753e48）"
  - "路徑穿越安全修複：拒絕包含目錄遍歷的存檔提取（#1250，commit e827184）"
tags: [rtk, streaming, git, docker, security-fix]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.41.0

RTK v0.41.0 是一次重要維護發佈，共修複 20+ 項 bug 與新增多項功能。最關鍵改進是將 git push 改為串流輸出，避免大型操作中遇到的 30 秒超時問題（issue #963）。另移除 git status 的 -uall 標誌，防止輸出尺寸超過限制。新增尾部提示功能、改進激進過濾機制、強化 Docker/Kubernetes 相容性。重要安全修複：拒絕含路徑穿越的存檔提取（issue #1250），防止被惡意檔案利用。

### 重點
- Git push streaming：改用串流輸出避免 30 秒超時（#963，commit d6c5647）
- Git status -uall 移除：防止輸出超過原始大小限制（commit 7753e48）
- 路徑穿越安全修複：拒絕包含目錄遍歷的存檔提取（#1250，commit e827184）

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/v0.41.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

0.41.0 (2026-05-22) 
 Features 
 
 hints: add tail hints for tee &amp; hints + address reviews ( 46fe7c4 ) 
 
 Bug Fixes 
 
 docker: forward --tail flag in compose logs ( 5f1d8b0 ) 
=* filters: add test for aggressive filter batch fix ( f6b28c2 ) 
 filters: address adversarial test-suite findings on aggressive filtering ( 62fc0e0 ) 
 filters: aggresivity batch fix ( 90c285c ) 
 filters: split docker ps/-a paths, cap ruff violations at 50 ( f21b864 ) 
 git: drop -uall from compact status so output never exceeds raw ( 7753e48 ) 
 git: preserve full status paths and untracked files ( 3ba1634 ) 
 git: stream push output to avoid spurious 30s timeout ( #963 ) ( d6c5647 ) 
 git: stream push output via FilterMode::Streaming ( #963 ) ( be51783 ) 
 hooks/init: preserve user content in copilot-instructions.md ( d108165 ) 
 install: reject archive with path traversal before extraction ( #1250 ) ( e827184 ) 
 kubectl: compact get pods and services aliases ( 2dd0ec9 ) 
 re-add env python as noisy dir ( 4eefe2f ) 
 rust: multi-line blocks used with tail hint ( 4960630 ) 
 tee: safe truncation caps and compose-ps tee content fix ( 548e4dd ) 
 tee: safe truncation caps and tee/hint coverage ( 15a0d2e ) 
 truncate: global caps reduce (avoid underflow and 0 results) ( d5a1731 ) 
 
 
 '...' ascii to unicode, remove some comments ( 3571d52 )

</details>