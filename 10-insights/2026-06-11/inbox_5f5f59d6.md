---
id: inbox_5f5f59d6
date: 2026-06-11
source_ref: "[[00-inbox/2026-06-11/2200-ruflo-releases-v3-10-42-community-bug-batch-windows-pat-a617]]"
title: "v3.10.42 — community bug batch: Windows path validation, trajectory feedback, init hooks"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.42
source: ruflo-releases
published_at: 2026-06-11T15:04:38+00:00
fetched_at: 2026-06-11T22:06:45.739446+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.42 補丁版本修復社區回報的三個臭蟲，針對 Claude Code hook 系統。第一，#2352 修正 Windows 路徑驗證——validatePath 函式將反斜線判為 shell 特殊字元，導致絕對路徑（如 E:\Repos\...）被拒；修復後改為檢查 result.success 欄位並妥善顯示錯誤。第二，#2351 解決 trajectory-end 回饋未被蒸餾為可搜尋 pattern——LLM agent 無步驟記錄時的回饋現已透過 bridge.bridgeStorePattern 納入索引，新增 feedbackDistilled 欄位。第三，#2350 修復 init hooks 子命令未寫入設定檔的問題，方法是在該子命令中納入 helpers。新增 22 項 Windows 路徑驗證測試，所有既有測試仍通過。"
key_points:
  - "Windows 路徑驗證修復（#2352）——改進 validatePath 邏輯以正確辨識 Windows 絕對路徑"
  - "無步驟回饋的 pattern 蒸餾（#2351）——透過 bridge.bridgeStorePattern 實現 LLM agent 反饋可搜尋化"
  - "init hooks 設定生成修復（#2350）——helpers 納入子命令以確保 hooks 區塊正常寫入"
tags: [claude-code, hooks, windows-compatibility, mcp]
topics: [agents.mcp]
importance: 3
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.42 — community bug batch: Windows path validation, trajectory feedback, init hooks

Ruflo v3.10.42 補丁版本修復社區回報的三個臭蟲，針對 Claude Code hook 系統。第一，#2352 修正 Windows 路徑驗證——validatePath 函式將反斜線判為 shell 特殊字元，導致絕對路徑（如 E:\Repos\...）被拒；修復後改為檢查 result.success 欄位並妥善顯示錯誤。第二，#2351 解決 trajectory-end 回饋未被蒸餾為可搜尋 pattern——LLM agent 無步驟記錄時的回饋現已透過 bridge.bridgeStorePattern 納入索引，新增 feedbackDistilled 欄位。第三，#2350 修復 init hooks 子命令未寫入設定檔的問題，方法是在該子命令中納入 helpers。新增 22 項 Windows 路徑驗證測試，所有既有測試仍通過。

### 重點
- Windows 路徑驗證修復（#2352）——改進 validatePath 邏輯以正確辨識 Windows 絕對路徑
- 無步驟回饋的 pattern 蒸餾（#2351）——透過 bridge.bridgeStorePattern 實現 LLM agent 反饋可搜尋化
- init hooks 設定生成修復（#2350）——helpers 納入子命令以確保 hooks 區塊正常寫入

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.42)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release fixing three reproducible community bugs reported by @grym3s , batched in the style of v3.10.41 / PR #2346 . 
 Fixes 
 #2352 — hooks post-edit : Windows paths rejected, failure printed as [OK] 
 
 validatePath used the general SHELL_META set which includes \ , so every absolute Windows path ( E:\Repos\... ) failed with "shell metacharacters" . Claude Code hook events deliver absolute paths in tool_input.file_path , so every forwarded post-edit call failed silently on Windows. 
 The CLI action printed [OK] Outcome recorded for ... whenever the MCP call returned at all, masking the failure. Now checks result.success , surfaces the error, and exits non-zero. 
 
 #2351 — trajectory-end : step-less feedback never distilled 
 When trajectory-end is called with feedback but no recorded steps (the common LLM-agent case), the feedback was persisted with the trajectory but never embedded as a searchable pattern — patternsExtracted always reported 0 and pattern-search never surfaced it. Now routes the trimmed feedback through bridge.bridgeStorePattern (or store-fallback) with modest default confidence, tagged trajectory-feedback . New feedbackDistilled.{patternId, controller} field on the response. 
 #2350 — init hooks : subcommand wrote no hooks block to settings.json 
 The settings generator gates the hooks block on components.helpers (the hook commands point at the helper script). The init hooks subcommand had helpers: false , so the one subcommand whose purpose is "Initialize only hooks configuration" produced settings.json with no hooks key while reporting "N hooks enabled" . Helpers now ship with the subcommand. 
 Install / upgrade 
 npx ruflo@latest init # 3.10.42 
npx @claude-flow/cli@latest # 3.10.42 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) and all three dist-tags ( latest , alpha , v3alpha ) are pinned to 3.10.42. 
 Tests 
 
 New validate-input-path-2352.test.ts — 22 tests pin Windows-path acceptance, POSIX still works, all shell metacharacters and traversal still rejected. 
 All existing validate-input , init-wizard-bugs , hooks-intelligence-learning , hooks-post-task tests still pass. 
 
 Diff 
 PR #2355 · main...v3.10.42 
 🤖 Generated with RuFlo

</details>