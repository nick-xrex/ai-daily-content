---
id: inbox_c33e9ec2
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_c33e9ec2]]"
title: "v13.5.3"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.5.3
source: claude-mem-releases
published_at: 2026-06-10T06:09:24+00:00
fetched_at: 2026-06-11T00:23:32.321188+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.5.3 修復 session_compressed 遙測資料品質四項 bug，所有分析數字現源於真實、提供者報告的資料。Claude token 計數修正：從 assistant message 的早期流式快照（8-10 token）改為 SDK 結果消息的真實計數（實測原 8 改 45），壓縮比從荒謬 6,000–38,000 降至真實 ~10–100。成本資料真實化：Claude 從 SDK cumulative total_cost_usd，OpenRouter 從 usage.cost + cost_details.upstream_inference_cost，Gemini 誠實為空（絕不估計）。模型規範化：使用 response.model 而非配置字串，陣列型設定標準化，error-path 也帶入，未知值不再隱沒。新增 install-state snapshot：worker_started 報告觀測/會話/摘要/專案計數、DB 大小、安裝年齡、7/30 天觀測數，啟用留存世代切片。"
key_points:
  - "Token 計數真實化：從 SDK 早期流式的 2-10 改為結果消息真實計數，壓縮比從 6,000x 荒謬值降至 10-100x 合理值，驗證 placeholder 8 vs result 45"
  - "成本資料精確化：Claude (SDK cumulative total_cost_usd) / OpenRouter (usage.cost + upstream_inference_cost) / Gemini (honest null) 三 provider 對齐，絕不估計，endpoint_class 區分 openrouter vs custom"
  - "Model 規範化：response.model 取代配置字串，陣列型設定標準化，error-path 事件帶入，unknown 作為底線，非字串值不再隱沒於洗淨器"
tags: [telemetry-data-quality, token-accounting, cost-precision, provider-parity]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.5.3

claude-mem v13.5.3 修復 session_compressed 遙測資料品質四項 bug，所有分析數字現源於真實、提供者報告的資料。Claude token 計數修正：從 assistant message 的早期流式快照（8-10 token）改為 SDK 結果消息的真實計數（實測原 8 改 45），壓縮比從荒謬 6,000–38,000 降至真實 ~10–100。成本資料真實化：Claude 從 SDK cumulative total_cost_usd，OpenRouter 從 usage.cost + cost_details.upstream_inference_cost，Gemini 誠實為空（絕不估計）。模型規範化：使用 response.model 而非配置字串，陣列型設定標準化，error-path 也帶入，未知值不再隱沒。新增 install-state snapshot：worker_started 報告觀測/會話/摘要/專案計數、DB 大小、安裝年齡、7/30 天觀測數，啟用留存世代切片。

### 重點
- Token 計數真實化：從 SDK 早期流式的 2-10 改為結果消息真實計數，壓縮比從 6,000x 荒謬值降至 10-100x 合理值，驗證 placeholder 8 vs result 45
- 成本資料精確化：Claude (SDK cumulative total_cost_usd) / OpenRouter (usage.cost + upstream_inference_cost) / Gemini (honest null) 三 provider 對齐，絕不估計，endpoint_class 區分 openrouter vs custom
- Model 規範化：response.model 取代配置字串，陣列型設定標準化，error-path 事件帶入，unknown 作為底線，非字串值不再隱沒於洗淨器

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.5.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.5.3

Telemetry: real data edition 
 Every analytics number claude-mem reports about itself is now real, provider-reported data — plus a new daily install-state snapshot so we can see the actual state of the installed base. 
 Fixed: the four session_compressed data-quality bugs 
 
 Claude token counts were placeholders. The Agent SDK attaches an early-streaming usage snapshot to assistant messages ( output_tokens of ~2–10, regardless of actual output). The session_compressed event is now fired from the SDK result message, which carries the finalized per-turn usage — verified empirically (placeholder said 8, result said 45). Compression ratios for Claude models drop from a nonsensical 6,000–38,000 to the true ~10–100 range. 
 cost_usd is now real and populated. Claude: computed from the SDK's cumulative total_cost_usd delta between consecutive turns. OpenRouter: usage.cost + cost_details.upstream_inference_cost (covers BYOK), with usage accounting requested from openrouter.ai only. Gemini reports no cost, so the field stays honestly absent — never estimated. 
 Impossible compression ratios (&lt; 1, or exactly 0.0) eliminated. Custom OpenAI-compatible gateways that report suffix-only or one-sided token usage can no longer produce half-real events: usage is now both-sides-or-nothing, ratios require input &gt; 0, and a new endpoint_class property ( openrouter | custom ) lets dashboards segment gateway-reported data. 
 model is never silently missing or wrong. The model that actually served the request ( response.model ) is stamped instead of the raw configured string, array-typed model settings are normalized, error-path events now carry the model, and unknown is the floor everywhere — non-string values previously vanished in the telemetry scrubber. 
 
 New: install-state snapshot 
 worker_started (start + daily heartbeat) now reports an aggregate snapshot of the local memory DB as person properties: observation/session/summary/project counts, DB file size, install age in days, observations in the last 7/30 days, and days since the last observation. Counts and day-deltas only — never project names, text, or any content. Makes retention, scale, and activity cohorts directly sliceable in analytics. 
 Also fixed 
 
 The ide person property on worker_started never populated — the lookup queried a legacy table and silently threw on every start since it shipped. 
 Epoch math now normalizes legacy seconds-unit rows (a few hundred per install) that would have reported install ages of ~20,000 days. 
 
 All new properties are whitelisted in the scrubber, documented at https://docs.claude-mem.ai/telemetry , and shown in the npx claude-mem telemetry consent screen. Telemetry remains anonymous and opt-out ( npx claude-mem telemetry disable ). 
 🤖 Generated with Claude Code

</details>