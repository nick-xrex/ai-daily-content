---
id: inbox_73a89d3d
date: 2026-07-09
source_ref: "[[00-inbox/2026-07-09/0023-codex-releases-0-144-1-208d]]"
title: "0.144.1"
url: https://github.com/openai/codex/releases/tag/rust-v0.144.1
source: codex-releases
published_at: 2026-07-09T23:04:05+00:00
fetched_at: 2026-07-10T00:27:37.940070+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex rust-v0.144.1 發布了 3 項可靠性修復。修復了 GitHub metadata 排序變化導致獨立安裝失敗的問題（#31913）。改進 macOS 套件安裝，code-mode host 現在正確暴露於 codex executable 旁。code mode 增加 fallback 機制，當 host binary 缺失時可回退到嵌入式運行時。整體提升 Codex 跨平台的穩定性。"
key_points:
  - "修復 GitHub metadata 排序變化導致的獨立安裝失敗（#31913）"
  - "macOS 套件安裝現在正確暴露 code-mode host 與 codex executable"
  - "Code mode 支援 host binary 缺失時的嵌入式運行時 fallback 機制"
tags: [openai-codex, bug-fix, installer-reliability, macos]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.144.1

OpenAI Codex rust-v0.144.1 發布了 3 項可靠性修復。修復了 GitHub metadata 排序變化導致獨立安裝失敗的問題（#31913）。改進 macOS 套件安裝，code-mode host 現在正確暴露於 codex executable 旁。code mode 增加 fallback 機制，當 host binary 缺失時可回退到嵌入式運行時。整體提升 Codex 跨平台的穩定性。

### 重點
- 修復 GitHub metadata 排序變化導致的獨立安裝失敗（#31913）
- macOS 套件安裝現在正確暴露 code-mode host 與 codex executable
- Code mode 支援 host binary 缺失時的嵌入式運行時 fallback 機制

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.144.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Bug Fixes 
 
 Fixed standalone installs failing when GitHub returns compact or reordered release metadata. ( #31913 ) 
 Ensured macOS package installs expose the code-mode host alongside the codex executable. ( #31913 ) 
 Kept code mode working when the companion host binary is unavailable by falling back to the embedded runtime. ( #31913 ) 
 
 Changelog 
 Full Changelog: rust-v0.144.0...rust-v0.144.1 
 
 #31913 [0.144] Backport installer and code-mode reliability fixes @bolinfest

</details>