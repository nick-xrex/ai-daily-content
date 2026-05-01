---
id: inbox_bf7a4f45
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-infoq-architecture-article-the-dpop-storage-paradox-why-bro-7041]]"
title: "Article: The DPoP Storage Paradox: Why Browser-Based Proof-of-Possession Remains an Unsolved Problem"
url: https://www.infoq.com/articles/dpop-key-storage-unsolved-problem/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-04-30T09:00:00+00:00
fetched_at: 2026-05-01T13:12:35.442955+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RFC 9449 中的 DPoP（Demonstration of Proof-of-Possession）雖然相比無狀態 bearer token 是有意義的升級，但在瀏覽器金鑰儲存方面存在架構決策真空。RFC 對金鑰儲存的沉默導致每個團隊必須主動評估與選擇方案——不存在一個處處適用的安全預設值。文章指出 DPoP 確實解決了 OAuth 2.0 中的真實問題，但其安全性最終取決於實踐層面的金鑰儲存決策。各團隊需根據自身威脅模型與用戶體驗需求進行權衡。"
key_points:
  - "DPoP 相比 bearer token 是有意義的升級，但需配合正確的金鑰儲存方案"
  - "瀏覽器金鑰儲存無安全預設值：localStorage vs. Memory vs. IndexedDB 各有風險"
  - "RFC 9449 的沉默創造決策真空，團隊需主動評估威脅模型與用戶體驗的平衡"
tags: [dpop, oauth2.0, browser-security, authentication, proof-of-possession]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: The DPoP Storage Paradox: Why Browser-Based Proof-of-Possession Remains an Unsolved Problem

RFC 9449 中的 DPoP（Demonstration of Proof-of-Possession）雖然相比無狀態 bearer token 是有意義的升級，但在瀏覽器金鑰儲存方面存在架構決策真空。RFC 對金鑰儲存的沉默導致每個團隊必須主動評估與選擇方案——不存在一個處處適用的安全預設值。文章指出 DPoP 確實解決了 OAuth 2.0 中的真實問題，但其安全性最終取決於實踐層面的金鑰儲存決策。各團隊需根據自身威脅模型與用戶體驗需求進行權衡。

### 重點
- DPoP 相比 bearer token 是有意義的升級，但需配合正確的金鑰儲存方案
- 瀏覽器金鑰儲存無安全預設值：localStorage vs. Memory vs. IndexedDB 各有風險
- RFC 9449 的沉默創造決策真空，團隊需主動評估威脅模型與用戶體驗的平衡

**原文：** [infoq-architecture](https://www.infoq.com/articles/dpop-key-storage-unsolved-problem/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/articles/dpop-key-storage-unsolved-problem/en/headerimage/dpop-key-storage-unsolved-problem-header-1777296488937.jpg" /><p>DPoP closes a real gap in OAuth 2.0. Sender-constrained tokens are a meaningful upgrade over bearer tokens for any client that can implement them. But RFC 9449's silence on browser key storage creates the need for an architectural decision that each team must confront deliberately — there is no safe default that works everywhere.</p> <i>By Dhruv Agnihotri</i>

</details>