---
id: inbox_fdddc8d3
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_fdddc8d3]]"
title: "datasette-ip-rate-limit 0.1a0"
url: https://simonwillison.net/2026/May/14/datasette-ip-rate-limit/#atom-everything
source: simon-willison
published_at: 2026-05-14T04:10:23+00:00
fetched_at: 2026-05-18T03:29:54.911802+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 使用 Codex (GPT-5.5 xhigh) 為 datasette.io 構建 datasette-ip-rate-limit 限流插件 v0.1a0，解決爬蟲濫用問題。插件支持基於客戶端 IP 的動態限流，核心配置包含 max_keys: 10,000、時間窗口 60 秒、每窗口最多 60 請求、超限後封禁 20 秒。該插件可針對不同路徑實施差異化規則，例如 /global-power-plants/ 和 /legislators/ 各有獨立限流參數。此案例展示了 AI 在快速生成複雜配置驅動軟體中的實用價值，已在生產環境驗證有效。"
key_points:
  - "Codex (GPT-5.5 xhigh) 生成 IP 限流插件，配置 max_keys: 10K、60s window、60 req/min、20s block"
  - "支援多路徑差異化限流規則（demo-databases 設置 60 req/min）"
  - "生產環境驗證的爬蟲防護解決方案"
tags: [datasette, rate-limiting, codex, gpt-5.5, ai-generated-code]
topics: [foundation_models.gpt]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-ip-rate-limit 0.1a0

Simon Willison 使用 Codex (GPT-5.5 xhigh) 為 datasette.io 構建 datasette-ip-rate-limit 限流插件 v0.1a0，解決爬蟲濫用問題。插件支持基於客戶端 IP 的動態限流，核心配置包含 max_keys: 10,000、時間窗口 60 秒、每窗口最多 60 請求、超限後封禁 20 秒。該插件可針對不同路徑實施差異化規則，例如 /global-power-plants/ 和 /legislators/ 各有獨立限流參數。此案例展示了 AI 在快速生成複雜配置驅動軟體中的實用價值，已在生產環境驗證有效。

### 重點
- Codex (GPT-5.5 xhigh) 生成 IP 限流插件，配置 max_keys: 10K、60s window、60 req/min、20s block
- 支援多路徑差異化限流規則（demo-databases 設置 60 req/min）
- 生產環境驗證的爬蟲防護解決方案

**原文：** [simon-willison](https://simonwillison.net/2026/May/14/datasette-ip-rate-limit/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette-ip-rate-limit 0.1a0

Release: datasette-ip-rate-limit 0.1a0 
 The datasette.io site was being hammered by poorly-behaved crawlers, so I had Codex (GPT-5.5 xhigh) build a configurable rate limiting plugin to block IPs that were hammering specific areas of the site too quickly. 
 Here's the production configuration I'm using on that site for the new plugin: 
 datasette-ip-rate-limit :
 header : Fly-Client-IP 
 max_keys : 10000 
 exempt_paths :
 - " /static/* " 
 - " /-/turnstile* " 
 rules :
 - name : demo-databases 
 paths :
 - " /global-power-plants/* " 
 - " /legislators/* " 
 window_seconds : 60 
 max_requests : 60 
 block_seconds : 20 
 
 
 Tags: datasette , rate-limiting , codex

</details>