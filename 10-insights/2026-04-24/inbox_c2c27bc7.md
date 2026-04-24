---
id: inbox_c2c27bc7
date: 2026-04-24
source_ref: "[[00-inbox/2026-04-24/0246-simon-willison-serving-the-for-you-feed-b1fd]]"
title: "Serving the For You feed"
url: https://simonwillison.net/2026/Apr/24/serving-the-for-you-feed/#atom-everything
source: simon-willison
published_at: 2026-04-24T01:08:17+00:00
fetched_at: 2026-04-24T02:56:27.829751+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Bluesky 的 For You Feed（服務 7.2 萬使用者）由單一 Go 進程 + SQLite 驅動，運行在使用者的客廳遊戲 PC 上（16 核、96GB 記憶體、4TB NVMe）。系統持續消費 Bluesky firehose，保留 90 天資料（約 419GB SQLite 儲存空間），推薦演算法基於使用者 likes 的協同過濾。基礎設施成本極低：月成本 $30（$20 電力 + $7 OVH VPS + $3 域名），VPS 透過 Tailscale 與居家伺服器通訊。開發者預估此架構可擴展至 Bluesky 全部約 100 萬日活使用者。展現精益分散式架構與 SQLite、Tailscale 組合的強大可擴展性。"
key_points:
  - "單機 SQLite 419GB 規模推薦系統月成本僅 $30，涵蓋電力、VPS、域名"
  - "Tailscale 安全跨域連接私人伺服器至公網 VPS，無需直接暴露主機"
  - "協同過濾（基於 likes）在 90 天時間窗口內足以支撐 72k 使用者"
tags: [bluesky, sqlite, distributed-systems, tailscale, cost-efficiency]
topics: []
importance: 3
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Serving the For You feed

Bluesky 的 For You Feed（服務 7.2 萬使用者）由單一 Go 進程 + SQLite 驅動，運行在使用者的客廳遊戲 PC 上（16 核、96GB 記憶體、4TB NVMe）。系統持續消費 Bluesky firehose，保留 90 天資料（約 419GB SQLite 儲存空間），推薦演算法基於使用者 likes 的協同過濾。基礎設施成本極低：月成本 $30（$20 電力 + $7 OVH VPS + $3 域名），VPS 透過 Tailscale 與居家伺服器通訊。開發者預估此架構可擴展至 Bluesky 全部約 100 萬日活使用者。展現精益分散式架構與 SQLite、Tailscale 組合的強大可擴展性。

### 重點
- 單機 SQLite 419GB 規模推薦系統月成本僅 $30，涵蓋電力、VPS、域名
- Tailscale 安全跨域連接私人伺服器至公網 VPS，無需直接暴露主機
- 協同過濾（基於 likes）在 90 天時間窗口內足以支撐 72k 使用者

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/24/serving-the-for-you-feed/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://atproto.com/blog/serving-the-for-you-feed">Serving the For You feed</a></strong></p>
One of Bluesky's most interesting features is that anyone can run their own <a href="https://simonwillison.net/atom/everything/bluesky custom feed">custom "feed" implementation</a> and make it available to other users - effectively enabling custom algorithms that can use any mechanism they like to recommend posts.</p>
<p>spacecowboy runs the <a href="https://bsky.app/profile/did:plc:3guzzweuqraryl3rdkimjamk/feed/for-you">For You Feed</a>, used by around 72,000 people. This guest post on the AT Protocol blog explains how it works.</p>
<p>The architecture is <em>fascinating</em>. The feed is served by a single Go process using SQLite on a "gaming" PC in spacecowboy's living room - 16 cores, 96GB of RAM and 4TB of attached NVMe storage.</p>
<p>Recommendations are based on likes: what else are the people who like the same things as you liking on the platform?</p>
<p>That Go server consumes the Bluesky firehose and stores the relevant details in SQLite, keeping the last 90 days of relevant data, which currently uses around 419GB of SQLite storage.</p>
<p>Public internet traffic is handled by a $7/month VPS on OVH, which talks to the living room server via Tailscale.</p>
<p>Total cost is now $30/month: $20 in electricity, $7 in VPS and $3 for the two domain names. spacecowboy estimates that the existing system could handle all ~1 million daily active Bluesky users if they were to switch to the cheapest algorithm they have found to work.


    <p>Tags: <a href="https://simonwillison.net/tags/go">go</a>, <a href="https://simonwillison.net/tags/scaling">scaling</a>, <a href="https://simonwillison.net/tags/sqlite">sqlite</a>, <a href="https://simonwillison.net/tags/software-architecture">software-architecture</a>, <a href="https://simonwillison.net/tags/tailscale">tailscale</a>, <a href="https://simonwillison.net/tags/bluesky">bluesky</a></p>

</details>