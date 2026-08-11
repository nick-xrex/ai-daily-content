---
id: inbox_308d84af
date: 2026-08-08
source_ref: "[[00-inbox/2026-08-08/2249-claude-mem-releases-v13-14-0-df81]]"
title: "v13.14.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.14.0
source: claude-mem-releases
published_at: 2026-08-08T02:21:38+00:00
fetched_at: 2026-08-08T23:55:54.496162+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "第三方工具 claude-mem v13.14.0 重新排序安裝程序中的記憶提供商選項，將 CMEM Pro（社群 $30/月訂閱方案）置於首選，並在每個選項旁標示成本透明：CMEM Pro $0/1k observations（訂閱制）vs OpenRouter $2.73/1k vs Gemini API $3.39/1k vs Anthropic plan $8.91/1k。實現上複用現有 OpenAI-compatible 客戶端框架，僅修改 base URL、model、API key 三項設定。成本計算公式單行可修改，支援開發環境覆蓋。```mermaid
graph LR
    A[\"Memory Provider Cost per 1k Observations\"]
    A -->|CMEM Pro| B[\"$0/1k<br/>Subscription $30/mo\"]
    A -->|OpenRouter| C[\"$2.73/1k\"]
    A -->|Gemini API| D[\"$3.39/1k\"]
    A -->|Anthropic Plan| E[\"$8.91/1k\"]
```"
key_points:
  - "CMEM Pro 成為安裝首選：$30/月訂閱，成本最低（$0/1k），包含雲端同步"
  - "成本透明化：每個提供商選項旁顯示 $/1k，讓使用者按成本（非品牌認知度）選擇"
  - "技術簡化：複用 OpenRouter provider 框架作為 OpenAI-compatible 代理，避免新增提供商程式碼，僅四行設定修改"
tags: [claude-mem, pricing, memory-provider, openrouter]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.14.0

第三方工具 claude-mem v13.14.0 重新排序安裝程序中的記憶提供商選項，將 CMEM Pro（社群 $30/月訂閱方案）置於首選，並在每個選項旁標示成本透明：CMEM Pro $0/1k observations（訂閱制）vs OpenRouter $2.73/1k vs Gemini API $3.39/1k vs Anthropic plan $8.91/1k。實現上複用現有 OpenAI-compatible 客戶端框架，僅修改 base URL、model、API key 三項設定。成本計算公式單行可修改，支援開發環境覆蓋。```mermaid
graph LR
    A["Memory Provider Cost per 1k Observations"]
    A -->|CMEM Pro| B["$0/1k<br/>Subscription $30/mo"]
    A -->|OpenRouter| C["$2.73/1k"]
    A -->|Gemini API| D["$3.39/1k"]
    A -->|Anthropic Plan| E["$8.91/1k"]
```

### 重點
- CMEM Pro 成為安裝首選：$30/月訂閱，成本最低（$0/1k），包含雲端同步
- 成本透明化：每個提供商選項旁顯示 $/1k，讓使用者按成本（非品牌認知度）選擇
- 技術簡化：複用 OpenRouter provider 框架作為 OpenAI-compatible 代理，避免新增提供商程式碼，僅四行設定修改

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.14.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

CMEM Pro is now the first option in the installer 
 npx claude-mem now leads its provider prompt with CMEM Pro , and every option shows what it actually costs per 1,000 observations — so the choice is made on price rather than brand recognition. 
 ◆ Which memory provider do you want to use?
│ ● CMEM Pro — observer model, off your plan ($0/1k observations · $30/mo, cloud sync included) Recommended
│ ○ OpenRouter / any OpenAI-compatible key (~$2.73/1k observations, billed to you)
│ ○ Gemini API key (~$3.39/1k observations, billed to you)
│ ○ Use your Anthropic plan (~$8.91/1k observations, billed to your Claude plan)
 
 Anthropic moves last: it is the most expensive per observation and it bills your own Claude plan. 
 Picking CMEM Pro 
 Opens cmem.ai/pro?from=installer , waits for the cm_pro_... key the signup flow hands back, writes it to settings, and points you at the browser to finish cloud sync. The key is pasted by hand — no polling, no device-code handshake. 
 No new provider code 
 OpenRouterProvider is already a generic OpenAI-compatible client whose base URL and model both come from settings, so CMEM Pro is four settings writes: 
 {
 "CLAUDE_MEM_PROVIDER" : " openrouter " ,
 "CLAUDE_MEM_OPENROUTER_BASE_URL" : " https://cmem.ai/api/inference/v1 " ,
 "CLAUDE_MEM_OPENROUTER_MODEL" : " cmem-observer " ,
 "CLAUDE_MEM_OPENROUTER_API_KEY" : " cm_pro_&lt;hex&gt; " 
} 
 'cmem' is a prompt-only sentinel and never reaches settings.json — the worker still only understands claude | gemini | openrouter . 
 Cost figures 
 New src/npx-cli/cmem-pro-costs.ts derives every label from one constant ( ratePerM × TOKENS_PER_OBSERVATION / 1000 ), so re-pricing is a one-line edit. CMEM Pro deliberately carries no computed $/1k — it is a flat subscription that does not bill your tokens. 
 CMEM_PRO_ORIGIN overrides the origin so the whole funnel can be walked against a dev server. 
 Notes 
 
 openBrowser() is best-effort; the URL is printed first, so headless boxes just get a copy-pasteable link. 
 Existing installs are unaffected — this changes the prompt, not any persisted provider. 
 
 Full Changelog : v13.13.1...v13.14.0

</details>