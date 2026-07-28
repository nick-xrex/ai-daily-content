---
id: inbox_edd0cfec
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_edd0cfec]]"
title: "How I Reproduced BM25, Dense Retrieval, and SPLADE on a 16GB MacBook"
url: https://towardsdatascience.com/how-i-reproduced-bm25-dense-retrieval-and-splade-on-a-16gb-macbook/
source: medium-towards-data-science
published_at: 2026-07-27T12:00:00+00:00
fetched_at: 2026-07-28T01:21:14.905162+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章實踐性地重現了三種檢索演算法（BM25、Dense Retrieval、SPLADE）在 16GB MacBook 上的實現。記錄開發過程中遇到的記憶體崩潰、修復方案及性能分數驗證步驟，為構建本地 RAG 系統的開發者提供了務實參考。展示如何透過最佳化在消費級硬體上部署多種檢索方法，對降低 RAG 系統開發成本有指導意義。"
key_points:
  - "BM25、Dense Retrieval、SPLADE 三種檢索演算法在 16GB 消費級硬體上的實現驗證"
  - "記憶體優化與崩潰修復的具體技巧與最佳實踐"
  - "性能評分檢查與驗證步驟，確保 RAG 系統正確性"
tags: [retrieval-algorithms, rag, dense-retrieval, splade, consumer-hardware]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## How I Reproduced BM25, Dense Retrieval, and SPLADE on a 16GB MacBook

文章實踐性地重現了三種檢索演算法（BM25、Dense Retrieval、SPLADE）在 16GB MacBook 上的實現。記錄開發過程中遇到的記憶體崩潰、修復方案及性能分數驗證步驟，為構建本地 RAG 系統的開發者提供了務實參考。展示如何透過最佳化在消費級硬體上部署多種檢索方法，對降低 RAG 系統開發成本有指導意義。

### 重點
- BM25、Dense Retrieval、SPLADE 三種檢索演算法在 16GB 消費級硬體上的實現驗證
- 記憶體優化與崩潰修復的具體技巧與最佳實踐
- 性能評分檢查與驗證步驟，確保 RAG 系統正確性

**原文：** [medium-towards-data-science](https://towardsdatascience.com/how-i-reproduced-bm25-dense-retrieval-and-splade-on-a-16gb-macbook/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# How I Reproduced BM25, Dense Retrieval, and SPLADE on a 16GB MacBook

A practical reproduction of three retrieval baselines, including the crashes, fixes, and score checks that matter for RAG systems. 
 The post How I Reproduced BM25, Dense Retrieval, and SPLADE on a 16GB MacBook appeared first on Towards Data Science .

</details>