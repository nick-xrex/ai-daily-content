---
id: inbox_93e997df
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-claudeai-loading-every-mcp-server-on-every-prompt-49d7]]"
title: "loading every MCP server on every prompt was quietly destroying my token budget"
url: https://www.reddit.com/r/ClaudeAI/comments/1t1e5u0/loading_every_mcp_server_on_every_prompt_was/
source: reddit-claudeai
published_at: 2026-05-02T03:07:17+00:00
fetched_at: 2026-05-03T02:06:18.775740+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者發現原有 5~6 個 MCP 伺服器在每次 prompt 都被載入，即使是最簡單的問題。導入選擇性載入路由層後，token 用量大幅下降，prompt 回應速度顯著提升。突出 MCP 伺服器配置的 lazy-loading 重要性，以及預設「全量載入」的隱藏成本。"
key_points:
  - "MCP 伺服器預設在每次 prompt 都被完整載入，造成不必要的 token 消耗與延遲，即使該伺服器不被使用"
  - "實作選擇性載入路由層（根據 prompt 內容決定哪些伺服器啟用），token 成本與速度都有顯著改善"
  - "診斷建議：檢視自己的 MCP 配置，確認是否啟用了 lazy-loading 或路由機制，避免盲目過度配置"
tags: [mcp, token-optimization, prompt-efficiency, routing]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## loading every MCP server on every prompt was quietly destroying my token budget

使用者發現原有 5~6 個 MCP 伺服器在每次 prompt 都被載入，即使是最簡單的問題。導入選擇性載入路由層後，token 用量大幅下降，prompt 回應速度顯著提升。突出 MCP 伺服器配置的 lazy-loading 重要性，以及預設「全量載入」的隱藏成本。

### 重點
- MCP 伺服器預設在每次 prompt 都被完整載入，造成不必要的 token 消耗與延遲，即使該伺服器不被使用
- 實作選擇性載入路由層（根據 prompt 內容決定哪些伺服器啟用），token 成本與速度都有顯著改善
- 診斷建議：檢視自己的 MCP 配置，確認是否啟用了 lazy-loading 或路由機制，避免盲目過度配置

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t1e5u0/loading_every_mcp_server_on_every_prompt_was/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>had like 5 or 6 MCP servers configured and did not realize all of them were loading every single time i sent a prompt. even for the dumbest simplest questions.</p> <p>found a routing layer that only loads the relevant ones per prompt and token usage dropped a lot. prompts feel faster too.</p> <p>honestly cannot believe i let it go on that long without checking</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/CodinDev"> /u/CodinDev </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1e5u0/loading_every_mcp_server_on_every_prompt_was/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1e5u0/loading_every_mcp_server_on_every_prompt_was/">[comments]</a></span>

</details>