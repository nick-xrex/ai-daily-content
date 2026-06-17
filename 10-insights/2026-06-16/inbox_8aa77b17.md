---
id: inbox_8aa77b17
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-simon-willison-cloudflare-captcha-on-at-least-one-amper-f06a]]"
title: "Cloudflare CAPTCHA on at least one ampersand"
url: https://simonwillison.net/2026/Jun/16/captcha-on-at-least-one-ampersand/#atom-everything
source: simon-willison
published_at: 2026-06-16T00:21:36+00:00
fetched_at: 2026-06-16T22:08:51.877048+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 分享了使用 Cloudflare WAF（Web Application Firewall）規則防止爬蟲過度爬取自己網站的技巧。透過規則 `(http.request.uri.path wildcard r\"/search/*\" and http.request.uri.query contains \"&\")` 可只在搜尋 URL 包含至少一個 ampersand 時觸發 CAPTCHA，避免簡單單參數查詢被誤觸。他同時嘗試了 Cloudflare MCP 與 Claude Code 的整合，最終改用 Cloudflare API 進行配置。"
key_points:
  - "WAF 規則：search/* 路徑 AND query 含 ampersand 時才觸發 CAPTCHA，區分複雜搜尋"
  - "Cloudflare MCP with Claude Code 可快速原型化 WAF 規則修改"
  - "Cloudflare MCP 無法直接編輯規則，需要改用 Cloudflare API 操作"
tags: [cloudflare, waf, claude-code, mcp]
topics: [agents.mcp]
importance: 2
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare CAPTCHA on at least one ampersand

Simon Willison 分享了使用 Cloudflare WAF（Web Application Firewall）規則防止爬蟲過度爬取自己網站的技巧。透過規則 `(http.request.uri.path wildcard r"/search/*" and http.request.uri.query contains "&")` 可只在搜尋 URL 包含至少一個 ampersand 時觸發 CAPTCHA，避免簡單單參數查詢被誤觸。他同時嘗試了 Cloudflare MCP 與 Claude Code 的整合，最終改用 Cloudflare API 進行配置。

### 重點
- WAF 規則：search/* 路徑 AND query 含 ampersand 時才觸發 CAPTCHA，區分複雜搜尋
- Cloudflare MCP with Claude Code 可快速原型化 WAF 規則修改
- Cloudflare MCP 無法直接編輯規則，需要改用 Cloudflare API 操作

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/16/captcha-on-at-least-one-ampersand/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

TIL: Cloudflare CAPTCHA on at least one ampersand 
 I'm using Cloudflare's CAPTCHA (they call it a "Web Application Firewall &gt; Custom rules &gt; Managed Challenge" these days) to prevent crawlers from aggresively spidering my faceted search engine on this site, but I got fed up of even simple ?q=term searches triggering the challenge. 
 After some mucking around with Claude Code it turns out you can register the following rule instead, so the CAPTCHA only kicks in for search URLs containing at least one ampersand: 
 (http.request.uri.path wildcard r"/search/*" and http.request.uri.query contains "&amp;") 
 And now /search/?q=lemur works without triggering a CAPTCHA! 
 Also included: notes on trying out the Cloudflare MCP with Claude Code , though it turned out not to be able to edit the rules in question so I had Claude Code switch to the Cloudflare API instead. 
 
 
 Tags: captchas , cloudflare , model-context-protocol , claude-code

</details>