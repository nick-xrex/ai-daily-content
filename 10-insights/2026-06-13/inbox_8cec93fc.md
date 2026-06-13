---
id: inbox_8cec93fc
date: 2026-06-13
source_ref: "[[00-inbox/.../inbox_8cec93fc]]"
title: "v13.5.7"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.5.7
source: claude-mem-releases
published_at: 2026-06-13T00:06:28+00:00
fetched_at: 2026-06-13T04:10:04.851178+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.5.7 修復陳舊 Claude CLI 默默殺死每個觀察的問題（#2911）。根本原因：被棄用的 npm-global claude 二進制檔在 PATH 中排在當前安裝前，每個 Observer 生成在 flag 解析時立即崩潰，worker 健康但零觀察且日誌無記錄。解析器現在：(1) 探測能力而非僅檢查存在（用 --permission-mode dontAsk --version 測試）；(2) 優先最新能力版本；(3) 失敗時大聲失敗、不沉默；(4) 成功分辨率快取 15 分鐘、失敗不快取、CLI 更新自動拾取；(5) 保留 2KB stderr 尾部用於診斷。"
key_points:
  - "CLI 能力探測策略：用 --permission-mode dontAsk --version 測試各候選，跳過 2.1.x 前舊二進制檔，優先最新版本"
  - "快取與自修復：成功分辨率快取 15 分鐘（CLI 更新自動拾起無需重啟）、失敗不快取、失敗重試"
  - "可見性改進：保留 2KB stderr 尾部在退出警告中、明確舊版本路徑和版本號、flag 解析失敗不再默默崩潰"
tags: [claude-mem, cli-compatibility, reliability, observer, version-detection]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.5.7

claude-mem v13.5.7 修復陳舊 Claude CLI 默默殺死每個觀察的問題（#2911）。根本原因：被棄用的 npm-global claude 二進制檔在 PATH 中排在當前安裝前，每個 Observer 生成在 flag 解析時立即崩潰，worker 健康但零觀察且日誌無記錄。解析器現在：(1) 探測能力而非僅檢查存在（用 --permission-mode dontAsk --version 測試）；(2) 優先最新能力版本；(3) 失敗時大聲失敗、不沉默；(4) 成功分辨率快取 15 分鐘、失敗不快取、CLI 更新自動拾取；(5) 保留 2KB stderr 尾部用於診斷。

### 重點
- CLI 能力探測策略：用 --permission-mode dontAsk --version 測試各候選，跳過 2.1.x 前舊二進制檔，優先最新版本
- 快取與自修復：成功分辨率快取 15 分鐘（CLI 更新自動拾起無需重啟）、失敗不快取、失敗重試
- 可見性改進：保留 2KB stderr 尾部在退出警告中、明確舊版本路徑和版本號、flag 解析失敗不再默默崩潰

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.5.7)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.5.7

What's Fixed 
 Stale Claude CLI can no longer silently kill every observation ( #2911 ) 
 If an abandoned npm-global claude binary sat earlier in PATH than your current install, every Observer spawn died instantly at flag parsing — worker healthy, zero observations, nothing in the logs. The resolver now: 
 
 Probes every candidate for capability , not just existence: each CLI is tested with --permission-mode dontAsk --version , the exact flags claude-mem passes on every agent spawn. Binaries that reject them (older than the 2.1.x line) are skipped up front with a clear warning. 
 Prefers the newest capable version — PATH order only breaks ties, so a stale binary can't shadow a current one. 
 Fails loud, never silent : an explicit CLAUDE_CODE_PATH that's too old throws with the version and the remedy; if every CLI found is too old, the error names each path and version. 
 Self-heals on CLI updates : successful resolutions are cached 15 minutes, failures are never cached — updating your CLI is picked up on the next observation without a worker restart. 
 Keeps a 2KB stderr tail from SDK children, included in exit warnings (and read on close , so it's never truncated) — a CLI dying at flag parsing now says why at default log level. 
 
 Build 
 
 Bundle-size budgets are now advisory warnings instead of hard build failures.

</details>