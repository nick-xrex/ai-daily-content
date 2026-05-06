---
id: inbox_71e30ba2
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/1002-simon-willison-datasette-referrer-policy-0-1-d256]]"
title: "datasette-referrer-policy 0.1"
url: https://simonwillison.net/2026/May/5/datasette-referrer-policy/#atom-everything
source: simon-willison
published_at: 2026-05-05T23:44:27+00:00
fetched_at: 2026-05-06T10:07:20.827674+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 全球發電廠演示的 OpenStreetMap 地圖因兩個 bugs 無法正常顯示。首先，datasette-turnstile CAPTCHA 誤攔截地圖插件的 .json fetch 請求，導致地圖無法加載；其次，OpenStreetMap 會拒絕帶有 Referrer-Policy: no-referrer HTTP 標頭的 tile 請求。新發布的 datasette-referrer-policy 0.1 插件提供靈活的 HTTP 標頭管理功能，允許應用設定不同的 referrer policy 值而不改變 Datasette 的預設安全設置。作者使用 Codex + GPT-5.5 協助插件開發。"
key_points:
  - "CAPTCHA 誤攔截地圖 JSON 請求、OpenStreetMap 要求 Referrer-Policy 非 no-referrer"
  - "datasette-referrer-policy 0.1 提供應用級標頭管理，無需改變框架預設"
  - "用 Codex + GPT-5.5 AI 輔助快速開發針對性插件"
tags: [datasette, http-headers, openstreetmap, referrer-policy, plugin]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-referrer-policy 0.1

Datasette 全球發電廠演示的 OpenStreetMap 地圖因兩個 bugs 無法正常顯示。首先，datasette-turnstile CAPTCHA 誤攔截地圖插件的 .json fetch 請求，導致地圖無法加載；其次，OpenStreetMap 會拒絕帶有 Referrer-Policy: no-referrer HTTP 標頭的 tile 請求。新發布的 datasette-referrer-policy 0.1 插件提供靈活的 HTTP 標頭管理功能，允許應用設定不同的 referrer policy 值而不改變 Datasette 的預設安全設置。作者使用 Codex + GPT-5.5 協助插件開發。

### 重點
- CAPTCHA 誤攔截地圖 JSON 請求、OpenStreetMap 要求 Referrer-Policy 非 no-referrer
- datasette-referrer-policy 0.1 提供應用級標頭管理，無需改變框架預設
- 用 Codex + GPT-5.5 AI 輔助快速開發針對性插件

**原文：** [simon-willison](https://simonwillison.net/2026/May/5/datasette-referrer-policy/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong>Release:</strong> <a href="https://github.com/datasette/datasette-referrer-policy/releases/tag/0.1">datasette-referrer-policy 0.1</a></p>
        <p>The OpenStreetMap tiles on the Datasette <a href="https://datasette.io/global-power-plants/global-power-plants">global-power-plants demo</a> weren't displaying correctly. This turned out to be caused by two bugs.</p>
<p>The first is that the CAPTCHA <a href="https://github.com/simonw/datasette-turnstile">I added</a> to that site a few weeks ago was triggering for the <code>.json</code> fetch requests used by the map plugin, and since those weren't HTML the user was not being asked to solve them. Here's <a href="https://github.com/simonw/datasette.io/commit/23a1c8596b75b2094db46035a3b4280109fb3df3">the fix</a>.</p>
<p>The second was that OpenStreetMap quite reasonably <a href="https://wiki.openstreetmap.org/wiki/Referer">block tile requests</a> from sites that use a <code>Referrer-Policy: no-referrer</code> header.</p>
<p>Datasette does this by default, and I didn't want to change that default on people without warning - so I had Codex + GPT-5.5 <a href="https://gisthost.github.io/?402f2f23ee3dbfa251bf0d216e0224f7">build me</a> a new plugin to help set that header to another value.</p>
    
    
        <p>Tags: <a href="https://simonwillison.net/tags/openstreetmap">openstreetmap</a>, <a href="https://simonwillison.net/tags/http">http</a>, <a href="https://simonwillison.net/tags/datasette">datasette</a></p>

</details>