---
id: inbox_f45f98a5
date: 2026-07-23
source_ref: "[[00-inbox/2026-07-23/0149-infoq-main-ink-switch-introduces-bijou64-canonical-49ca]]"
title: "Ink &amp; Switch Introduces Bijou64: Canonical Variable-Length Integer Encoding for Safe Parsing"
url: https://www.infoq.com/news/2026/07/bijou64-canonical-varint/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-23T09:43:00+00:00
fetched_at: 2026-07-24T02:06:36.362365+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ink & Switch 發佈了 Bijou64，一種新型變長整數編碼方案。該方案的核心特性是每個數值都有唯一的位元組表示，從根本上消除了所謂 canonicality bug class。這類漏洞曾影響 PKCS#1、JWT 庫和比特幣等關鍵系統。相比 LEB128 編碼，Bijou64 的解碼速度快 2 至 10 倍，性能優勢顯著。此發布已催生了 Elixir、Go、Perl 和 Java 等多種語言的社群移植版本。技術社群對此引發了關於 SIMD 性能和邊界檢查的深度討論。"
key_points:
  - "Bijou64 確保每個整數只有唯一編碼，徹底消除 canonicality 攻擊向量（影響 PKCS#1、JWT、Bitcoin）"
  - "解碼速度較 LEB128 快 2-10 倍，性能全面領先"
  - "已有多語言社群實現（Elixir、Go、Perl、Java），顯示實用價值和採用潛力"
tags: [encoding, security, cryptography, bijou64]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Ink & Switch Introduces Bijou64: Canonical Variable-Length Integer Encoding for Safe Parsing

Ink & Switch 發佈了 Bijou64，一種新型變長整數編碼方案。該方案的核心特性是每個數值都有唯一的位元組表示，從根本上消除了所謂 canonicality bug class。這類漏洞曾影響 PKCS#1、JWT 庫和比特幣等關鍵系統。相比 LEB128 編碼，Bijou64 的解碼速度快 2 至 10 倍，性能優勢顯著。此發布已催生了 Elixir、Go、Perl 和 Java 等多種語言的社群移植版本。技術社群對此引發了關於 SIMD 性能和邊界檢查的深度討論。

### 重點
- Bijou64 確保每個整數只有唯一編碼，徹底消除 canonicality 攻擊向量（影響 PKCS#1、JWT、Bitcoin）
- 解碼速度較 LEB128 快 2-10 倍，性能全面領先
- 已有多語言社群實現（Elixir、Go、Perl、Java），顯示實用價值和採用潛力

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/bijou64-canonical-varint/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ink & Switch published bijou64, a variable-length integer encoding where every number has exactly one byte representation, closing the canonicality bug class behind attacks on PKCS#1, JWT libraries, and Bitcoin. The design also decodes two to ten times faster than LEB128. Community ports to Elixir, Go, Perl, and Java followed, while HN commenters debated SIMD performance and residual range checks. By Steef-Jan Wiggers

</details>