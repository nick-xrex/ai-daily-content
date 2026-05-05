---
id: inbox_8f1b8e5f
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/0819-infoq-main-figma-builds-in-house-redis-proxy-to-hit-0898]]"
title: "Figma Builds In-House Redis Proxy to Hit Six Nines Uptime"
url: https://www.infoq.com/news/2026/05/figma-redis-figcache/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-05T07:00:00+00:00
fetched_at: 2026-05-05T08:25:42.777103+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Figma 開發了內部緩存代理服務 FigCache，2025 年下半年投入生產，取代了之前破碎的多層緩存堆棧架構。該系統在生產環境中實現了六個九（99.9999%）的可用性，成為 Figma 基礎設施的關鍵支撐。透過統一的代理層，FigCache 簡化了複雜的緩存管理，提高了整體系統穩定性和易維護性。此案例展示了大型科技公司如何通過構建定製化的內部工具來解決特定的可靠性挑戰。"
key_points:
  - "FigCache：統一的 Redis 代理服務，取代破碎的多層緩存堆棧架構"
  - "六個九可用性（99.9999%）：在生產環境中實現超高可靠性"
  - "生產化驗證：自 2025 年下半年投入生產，經充分測試"
tags: [caching, redis, infrastructure, site-reliability, figma]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Figma Builds In-House Redis Proxy to Hit Six Nines Uptime

Figma 開發了內部緩存代理服務 FigCache，2025 年下半年投入生產，取代了之前破碎的多層緩存堆棧架構。該系統在生產環境中實現了六個九（99.9999%）的可用性，成為 Figma 基礎設施的關鍵支撐。透過統一的代理層，FigCache 簡化了複雜的緩存管理，提高了整體系統穩定性和易維護性。此案例展示了大型科技公司如何通過構建定製化的內部工具來解決特定的可靠性挑戰。

### 重點
- FigCache：統一的 Redis 代理服務，取代破碎的多層緩存堆棧架構
- 六個九可用性（99.9999%）：在生產環境中實現超高可靠性
- 生產化驗證：自 2025 年下半年投入生產，經充分測試

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/figma-redis-figcache/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/05/figma-redis-figcache/en/headerimage/generatedHeaderImage-1777405837575.jpg" /><p>Figma has published a detailed account of how it built an in-house Redis proxy service called FigCache, replacing a fragmented caching stack that had become a liability for site availability. The system, described in a post by Kevin Lin, has been in production since the second half of 2025 and has delivered what the company describes as six nines of uptime across its caching layer.</p> <i>By Matt Saunders</i>

</details>