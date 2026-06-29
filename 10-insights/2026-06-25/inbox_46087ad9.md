---
id: inbox_46087ad9
date: 2026-06-25
source_ref: "[[00-inbox/.../inbox_46087ad9]]"
title: "v3.14.2 — fix Windows embedding crash (#2461)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.14.2
source: ruflo-releases
published_at: 2026-06-25T22:07:11+00:00
fetched_at: 2026-06-29T00:56:10.456756+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.14.2 修復了 Windows 環境下嵌入系統的多個連鎖崩潰（#2461），涉及三個獨立但相關的 bug：(1) loadEmbeddingModel() 在 @xenova/transformers 無法從遠程取得模型時即中止，未能回退到內建的 ruvector ONNX；(2) generateLocalEmbedding() 對空狀態進行解引用導致崩潰；(3) memory store 在未指定 -n 參數時將嵌入儲存在字面的「undefined」命名空間，造成靜默資料遺失。此修復對企業環境尤為重要，因為企業代理或防火牆常阻止遠程模型文件下載。官方驗證顯示 50/50 發布版和 100/100 本地無網狀態均達 100% 成功率（之前首次調用即崩潰）。三個相關套件 @claude-flow/cli、claude-flow、ruflo 已全部同步至 v3.14.2。"
key_points:
  - "修復 Windows 嵌入三個連鎖崩潰：transformers 例外未回退、null 解引用、命名空間儲存靜默失敗"
  - "強化離線或代理環境下的模型載入容錯（回退到內建 ONNX）"
  - "50/50 發布版和 100/100 離線驗證達成，解決企業代理場景的阻斷"
tags: [ruflo, embedding, windows, memory-store, error-handling]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.14.2 — fix Windows embedding crash (#2461)

Ruflo v3.14.2 修復了 Windows 環境下嵌入系統的多個連鎖崩潰（#2461），涉及三個獨立但相關的 bug：(1) loadEmbeddingModel() 在 @xenova/transformers 無法從遠程取得模型時即中止，未能回退到內建的 ruvector ONNX；(2) generateLocalEmbedding() 對空狀態進行解引用導致崩潰；(3) memory store 在未指定 -n 參數時將嵌入儲存在字面的「undefined」命名空間，造成靜默資料遺失。此修復對企業環境尤為重要，因為企業代理或防火牆常阻止遠程模型文件下載。官方驗證顯示 50/50 發布版和 100/100 本地無網狀態均達 100% 成功率（之前首次調用即崩潰）。三個相關套件 @claude-flow/cli、claude-flow、ruflo 已全部同步至 v3.14.2。

### 重點
- 修復 Windows 嵌入三個連鎖崩潰：transformers 例外未回退、null 解引用、命名空間儲存靜默失敗
- 強化離線或代理環境下的模型載入容錯（回退到內建 ONNX）
- 50/50 發布版和 100/100 離線驗證達成，解決企業代理場景的阻斷

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.14.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.14.2 — fix Windows embedding crash (#2461)

Patch release fixing a Windows-on-proxy crash and a silent data-loss bug in `memory store`. 
 Fixes 
 
 
 #2461 — `ruflo memory store` / `memory search` crashed with `Cannot read properties of null (reading 'model')` whenever `@xenova/transformers` couldn't fetch model files (corporate proxy, strict firewall, offline). Three independent bugs in the same path: 
 
 `loadEmbeddingModel()` aborted on transformers throw; never reached the working ruvector ONNX fallback that ships in-tree. 
 `generateLocalEmbedding()` then crashed dereferencing the null state. 
 `memory store` without `-n` stored under literal namespace `"undefined"` (silent data loss). 
 
 All three fixed in this release. 
 
 
 Verification 
 
 50× `generateLocalEmbedding` on the published `ruflo@3.14.2` artifact → 50/50 success, 0 crashes 
 100× the same call locally with every embedder module unresolvable → 100/100 success (was: crash on call #1 ) 
 `@claude-flow/cli` builds clean 
 
 Install 
 ```bash 
npx ruflo@3.14.2 
 or 
 npx @claude-flow/cli@3.14.2 
``` 
 All three packages — `@claude-flow/cli`, `claude-flow`, `ruflo` — at 3.14.2 with consistent `latest` / `alpha` / `v3alpha` dist-tags. 
 Credits 
 @Pishro-canadaapply filed #2461 with full root-cause analysis and a proposed fix; this release implements it. 
 PR 
 #2467 — diff and per-commit history.

</details>