---
id: inbox_8cd1880f
date: 2026-07-16
source_ref: "[[00-inbox/.../inbox_8cd1880f]]"
title: "0.144.5"
url: https://github.com/openai/codex/releases/tag/rust-v0.144.5
source: codex-releases
published_at: 2026-07-16T02:56:18+00:00
fetched_at: 2026-07-17T00:42:49.930081+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex 釋出 v0.144.5 補丁版本，核心改進為危險指令偵測機制的安全強化。新版本擴大了對 rm 命令的識別涵蓋範圍（包括強制形式如 rm -rf），並在命令被系統拒絕時提供更清晰的拒絕理由與說明，增強了 Codex 在安全執行命令時的防禦能力與使用者體驗。"
key_points:
  - "OpenAI Codex v0.144.5 擴展 is_dangerous_command 邏輯，涵蓋更多強制 rm 命令變體"
  - "改進被拒命令的錯誤訊息清晰度，使使用者更好理解為何命令被阻止（issue #33455）"
  - "補丁聚焦核心安全防禦，強化命令執行的危害檢測與反饋機制"
tags: [codex, dangerous-command-detection, security-hardening, patch-release, rust]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.144.5

OpenAI Codex 釋出 v0.144.5 補丁版本，核心改進為危險指令偵測機制的安全強化。新版本擴大了對 rm 命令的識別涵蓋範圍（包括強制形式如 rm -rf），並在命令被系統拒絕時提供更清晰的拒絕理由與說明，增強了 Codex 在安全執行命令時的防禦能力與使用者體驗。

### 重點
- OpenAI Codex v0.144.5 擴展 is_dangerous_command 邏輯，涵蓋更多強制 rm 命令變體
- 改進被拒命令的錯誤訊息清晰度，使使用者更好理解為何命令被阻止（issue #33455）
- 補丁聚焦核心安全防禦，強化命令執行的危害檢測與反饋機制

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.144.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# 0.144.5

Bug Fixes 
 
 Improved dangerous-command detection, including more forced rm forms, and provides clearer rejection reasons when commands are denied. ( #33455 ) 
 
 Changelog 
 Full Changelog: rust-v0.144.4...rust-v0.144.5 
 
 #33455 [release/0.144] fix(core) expand is_dangerous_command @dylan-hurd-oai

</details>