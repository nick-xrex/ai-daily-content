---
id: inbox_621da82b
date: 2026-07-21
source_ref: "[[00-inbox/2026-07-21/0016-infoq-main-yelp-unifies-ml-model-training-with-trai-556e]]"
title: "Yelp Unifies ML Model Training with Training Orchestrator"
url: https://www.infoq.com/news/2026/07/yelp-ai-model-training/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-21T10:00:00+00:00
fetched_at: 2026-07-22T00:25:37.742447+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Yelp 推出內部框架 Training Orchestrator，用來統一機器學習模型訓練工作流。此框架取代各團隊個別維護的 Spark 訓練腳本，採用配置驅動（configuration-driven）與 DAG 為基礎的執行模型。這種設計標準化了訓練基礎設施，減少重複維護成本。文章未披露具體的效能提升數字或涉及的團隊規模。此舉反映大型公司為簡化 ML 基礎設施而進行的基層現代化嘗試。"
key_points:
  - "Training Orchestrator 統一框架取代分散的 Spark 訓練腳本，降低團隊間的維護重複"
  - "採用 DAG 為基礎的執行模型，實現配置驅動的訓練編排，標準化 ML 工作流"
  - "內部工具，未公開具體的效能指標、成本節省或遷移規模"
tags: [ml-training-orchestration, spark, infrastructure-unification]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Yelp Unifies ML Model Training with Training Orchestrator

Yelp 推出內部框架 Training Orchestrator，用來統一機器學習模型訓練工作流。此框架取代各團隊個別維護的 Spark 訓練腳本，採用配置驅動（configuration-driven）與 DAG 為基礎的執行模型。這種設計標準化了訓練基礎設施，減少重複維護成本。文章未披露具體的效能提升數字或涉及的團隊規模。此舉反映大型公司為簡化 ML 基礎設施而進行的基層現代化嘗試。

### 重點
- Training Orchestrator 統一框架取代分散的 Spark 訓練腳本，降低團隊間的維護重複
- 採用 DAG 為基礎的執行模型，實現配置驅動的訓練編排，標準化 ML 工作流
- 內部工具，未公開具體的效能指標、成本節省或遷移規模

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/yelp-ai-model-training/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Yelp has launched Training Orchestrator. This new internal framework replaces individual team Spark training scripts. Now, it uses a configuration-driven, DAG-based execution model. By Claudio Masolo

</details>