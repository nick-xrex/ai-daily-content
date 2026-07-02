---
id: inbox_4b6424fd
date: 2026-06-30
source_ref: "[[00-inbox/.../inbox_4b6424fd]]"
title: "v6.1.0"
url: https://github.com/obra/superpowers/releases/tag/v6.1.0
source: superpowers-releases
published_at: 2026-06-30T18:42:18+00:00
fetched_at: 2026-07-02T01:14:54.816587+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "superpowers v6.1.0 聚焦單次會話令牌成本最佳化。using-superpowers bootstrap 注入每個會話，固定成本極高，本版本壓縮 bootstrap 本體和工具對應表，移除 graphviz 技能流圖改為純文本敘述、折疊獨立指令優先級章節、刪除平台特定的「技能訪問」逐步指南，保留紅旗識別表與優先級規則不變。Codex 側修復：Codex 市場安裝現支援 repository-local manifest 指向同根目錄，移除 Codex SessionStart hook（已可自動觸發），刪除 hooks-codex.json。開發工具方面：移除 Gemini CLI 支援（Google 2026-06-18 停用）及其工具對應參考。"
key_points:
  - "Bootstrap 壓縮：移除圖表、簡化工具表單、保留核心邏輯，降低固定會話開銷"
  - "Codex 市場支援：新增 marketplace.json manifest（repository-local），移除冗餘 SessionStart hook"
  - "平台整理：Gemini CLI 停用移除（Google EOL 2026-06-18），刪除過時平台參考文件"
tags: [superpowers, token-cost, codex, harness-optimization]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v6.1.0

superpowers v6.1.0 聚焦單次會話令牌成本最佳化。using-superpowers bootstrap 注入每個會話，固定成本極高，本版本壓縮 bootstrap 本體和工具對應表，移除 graphviz 技能流圖改為純文本敘述、折疊獨立指令優先級章節、刪除平台特定的「技能訪問」逐步指南，保留紅旗識別表與優先級規則不變。Codex 側修復：Codex 市場安裝現支援 repository-local manifest 指向同根目錄，移除 Codex SessionStart hook（已可自動觸發），刪除 hooks-codex.json。開發工具方面：移除 Gemini CLI 支援（Google 2026-06-18 停用）及其工具對應參考。

### 重點
- Bootstrap 壓縮：移除圖表、簡化工具表單、保留核心邏輯，降低固定會話開銷
- Codex 市場支援：新增 marketplace.json manifest（repository-local），移除冗餘 SessionStart hook
- 平台整理：Gemini CLI 停用移除（Google EOL 2026-06-18），刪除過時平台參考文件

**原文：** [superpowers-releases](https://github.com/obra/superpowers/releases/tag/v6.1.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v6.1.0

Lower Per-Session Token Cost 
 The using-superpowers bootstrap is injected into every session, so its size is paid for constantly. This release trims it and the per-harness references it points to, without dropping behavior-shaping content. 
 
 Compressed the using-superpowers bootstrap. Replaced the graphviz skill-flow diagram with the prose it encoded, folded the standalone Instruction-Priority section into User Instructions, dropped the per-platform "How to Access Skills" walkthrough, and trimmed the Platform Adaptation pointer to the harnesses that still ship a reference file. The full Red Flags rationalization table and the user-instruction precedence rules are unchanged. 
 Pruned the per-harness tool-mapping references. The verbose action-to-tool tables restated guidance modern agents already follow. Each reference file is trimmed to the harness-specific notes that still carry weight — subagent dispatch, task tracking, instructions-file paths — and claude-code-tools.md and copilot-tools.md , which had nothing harness-specific left, are deleted. 
 
 Codex 
 
 Codex can install from the marketplace. Codex marketplace sources expect a .agents/plugins/marketplace.json at the marketplace root; the repo only shipped the Claude marketplace file, so Codex could name the marketplace but found no installable plugin entries. A repo-local Codex marketplace manifest now points at the same repository root, so the plugin is installable from Codex. 
 Codex no longer ships a SessionStart hook. Codex reliably triggers skills on its own, and the bootstrap hook made the UX worse rather than better. The Codex hook config ( hooks-codex.json ) and its manifest registration are removed. 
 
 Harness Support 
 
 Gemini CLI support removed. Google EOLed the Gemini CLI on 2026-06-18; the extension can no longer be installed or updated. Gemini is gone from the install docs, the subagent-capable platform lists, and the eval-harness description, and its tool-mapping reference is deleted.

</details>