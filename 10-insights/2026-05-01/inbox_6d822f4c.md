---
id: inbox_6d822f4c
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/1257-reddit-localllama-16x-spark-cluster-build-update-610a]]"
title: "16x Spark Cluster (Build Update)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t0lwx6/16x_spark_cluster_build_update/
source: reddit-localllama
published_at: 2026-05-01T07:00:58+00:00
fetched_at: 2026-05-01T13:30:13.946325+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "16 節點 DGX Spark 叢集完成部署與驗證。統一記憶體設計優於分散 H100 配置，可服務 GLM-5.1-NVFP4（434GB）於 TP=8 拓展。FS 200Gbps 結構交換機支援雙通道，實測 100–111 Gbps/通道（聚合 200 Gbps）。後續規劃：搭配 M5 Ultra Mac Studios 執行 Prefill/Decode 分離架構，以 Spark 叢集擔當 Prefill（平行吞吐最大化）、Mac Studios 擔當 Decode。機架包含防火牆、NAS（374TB U.2）、工作站與備份系統，工程化完整。"
key_points:
  - "16×DGX Spark 統一記憶體叢集可推理 434GB GLM-5.1-NVFP4 模型，TP=8，相較於單節點 H100 更具記憶體優勢"
  - "200Gbps 結構網路（FS QSFP56 交換機），實現雙通道 100–111 Gbps，符合設計規格"
  - "Prefill/Decode 分離架構：Spark 集中處理高平行度預填充，後續整合 M5 Ultra Mac Studios 專責解碼，優化端到端延遲"
tags: [dgx-spark-cluster, inference-infrastructure, unified-memory, prefill-decode-split]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## 16x Spark Cluster (Build Update)

16 節點 DGX Spark 叢集完成部署與驗證。統一記憶體設計優於分散 H100 配置，可服務 GLM-5.1-NVFP4（434GB）於 TP=8 拓展。FS 200Gbps 結構交換機支援雙通道，實測 100–111 Gbps/通道（聚合 200 Gbps）。後續規劃：搭配 M5 Ultra Mac Studios 執行 Prefill/Decode 分離架構，以 Spark 叢集擔當 Prefill（平行吞吐最大化）、Mac Studios 擔當 Decode。機架包含防火牆、NAS（374TB U.2）、工作站與備份系統，工程化完整。

### 重點
- 16×DGX Spark 統一記憶體叢集可推理 434GB GLM-5.1-NVFP4 模型，TP=8，相較於單節點 H100 更具記憶體優勢
- 200Gbps 結構網路（FS QSFP56 交換機），實現雙通道 100–111 Gbps，符合設計規格
- Prefill/Decode 分離架構：Spark 集中處理高平行度預填充，後續整合 M5 Ultra Mac Studios 專責解碼，優化端到端延遲

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t0lwx6/16x_spark_cluster_build_update/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0lwx6/16x_spark_cluster_build_update/"> <img alt="16x Spark Cluster (Build Update)" src="https://preview.redd.it/lh1wlzoi5hyg1.jpeg?width=640&amp;crop=smart&amp;auto=webp&amp;s=9a808f325dc1c52ee929cf060a2e3d01f4bd643f" title="16x Spark Cluster (Build Update)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Build is done. 16 DGX Sparks on the fabric, all hitting line rate.</p> <p>Setup was time consuming but honestly smoother than I expected. Each Spark runs Nvidia’s flavor of Ubuntu out of the box with mostly everything pre installed and ready to go. For setup I had to rack them, power on, create the same user/pass across all nodes, wait about 20 minutes per node for updates, then configure passwordless SSH, jumbo frames, IPs, etc. which I scripted to save time.</p> <p>Each Spark connects to the FS N8510 switch with a single QSFP56 cable. The DGX Spark bonds its two NIC interfaces into each port, so you get dual rail over one cable. I'm seeing 100 to 111 Gbps per rail, which aggregates to the advertised 200 Gbps.</p> <p><strong>Why this over H100s or a GB300?</strong> </p> <p>Unified memory. The whole point is maximizing unified memory capacity within the Nvidia ecosystem. With 8 nodes I was serving GLM-5.1-NVFP4 (434GB) at TP=8. Now going to test with DeepSeek and Kimi</p> <p>The longer term plan is a prefill/decode split. The Spark cluster handles prefill (massive parallel throughput), and once the M5 Ultra Mac Studios drop I'll add 2 to 4 into the rack for decode.</p> <p>—</p> <p>Full rack, top to bottom:</p> <p>- 1U Brush Panel</p> <p>- OPNSense Firewall</p> <p>- Mikrotik 10Gb switch (internet uplink)</p> <p>- Mikrotik 100Gb switch (HPC to NAS)</p> <p>- 1U Brush Panel</p> <p>- QNAP 374TB all U.2 NAS</p> <p>- Management Server</p> <p>- Dual 4090 Workstation</p> <p>- Backup Dual 4090 Workstation (identical specs)</p> <p>- FS 200Gbps QSFP56 Fabric Switch (Spark cluster)</p> <p>- 1U Brush Panel</p> <p>- 8x DGX Spark Shelf One</p> <p>- 8x DGX Spark Shelf Two</p> <p>- 2U Spacer Panel</p> <p>- SuperMicro 4x H100 NVL Station</p> <p>- GH200</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Kurcide"> /u/Kurcide </a> <br /> <span><a href="https://i.redd.it/lh1wlzoi5hyg1.jpeg">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0lwx6/16x_spark_cluster_build_update/">[comments]</a></span> </td></tr></table>

</details>