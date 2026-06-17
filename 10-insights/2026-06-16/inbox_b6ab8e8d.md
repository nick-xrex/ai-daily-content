---
id: inbox_b6ab8e8d
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-ruflo-releases-v3-11-0-router-adr-148-149-cost-tracker-8500]]"
title: "v3.11.0 — router ADR-148/149 + cost-tracker observability + fleet audits"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.11.0
source: ruflo-releases
published_at: 2026-06-16T16:13:38+00:00
fetched_at: 2026-06-16T22:06:44.942896+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.11.0 版本發布（PR #2398 壓縮合併）。路由層實現 ADR-148（FastGRNN 路由器生命週期管理）和 ADR-149（per-model 成本最優決策），新增 task_hash 去重；Cost-tracker 插件引入完整可觀測棧（投影、反事實、燃速、異常檢測 MAD、複合健康度檢查、PR 回歸比較、消息級鑽取），支持 stop-hook 自動追蹤與 git 上下文快照；4 層閉合 cache-write 可見性（消息級、時序、摘要、diff），揭示 cache_creation_input_tokens 為隱藏成本驅動；Fleet 級 CI 涵蓋 32 個插件、402+ 結構不變量、SKILL.md 前置詞審計（117 文件）、plugin.json 清單審計（34 文件），支持 per-plugin timeout 與 --fail-fast 配置。"
key_points:
  - "Router 層：ADR-148/149 實現 FastGRNN 與 per-model 成本最優路由，task_hash 去重修復"
  - "Cost-tracker 可觀測：projection / anomaly(MAD) / health gate / session drill-down，cache_creation_input_tokens 成本可見化"
  - "Fleet CI 規模：32 插件、402+ 結構不變量、audit 自動化（SKILL.md frontmatter、plugin.json manifest）"
tags: [ruflo, router, cost-optimization, observability, fleet-ci]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.11.0 — router ADR-148/149 + cost-tracker observability + fleet audits

Ruflo v3.11.0 版本發布（PR #2398 壓縮合併）。路由層實現 ADR-148（FastGRNN 路由器生命週期管理）和 ADR-149（per-model 成本最優決策），新增 task_hash 去重；Cost-tracker 插件引入完整可觀測棧（投影、反事實、燃速、異常檢測 MAD、複合健康度檢查、PR 回歸比較、消息級鑽取），支持 stop-hook 自動追蹤與 git 上下文快照；4 層閉合 cache-write 可見性（消息級、時序、摘要、diff），揭示 cache_creation_input_tokens 為隱藏成本驅動；Fleet 級 CI 涵蓋 32 個插件、402+ 結構不變量、SKILL.md 前置詞審計（117 文件）、plugin.json 清單審計（34 文件），支持 per-plugin timeout 與 --fail-fast 配置。

### 重點
- Router 層：ADR-148/149 實現 FastGRNN 與 per-model 成本最優路由，task_hash 去重修復
- Cost-tracker 可觀測：projection / anomaly(MAD) / health gate / session drill-down，cache_creation_input_tokens 成本可見化
- Fleet CI 規模：32 插件、402+ 結構不變量、audit 自動化（SKILL.md frontmatter、plugin.json manifest）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.11.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merged PR #2398 (squash). 
 Highlights 
 
 Router (v3/@claude-flow/cli) : ADR-148 FastGRNN router artifact lifecycle, ADR-149 per-model cost-optimal routing, Map&lt;task_hash&gt; dedup fixes across decisions/cost-savings/cost-projection. 
 Cost-tracker plugin : forward observability stack — projection / counterfactual / burn / anomaly (MAD) / health (composite gate) / diff (PR regression) / session (per-message drill-down). Stop-hook auto-track. Snapshot git-context. 
 Cache-write visibility : closed at four layers (per-message, time-series, summary, diff) — cache_creation_input_tokens was the silent cost driver. 
 Fleet-wide CI : meta-smoke runner across 32 plugins (402+ structural invariants), exit-bypass antipattern lint, SKILL.md frontmatter audit (117 files), plugin.json manifest audit (34 files), per-plugin timeout/ --fail-fast . 
 
 Install 
 npx ruflo@latest # latest stable 
npx @claude-flow/cli@latest 
 Legacy alpha and v3alpha dist-tags also updated to 3.11.0.

</details>