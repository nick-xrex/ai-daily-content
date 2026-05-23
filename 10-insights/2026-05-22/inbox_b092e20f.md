---
id: inbox_b092e20f
date: 2026-05-22
source_ref: "[[00-inbox/2026-05-22/1800-gitnexus-releases-rc-954b1842486bd381c80133d68ef08de4872d2-72c1]]"
title: "rc/954b1842486bd381c80133d68ef08de4872d28cf: fix(cli): apply --no-stats to keep-marker stats line (#1706) (#1765)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F954b1842486bd381c80133d68ef08de4872d28cf
source: gitnexus-releases
published_at: 2026-05-22T06:03:40+00:00
fetched_at: 2026-05-22T18:06:42.967018+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 修復：--no-stats 旗標在 keep-marker 路徑被忽略問題。keep-marker 分支每次分析時重建 index-summary 行，總是重新注入易變計數（符號數、檔案數等），導致 --no-stats 被無視。對於提交帶 gitnexus:keep marker 的 AGENTS.md/CLAUDE.md 的團隊，此行為產生反覆無價值的合併衝突，正是 --no-stats 設計用來防止的。解決方案：將 noStats 參數傳入 upsertGitNexusSection。應用 --no-stats 時，keep 路徑統計行簡化為「Indexed as」，移除 (N symbols, ...) 括號；項目名仍刷新以支持重命名。新增測試驗證計數返回（防旗標粘滯）和 AGENTS.md/CLAUDE.md 兼容性。"
key_points:
  - "--no-stats 在 keep-marker 路徑被忽略，導致每次分析重新注入易變計數 → 反覆合併衝突"
  - "解決方案：noStats 參數傳入 upsertGitNexusSection；--no-stats 時統計行變「Indexed as」，無計數括號"
  - "新增測試確保計數返回防旗標粘滯、AGENTS.md 和 CLAUDE.md 兼容性一致（避免未來不對稱）"
tags: [gitnexus, keep-marker, cli, merge-conflict]
topics: []
importance: 2
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/954b1842486bd381c80133d68ef08de4872d28cf: fix(cli): apply --no-stats to keep-marker stats line (#1706) (#1765)

GitNexus 修復：--no-stats 旗標在 keep-marker 路徑被忽略問題。keep-marker 分支每次分析時重建 index-summary 行，總是重新注入易變計數（符號數、檔案數等），導致 --no-stats 被無視。對於提交帶 gitnexus:keep marker 的 AGENTS.md/CLAUDE.md 的團隊，此行為產生反覆無價值的合併衝突，正是 --no-stats 設計用來防止的。解決方案：將 noStats 參數傳入 upsertGitNexusSection。應用 --no-stats 時，keep 路徑統計行簡化為「Indexed as」，移除 (N symbols, ...) 括號；項目名仍刷新以支持重命名。新增測試驗證計數返回（防旗標粘滯）和 AGENTS.md/CLAUDE.md 兼容性。

### 重點
- --no-stats 在 keep-marker 路徑被忽略，導致每次分析重新注入易變計數 → 反覆合併衝突
- 解決方案：noStats 參數傳入 upsertGitNexusSection；--no-stats 時統計行變「Indexed as」，無計數括號
- 新增測試確保計數返回防旗標粘滯、AGENTS.md 和 CLAUDE.md 兼容性一致（避免未來不對稱）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F954b1842486bd381c80133d68ef08de4872d28cf)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(cli): apply --no-stats to keep-marker stats line ( #1706 ) 
 
 The keep-marker branch of upsertGitNexusSection rebuilt the index-summary 
line on every analyze and always re-injected the volatile counts, 
ignoring --no-stats. For teams that commit a trimmed AGENTS.md/CLAUDE.md 
with a gitnexus:keep marker, that produced recurring no-value merge 
conflicts — exactly what --no-stats exists to prevent. 
 Thread noStats into upsertGitNexusSection. Under --no-stats the keep-path 
stats line becomes "Indexed as " with no (N symbols, ...) 
parenthetical; the project name still refreshes so renames propagate. 
The statsPattern parenthetical is now optional so a count-free line left 
by a prior --no-stats run still matches. 
 
 test(cli): cover count-return and AGENTS.md parity for --no-stats keep path 
 
 Addresses review findings F1 and F2 on PR #1765 : 
 
 F1: add a test that counts RETURN when --no-stats is dropped after a 
prior count-free run — guards against the flag becoming sticky. 
 F2: extend the noStats+keep "drops the volatile counts" test to assert 
AGENTS.md alongside CLAUDE.md, so a future asymmetry between the two 
upsertGitNexusSection call sites is caught. 
 
 
 Co-authored-by: Emmanuel Alawode platforms@chowbea.com 
Co-authored-by: Gergő Magyar gergomagyar@icloud.com

</details>