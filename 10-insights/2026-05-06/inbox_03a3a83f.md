---
id: inbox_03a3a83f
date: 2026-05-06
source_ref: "[[00-inbox/.../inbox_03a3a83f]]"
title: "v12.7.2"
url: https://github.com/thedotmack/claude-mem/releases/tag/v12.7.2
source: claude-mem-releases
published_at: 2026-05-06T10:34:46+00:00
fetched_at: 2026-06-11T00:28:36.576233+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Mem v12.7.2 發佈，主要改進包括三項安全相關的修復：(1) 新增環境變數 CLAUDE_CODE_DISABLE_AUTO_MEMORY=1 用於在安裝 Claude Code 時禁用自動內存功能；(2) 強化 JSON 配置檔案寫入的原子性、耐久性與符號連結安全性，確保在異常中斷時不會破壞配置；(3) 新增回歸測試以驗證通過符號連結與懸掛符號連結路徑進行的原子 JSON 寫操作。此版本著重於改善配置持久化的可靠性與用户的內存管理彈性。"
key_points:
  - "新增 CLAUDE_CODE_DISABLE_AUTO_MEMORY 環境變數，允許使用者在安裝時關閉自動內存"
  - "JSON 配置寫入改進為原子性、耐久性、符號連結安全與懸掛符號連結安全"
  - "新增自動化回歸測試涵蓋所有邊界情況，防止配置損毀"
tags: [claude-mem, reliability, config-safety, v12.7.2]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v12.7.2

Claude Mem v12.7.2 發佈，主要改進包括三項安全相關的修復：(1) 新增環境變數 CLAUDE_CODE_DISABLE_AUTO_MEMORY=1 用於在安裝 Claude Code 時禁用自動內存功能；(2) 強化 JSON 配置檔案寫入的原子性、耐久性與符號連結安全性，確保在異常中斷時不會破壞配置；(3) 新增回歸測試以驗證通過符號連結與懸掛符號連結路徑進行的原子 JSON 寫操作。此版本著重於改善配置持久化的可靠性與用户的內存管理彈性。

### 重點
- 新增 CLAUDE_CODE_DISABLE_AUTO_MEMORY 環境變數，允許使用者在安裝時關閉自動內存
- JSON 配置寫入改進為原子性、耐久性、符號連結安全與懸掛符號連結安全
- 新增自動化回歸測試涵蓋所有邊界情況，防止配置損毀

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v12.7.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v12.7.2

v12.7.2 
 Fixed 
 
 Disable Claude Code built-in auto-memory during claude-code installs by setting CLAUDE_CODE_DISABLE_AUTO_MEMORY=1 in Claude settings. 
 Make JSON config writes crash-safe, durable, symlink-safe, and safe for dangling symlink destinations. 
 Add regression coverage for atomic JSON writes through symlinked and dangling-symlink settings paths.

</details>