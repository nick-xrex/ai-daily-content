---
id: inbox_6922af71
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-localllama-collected-the-infinity-stones-0cf4]]"
title: "Collected the infinity stones"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t6pw92/collected_the_infinity_stones/
source: reddit-localllama
published_at: 2026-05-07T22:39:57+00:00
fetched_at: 2026-05-08T08:02:51.414412+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LocalLLaMA 社群成員展示實驗性異構推理集群，配置 2.3TB 記憶體與 400+ vCores，規劃以 Blackwell 處理前綴階段(prefill)、透過 RDMA 連接 studio mesh 進行解碼階段(decode)。此設計體現異構計算的可行性，若完成 Tinygrad 驅動支援，將開啟首個異構叢集在本地 LLM 推理中的應用先例，對模型服務吞吐量優化有借鑑意義。"
key_points:
  - "異構架構：Blackwell prefill + RDMA decode 分工，避免單一硬體瓶頸"
  - "規模：2.3TB RAM、400+ vCores，支援大模型並行推理"
  - "技術瓶頸：待 Tinygrad 驅動完善 RDMA 通訊支援"
tags: [異構計算, prefill-decode分工, blackwell, rdma]
topics: []
importance: 2
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Collected the infinity stones

LocalLLaMA 社群成員展示實驗性異構推理集群，配置 2.3TB 記憶體與 400+ vCores，規劃以 Blackwell 處理前綴階段(prefill)、透過 RDMA 連接 studio mesh 進行解碼階段(decode)。此設計體現異構計算的可行性，若完成 Tinygrad 驅動支援，將開啟首個異構叢集在本地 LLM 推理中的應用先例，對模型服務吞吐量優化有借鑑意義。

### 重點
- 異構架構：Blackwell prefill + RDMA decode 分工，避免單一硬體瓶頸
- 規模：2.3TB RAM、400+ vCores，支援大模型並行推理
- 技術瓶頸：待 Tinygrad 驅動完善 RDMA 通訊支援

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t6pw92/collected_the_infinity_stones/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

2.3 TB of ram in here. 400+ vCores. All thats left is plugging it to the blackwell with the driver to do RDMA, and it’s over. Using Blackwells for prefill, RDMA to the studio mesh for decode. I think this would be the first heterogeneous cluster. I do, however, need help with the Tinygrad Driver to make this work. If anyone with any knowledge on these domains would like to collaborate, let me know via PM. We are very close here. &#32; submitted by &#32; /u/Street-Buyer-2428 [link] &#32; [comments]

</details>