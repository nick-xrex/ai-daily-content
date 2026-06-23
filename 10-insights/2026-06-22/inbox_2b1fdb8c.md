---
id: inbox_2b1fdb8c
date: 2026-06-22
source_ref: "[[00-inbox/2026-06-22/2219-infoq-architecture-aws-graviton5-reaches-general-availabili-0312]]"
title: "AWS Graviton5 Reaches General Availability with 192 Cores and Formally Verified VM Isolation"
url: https://www.infoq.com/news/2026/06/aws-graviton5-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-22T10:05:00+00:00
fetched_at: 2026-06-23T00:29:47.777442+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 正式推出 Graviton5 處理器的 M9g 與 M9gd EC2 執行個體，搭載 192 個 ARM 核心與 DDR5-8800 記憶體，透過 Nitro Isolation Engine 實現形式驗證的虛擬機隔離。ClickHouse 在零程式碼改動的情況下性能提升 36%，Meta 已承諾投入數千萬核。定價較 Graviton4 高 9%，但整體價效比改善約 15%，進一步證實 ARM 架構在商業雲端運算中的可行性。"
key_points:
  - "Graviton5 硬體規格：192 ARM 核心、DDR5-8800 記憶體、Nitro Isolation Engine 提供正式驗證的 VM 隔離"
  - "性能實績：ClickHouse 實測零改動下性能提升 36%；Meta 大規模承諾數千萬核部署"
  - "成本效益：定價較上一代高 9%，但整體價效比提升 15%，降低企業大規模採購成本"
tags: [aws-graviton5, arm-servers, ec2, performance-benchmark, price-performance]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Graviton5 Reaches General Availability with 192 Cores and Formally Verified VM Isolation

AWS 正式推出 Graviton5 處理器的 M9g 與 M9gd EC2 執行個體，搭載 192 個 ARM 核心與 DDR5-8800 記憶體，透過 Nitro Isolation Engine 實現形式驗證的虛擬機隔離。ClickHouse 在零程式碼改動的情況下性能提升 36%，Meta 已承諾投入數千萬核。定價較 Graviton4 高 9%，但整體價效比改善約 15%，進一步證實 ARM 架構在商業雲端運算中的可行性。

### 重點
- Graviton5 硬體規格：192 ARM 核心、DDR5-8800 記憶體、Nitro Isolation Engine 提供正式驗證的 VM 隔離
- 性能實績：ClickHouse 實測零改動下性能提升 36%；Meta 大規模承諾數千萬核部署
- 成本效益：定價較上一代高 9%，但整體價效比提升 15%，降低企業大規模採購成本

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/aws-graviton5-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS made Graviton5-powered EC2 M9g and M9gd instances generally available with 192 ARM cores, formally verified VM isolation via the Nitro Isolation Engine, and DDR5-8800 memory. ClickHouse reported 36% better performance with zero code changes. Meta committed tens of millions of cores. On-demand pricing is 9% above Graviton4, translating to roughly 15% better price-performance. By Steef-Jan Wiggers

</details>