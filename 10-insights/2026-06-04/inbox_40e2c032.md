---
id: inbox_40e2c032
date: 2026-06-04
source_ref: "[[00-inbox/.../inbox_40e2c032]]"
title: "AWS Replaces Fat-Tree Data Center Networks with Random Graph Theory, Cutting Routers by 69%"
url: https://www.infoq.com/news/2026/06/aws-random-graph-data-center/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-04T08:25:00+00:00
fetched_at: 2026-06-05T01:16:26.823994+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 公開 Resilient Network Graphs（RNG），一種基於準隨機圖論的平坦網路架構，已成為新資料中心的預設標準。RNG 以被動光學 ShuffleBox 實現 ToR-to-ToR（機架頂部到機架頂部）直連網格，取代傳統 fat-tree 階層結構，實現路由器數量減少 69%、輸送量提升 33%、網路功耗降低 40% 的成果。

```mermaid
graph TD
    A[\"傳統 Fat-Tree<br/>階層式路由\"] -->|69% 更多<br/>路由器| B[\"成本高\"]
    C[\"AWS RNG<br/>隨機圖+ShuffleBox\"] -->|33% 更高<br/>輸送量| D[\"性能優\"]
    C -->|40% 更低<br/>功耗| E[\"節能優\"]
    C -->|69% 更少<br/>路由器| F[\"成本低\"]
```"
key_points:
  - "網路架構創新：從 fat-tree 階層轉向基於準隨機圖論的平坦網格，使用被動光學 ShuffleBox"
  - "成本效益：路由器數量減少 69%，顯著降低基礎設施投資"
  - "性能倍增：輸送量提升 33%，網路功耗降低 40%"
tags: [aws, network-architecture, data-center, infrastructure, graph-theory]
topics: []
importance: 5
novelty: 5
insight_quality: 4
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## AWS Replaces Fat-Tree Data Center Networks with Random Graph Theory, Cutting Routers by 69%

AWS 公開 Resilient Network Graphs（RNG），一種基於準隨機圖論的平坦網路架構，已成為新資料中心的預設標準。RNG 以被動光學 ShuffleBox 實現 ToR-to-ToR（機架頂部到機架頂部）直連網格，取代傳統 fat-tree 階層結構，實現路由器數量減少 69%、輸送量提升 33%、網路功耗降低 40% 的成果。

```mermaid
graph TD
    A["傳統 Fat-Tree<br/>階層式路由"] -->|69% 更多<br/>路由器| B["成本高"]
    C["AWS RNG<br/>隨機圖+ShuffleBox"] -->|33% 更高<br/>輸送量| D["性能優"]
    C -->|40% 更低<br/>功耗| E["節能優"]
    C -->|69% 更少<br/>路由器| F["成本低"]
```

### 重點
- 網路架構創新：從 fat-tree 階層轉向基於準隨機圖論的平坦網格，使用被動光學 ShuffleBox
- 成本效益：路由器數量減少 69%，顯著降低基礎設施投資
- 性能倍增：輸送量提升 33%，網路功耗降低 40%

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/aws-random-graph-data-center/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# AWS Replaces Fat-Tree Data Center Networks with Random Graph Theory, Cutting Routers by 69%

AWS disclosed that Resilient Network Graphs, a flat network architecture based on quasi-random graph theory, is now the default for most new data center builds. The design replaces fat-tree hierarchies with direct ToR-to-ToR mesh connections using passive optical ShuffleBoxes, cutting routers by 69%, boosting throughput by 33%, and reducing network power consumption by 40%. By Steef-Jan Wiggers

</details>