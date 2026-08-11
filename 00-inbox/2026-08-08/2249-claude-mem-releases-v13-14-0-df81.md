---
id: inbox_308d84af
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.14.0"
author: "thedotmack"
published_at: 2026-08-08T02:21:38+00:00
fetched_at: 2026-08-08T22:49:18.924867+00:00
content_hash: "df81bd5bf9245f46de54db73ca389e24a6385043f9e3eeab798e26bd64117f1c"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.14.0

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