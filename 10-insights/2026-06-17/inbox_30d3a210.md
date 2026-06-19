---
id: inbox_30d3a210
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-ruflo-releases-v3-12-3-2395-fix-mcp-no-longer-emits-128-0d63]]"
title: "v3.12.3 — #2395 fix: MCP no longer emits 128-dim mock embeddings"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.12.3
source: ruflo-releases
published_at: 2026-06-17T23:38:59+00:00
fetched_at: 2026-06-18T22:06:56.774859+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.12.3 修復 MCP memory_store 的資料質量迴歸：在會話內 MCP 路徑堅持發送 128 維 mock embeddings，而獨立 CLI 使用真實 384 維 ONNX embedding，導致相似度召回失效。根本原因：AgentDB 的 vectorBackend 控制器在無可用後端時 silent fallback 至 128 維雜湊樁，但 bridgeGenerateEmbedding 仍無條件標籤結果為 `backend: 'onnx'` 且未設置 `isMock=true`，使得既有的 isMock 檢查無法攔截虛假結果。修復方案：對回傳結果做維度檢查——簽名模型 Xenova/all-MiniLM-L6-v2 固定產生 384 維；若維度非 384，判定為樁並從 bridge 回傳 null，讓呼叫方落回 generateLocalEmbedding，正確路由至真實 ONNX 鏈（transformers.js / ruvector）。結果：backend 標籤語義恢復正確，向量記憶品質不再遭到 silent 汙染。"
key_points:
  - "Silent fallback 品質迴歸：MCP in-session path 發送 128 維雜湊樁 embedding，獨立 CLI 發送 384 維真實 ONNX，similarity recall 無效化，向量記憶功能喪失"
  - "維度檢查修復邏輯：Xenova/all-MiniLM-L6-v2 簽名 = 384 維；非 384 維則判定為樁，bridge 回傳 null 強制回落 generateLocalEmbedding → transformers.js/ruvector 的真實 ONNX 鏈"
  - "根本問題：vectorBackend 的樁實裝未暴露 isMock=true，導致 bridgeGenerateEmbedding 無法辨別虛實"
tags: [embedding-quality, mcp-memory-store, silent-fallback-pattern, dimensional-check]
topics: [agents.mcp]
importance: 4
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.12.3 — #2395 fix: MCP no longer emits 128-dim mock embeddings

ruflo v3.12.3 修復 MCP memory_store 的資料質量迴歸：在會話內 MCP 路徑堅持發送 128 維 mock embeddings，而獨立 CLI 使用真實 384 維 ONNX embedding，導致相似度召回失效。根本原因：AgentDB 的 vectorBackend 控制器在無可用後端時 silent fallback 至 128 維雜湊樁，但 bridgeGenerateEmbedding 仍無條件標籤結果為 `backend: 'onnx'` 且未設置 `isMock=true`，使得既有的 isMock 檢查無法攔截虛假結果。修復方案：對回傳結果做維度檢查——簽名模型 Xenova/all-MiniLM-L6-v2 固定產生 384 維；若維度非 384，判定為樁並從 bridge 回傳 null，讓呼叫方落回 generateLocalEmbedding，正確路由至真實 ONNX 鏈（transformers.js / ruvector）。結果：backend 標籤語義恢復正確，向量記憶品質不再遭到 silent 汙染。

### 重點
- Silent fallback 品質迴歸：MCP in-session path 發送 128 維雜湊樁 embedding，獨立 CLI 發送 384 維真實 ONNX，similarity recall 無效化，向量記憶功能喪失
- 維度檢查修復邏輯：Xenova/all-MiniLM-L6-v2 簽名 = 384 維；非 384 維則判定為樁，bridge 回傳 null 強制回落 generateLocalEmbedding → transformers.js/ruvector 的真實 ONNX 鏈
- 根本問題：vectorBackend 的樁實裝未暴露 isMock=true，導致 bridgeGenerateEmbedding 無法辨別虛實

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.12.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Bundled fix 
 #2395 — MCP memory_store emitted 128-dim mock embeddings (data quality regression) 
 Symptom (per issue): standalone CLI used real 384-dim ONNX embeddings, but the in-session MCP path persistently emitted 128-dim hash-fallback ("mock") embeddings — silently corrupting similarity recall and wasting any benefit of vector memory. 
 Root cause: bridgeGenerateEmbedding returned embedder.embed() results labeled backend: 'onnx' unconditionally, even when AgentDB's vectorBackend controller silently fell back to a 128-dim hash stub. The stub didn't expose isMock=true , so the existing isMock check let it through with a wrong label. 
 Fix: dimensional sanity check. The hardcoded model name Xenova/all-MiniLM-L6-v2 always produces 384-dim; anything else is definitively a stub. Return null from the bridge wrapper in that case so the caller falls through to generateLocalEmbedding , which routes via the real ONNX chain (transformers.js / ruvector). 
 Net: backend labels now match actual semantics, no more silent mock embeddings. 
 Install 
 npx ruflo@3.12.3
 # or 
npm i ruflo@latest 
 All 3 packages × 3 dist-tags published in lockstep. 
 🤖 Generated with RuFlo

</details>