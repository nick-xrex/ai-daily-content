---
id: inbox_493efffa
date: 2026-05-27
source_ref: "[[00-inbox/2026-05-27/2345-infoq-main-how-linkedin-identified-a-kernel-lock-co-8e37]]"
title: "How LinkedIn Identified a Kernel Lock Contention Issue Causing Recurring System Freezes"
url: https://www.infoq.com/news/2026/05/linkedin-kernel-lock-freeze/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-27T18:00:00+00:00
fetched_at: 2026-05-27T23:53:01.575146+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LinkedIn 工程師使用 eBPF off-CPU profiling 診斷用戶信息流資料庫的間歇性宕機問題。問題表現為短暫反覆停機但無日誌痕跡，根本原因是 kernel lock contention。此案例展示了用現代 observability 工具診斷底層系統問題的方法，對大規模基礎設施診斷具有參考價值。"
key_points:
  - "eBPF off-CPU profiling 診斷難追蹤的系統凍結：比傳統 on-CPU profiling 捕捉 lock contention 更有效"
  - "Kernel lock contention 導致週期性 database 宕機但無明顯日誌，突出觀測盲點"
  - "可複製的診斷方法：用 eBPF 追蹤系統層面的性能問題，適用於類似間歇性故障"
tags: [ebpf, kernel-profiling, observability, lock-contention]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## How LinkedIn Identified a Kernel Lock Contention Issue Causing Recurring System Freezes

LinkedIn 工程師使用 eBPF off-CPU profiling 診斷用戶信息流資料庫的間歇性宕機問題。問題表現為短暫反覆停機但無日誌痕跡，根本原因是 kernel lock contention。此案例展示了用現代 observability 工具診斷底層系統問題的方法，對大規模基礎設施診斷具有參考價值。

### 重點
- eBPF off-CPU profiling 診斷難追蹤的系統凍結：比傳統 on-CPU profiling 捕捉 lock contention 更有效
- Kernel lock contention 導致週期性 database 宕機但無明顯日誌，突出觀測盲點
- 可複製的診斷方法：用 eBPF 追蹤系統層面的性能問題，適用於類似間歇性故障

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/linkedin-kernel-lock-freeze/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

When LinkedIn engineers encountered short-lived, recurring outages where the database powering their user feed became unavailable and then recover without leaving helpful traces, they had to devise a novel approach to uncover the root cause using off-CPU profiling with eBPF. By Sergio De Simone

</details>