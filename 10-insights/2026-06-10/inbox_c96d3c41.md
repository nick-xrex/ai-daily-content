---
id: inbox_c96d3c41
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_c96d3c41]]"
title: "v13.5.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.5.1
source: claude-mem-releases
published_at: 2026-06-10T04:43:24+00:00
fetched_at: 2026-06-11T00:23:32.322587+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.5.1 新增深度遙測檢測以測量 context-injected 的真實 token 經濟效益及觀測類型細分。context_injected 現透過 generateContextWithStats() 報告 token 經濟與觀測類型細分。session_compressed 豐富化含 provider、model、真實 per-call token 計數（Claude/Gemini/OpenRouter 對齐）、延遲、觀測類型細分。生命週期事件建立 person profile 含 IDE、provider、mode 屬性，解鎖 DAU/WAU 與世代分析。worker_started 捕捉移至 DB 初始化後以反映真正 live worker。遙測洗淨白名單擴充並測試，同意畫面與文件列舉所有收集屬性。"
key_points:
  - "Context 節省測量：generateContextWithStats() 新增 token 經濟與觀測類型細分報告，可量化 context-injected 的真實節省效益"
  - "會話壓縮豐富化：session_compressed 新增 provider / model / real per-call token (Claude/Gemini/OpenRouter 對齐) / latency / observation-type 細分，完整會話成本可視化"
  - "生命週期人格化：worker_started 捕捉移至 DB init 後，建立含 IDE / provider / mode 的 person profile，啟用 DAU/WAU 與留存世代分析，daily heartbeat 支援"
tags: [telemetry-instrumentation, context-economics, session-analytics, retention-cohorts]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.5.1

claude-mem v13.5.1 新增深度遙測檢測以測量 context-injected 的真實 token 經濟效益及觀測類型細分。context_injected 現透過 generateContextWithStats() 報告 token 經濟與觀測類型細分。session_compressed 豐富化含 provider、model、真實 per-call token 計數（Claude/Gemini/OpenRouter 對齐）、延遲、觀測類型細分。生命週期事件建立 person profile 含 IDE、provider、mode 屬性，解鎖 DAU/WAU 與世代分析。worker_started 捕捉移至 DB 初始化後以反映真正 live worker。遙測洗淨白名單擴充並測試，同意畫面與文件列舉所有收集屬性。

### 重點
- Context 節省測量：generateContextWithStats() 新增 token 經濟與觀測類型細分報告，可量化 context-injected 的真實節省效益
- 會話壓縮豐富化：session_compressed 新增 provider / model / real per-call token (Claude/Gemini/OpenRouter 對齐) / latency / observation-type 細分，完整會話成本可視化
- 生命週期人格化：worker_started 捕捉移至 DB init 後，建立含 IDE / provider / mode 的 person profile，啟用 DAU/WAU 與留存世代分析，daily heartbeat 支援

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.5.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.5.1

What's New in 13.5.1 
 Deep telemetry instrumentation (anonymous, opt-out — see npx claude-mem telemetry ): 
 
 context_injected now reports token economics and observation-type breakdowns via the new generateContextWithStats() context builder, so we can measure real context savings. 
 session_compressed enriched with provider, model, real per-call token counts (Claude, Gemini, and OpenRouter at parity), latency, and observation-type breakdown. 
 Lifecycle events now create person profiles with IDE, provider, and mode properties, unlocking retention/cohort analytics (DAU/WAU via daily worker heartbeat). 
 worker_started capture moved after DB init so it reflects a genuinely live worker. 
 Telemetry scrub whitelist expanded and tested for all new properties; consent screen and docs list every property collected. 
 
 🤖 Generated with Claude Code

</details>