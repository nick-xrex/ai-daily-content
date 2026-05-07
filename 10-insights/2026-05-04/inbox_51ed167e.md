---
id: inbox_51ed167e
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_51ed167e]]"
title: "How Monero’s proof of work works"
url: https://blog.alcazarsec.com/tech/posts/how-moneros-proof-of-work-works
source: hackernews
published_at: 2026-05-04T14:10:50+00:00
fetched_at: 2026-05-07T01:51:06.010052+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Monero 採用 RandomX 共識算法而非傳統固定雜湊函數。RandomX 的核心設計包括：(1) 執行隨機代碼而非固定流程，利用現代 CPU 的多元硬體特性（快取、浮點運算、分支處理、推測執行）；(2) 構建約 2GB 資料集 + 256MB 快取以強化記憶體使用；(3) 執行 8 個鏈式程序，每個包含整數運算、浮點運算和大量記憶體訪問。這項設計刻意抵抗 ASIC 礦機優化（Bitcoin SHA-256 的反面），使普通 CPU 競爭力更強，達到分散式挖礦目標。2019 年推出後，現仍是 Monero 的標準。"
key_points:
  - "隨機代碼執行（vs. Bitcoin 固定 SHA-256）：資料集大小 2,147,483,648 + 33,554,368 bytes，刻意設為非 2 的冪次方以增加硬體設計難度"
  - "金鑰更新週期 2048 區塊（~2.8 天），允許礦工重用 256MB 快取建立的 2GB 資料集；候選區塊雜湊（H）則持續變動"
  - "設計哲學：普通 CPU 內含的多層快取、浮點單元、亂序執行等特性成為優勢，ASIC 難以特化"
tags: [monero, randomx, proof-of-work, asic-resistance, cryptocurrency]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## How Monero’s proof of work works

Monero 採用 RandomX 共識算法而非傳統固定雜湊函數。RandomX 的核心設計包括：(1) 執行隨機代碼而非固定流程，利用現代 CPU 的多元硬體特性（快取、浮點運算、分支處理、推測執行）；(2) 構建約 2GB 資料集 + 256MB 快取以強化記憶體使用；(3) 執行 8 個鏈式程序，每個包含整數運算、浮點運算和大量記憶體訪問。這項設計刻意抵抗 ASIC 礦機優化（Bitcoin SHA-256 的反面），使普通 CPU 競爭力更強，達到分散式挖礦目標。2019 年推出後，現仍是 Monero 的標準。

### 重點
- 隨機代碼執行（vs. Bitcoin 固定 SHA-256）：資料集大小 2,147,483,648 + 33,554,368 bytes，刻意設為非 2 的冪次方以增加硬體設計難度
- 金鑰更新週期 2048 區塊（~2.8 天），允許礦工重用 256MB 快取建立的 2GB 資料集；候選區塊雜湊（H）則持續變動
- 設計哲學：普通 CPU 內含的多層快取、浮點單元、亂序執行等特性成為優勢，ASIC 難以特化

**原文：** [hackernews](https://blog.alcazarsec.com/tech/posts/how-moneros-proof-of-work-works)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# How Monero’s proof of work works

</details>