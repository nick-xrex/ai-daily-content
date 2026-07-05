---
id: inbox_44f9204f
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/2200-ruflo-releases-v3-22-0-memory-distillation-loop-page-ag-187b]]"
title: "v3.22.0 — memory distillation loop + page-agent intent + signed hook auto-refresh"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.22.0
source: ruflo-releases
published_at: 2026-07-04T21:13:02+00:00
fetched_at: 2026-07-04T22:05:43.756826+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.22.0 推出四大新功能，重點聚焦代理自學習與執行安全。首先，ADR-174 記憶蒸餾自學習循環將記憶項目分析轉化為集節點、推理模式及弱關係圖譜，訓練本地 SONA/MoE 模型，成本零起點且非破壞性。其次，失敗信號捕捉改進執行追蹤：hook 過往固定輸出 success:true（898/898 成功），現改讀取 Claude Code 的 PostToolUse 結果，記錄真實失敗以供預言機層學習負例。第三，ADR-175 page-agent 新增自然語言瀏覽意圖工具（browser_act MCP），移除不安全的 Alibaba 沙箱自動連接，改以 LLM 代理持有金鑰而非暴露頁面上下文。第四，版本戳記的 Ed25519 簽名自動刷新機制確保 hook 升級無需手動 re-init，通過 GCP Secret Manager 金鑰防止篡改，fail-closed 設計。"
key_points:
  - "ADR-174 記憶蒸餾循環：memory_entries → episodes → reasoning_patterns → 弱關係邊，訓練本地 MoE 模型，零成本增量"
  - "失敗信號捕捉：hooks 改錄真實 PostToolUse 結果而非硬編碼 success:true，為預言機層提供負例"
  - "ADR-175 browser_act MCP 工具：自然語言瀏覽意圖，LLM 金鑰隔離代理，fail-closed 設計"
tags: [memory-distillation, agent-learning, failure-signals, mcp-tools]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.22.0 — memory distillation loop + page-agent intent + signed hook auto-refresh

RuFlo v3.22.0 推出四大新功能，重點聚焦代理自學習與執行安全。首先，ADR-174 記憶蒸餾自學習循環將記憶項目分析轉化為集節點、推理模式及弱關係圖譜，訓練本地 SONA/MoE 模型，成本零起點且非破壞性。其次，失敗信號捕捉改進執行追蹤：hook 過往固定輸出 success:true（898/898 成功），現改讀取 Claude Code 的 PostToolUse 結果，記錄真實失敗以供預言機層學習負例。第三，ADR-175 page-agent 新增自然語言瀏覽意圖工具（browser_act MCP），移除不安全的 Alibaba 沙箱自動連接，改以 LLM 代理持有金鑰而非暴露頁面上下文。第四，版本戳記的 Ed25519 簽名自動刷新機制確保 hook 升級無需手動 re-init，通過 GCP Secret Manager 金鑰防止篡改，fail-closed 設計。

### 重點
- ADR-174 記憶蒸餾循環：memory_entries → episodes → reasoning_patterns → 弱關係邊，訓練本地 MoE 模型，零成本增量
- 失敗信號捕捉：hooks 改錄真實 PostToolUse 結果而非硬編碼 success:true，為預言機層提供負例
- ADR-175 browser_act MCP 工具：自然語言瀏覽意圖，LLM 金鑰隔離代理，fail-closed 設計

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.22.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 
 ADR-174 — Memory distillation self-learning loop. The daemon's consolidate worker was a stub writing zeros; it now really mines memory_entries → episodes → reasoning_patterns (+embeddings) → weak relational edges. $0 default, incremental, non-destructive, provenance-gated (ADR-171). memory distill run|status|config CLI + self-optimization ( distill-tuning ). Trains the local SONA/MoE model on your own memory. 
 Failure-signal capture. Hooks recorded a hardcoded success:true (898/898, 0 failures) — now they read Claude Code's PostToolUse outcome and record real failures, so the oracle tier finally has negative examples. 
 ADR-175 — page-agent browser intent. New browser_act MCP tool: natural-language intents on top of the selector tools. Strips page-agent's demo auto-connect to Alibaba's sandbox (fail-closed firewall) and proxies the LLM key so it never enters page context. 
 Version-stamped helper auto-refresh (secured). Hook fixes now propagate to every project on the next ruflo command — no re-init — gated by an Ed25519 signed manifest (key in GCP Secret Manager); a tampered helper is refused, not propagated. 
 
 Also: statusline vector-count + corruption auto-recovery ( #2569 ), memory-search recall ( #2558 ), agenticow/memory perf. 
 All backward-compatible additions. 3-package train ( @claude-flow/cli , claude-flow , ruflo ) at 3.22.0. 
 🤖 Generated with RuFlo

</details>