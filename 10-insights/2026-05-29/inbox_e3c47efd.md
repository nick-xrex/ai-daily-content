---
id: inbox_e3c47efd
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-medium-tag-llm-ai-doesnt-run-on-vibe-it-runs-on-infra-b94d]]"
title: "AI Doesn’t Run on Vibe. It Runs on Infra"
url: https://medium.com/@mohitmishra3333/ai-doesnt-run-on-vibe-it-runs-on-infra-d6e79aa6348b?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-29T17:40:19+00:00
fetched_at: 2026-05-30T02:29:30.904023+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI 不在演算法，在基礎設施。聚焦 ChatGPT/Claude/Gemini 一個查詢背後的完整棧：(1) 請求路由：DNS/Anycast/CDN/負載均衡；(2) 排程：決定 GPU 叢集、推理 vs 推理基礎設施、模型版本；(3) GPU 執行：H100/H200/B200/MI300 等，每 GPU 數萬美元，一個叢集數千 GPU；(4) 儲存：訓練資料達 PB 規模、模型參數達數兆、嵌入向量達數十億；(5) 網路：InfiniBand/RDMA 低延遲結構，梯度/參數持續交換。核心論點：GPU 成為新油氣、網路架構與 GPU 同等關鍵、計算編排框架（類 Kubernetes）複雜度倍增。"
key_points:
  - "AI 棧複雜度：DNS → CDN → 負載均衡 → GPU 排程 → 矩陣運算 → 分散式網路，任一層瓶頸皆致 GPU 閒置及成本灼傷"
  - "GPU 為新油氣：AI GPU（H100 數萬美元）平行運算能力使訓練週期從年級降至週級、推理從分鐘級降至秒級"
  - "儲存與網路同等關鍵：PB 規模資料集 + InfiniBand 低延遲結構，是 GPU 能否高效工作的決定因素，非只是 GPU 數量"
tags: [ai-infrastructure, gpu-economics, distributed-systems, storage-architecture, network-fabric]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## AI Doesn’t Run on Vibe. It Runs on Infra

AI 不在演算法，在基礎設施。聚焦 ChatGPT/Claude/Gemini 一個查詢背後的完整棧：(1) 請求路由：DNS/Anycast/CDN/負載均衡；(2) 排程：決定 GPU 叢集、推理 vs 推理基礎設施、模型版本；(3) GPU 執行：H100/H200/B200/MI300 等，每 GPU 數萬美元，一個叢集數千 GPU；(4) 儲存：訓練資料達 PB 規模、模型參數達數兆、嵌入向量達數十億；(5) 網路：InfiniBand/RDMA 低延遲結構，梯度/參數持續交換。核心論點：GPU 成為新油氣、網路架構與 GPU 同等關鍵、計算編排框架（類 Kubernetes）複雜度倍增。

### 重點
- AI 棧複雜度：DNS → CDN → 負載均衡 → GPU 排程 → 矩陣運算 → 分散式網路，任一層瓶頸皆致 GPU 閒置及成本灼傷
- GPU 為新油氣：AI GPU（H100 數萬美元）平行運算能力使訓練週期從年級降至週級、推理從分鐘級降至秒級
- 儲存與網路同等關鍵：PB 規模資料集 + InfiniBand 低延遲結構，是 GPU 能否高效工作的決定因素，非只是 GPU 數量

**原文：** [medium-tag-llm](https://medium.com/@mohitmishra3333/ai-doesnt-run-on-vibe-it-runs-on-infra-d6e79aa6348b?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Behind every AI company racing to build smarter models, is an even bigger race to acquire the infra, needed to run them. Continue reading on Medium »

</details>