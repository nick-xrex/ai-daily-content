---
id: inbox_e6e3552f
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_e6e3552f]]"
title: "Frontier models can&#39;t run on satellites. Here&#39;s an end-to-end wildfire detection pipeline using a 450M on-board Vision-Language Model (Sentinel-2 + LFM2.5-VL)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t36myv/frontier_models_cant_run_on_satellites_heres_an/
source: reddit-localllama
published_at: 2026-05-04T03:48:22+00:00
fetched_at: 2026-05-04T14:27:18.243608+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者分享衛星野火預警系統設計，核心洞見為：設計瓶頸非模型品質而是頻寬。在衛星上執行 450M Vision-Language Model (LFM2.5-VL-450M) 本地推理，只下傳 JSON 風險檔案而非龐大多譜影像矩陣。技術方案：RGB (B4-B3-B2) + SWIR (B12-B8-B4) 多譜 tile 組合，SWIR 擷取植被濕度壓力（真實燃料指標）；VLM 整合多模態獲得場景整體理解而非純像素統計，輸出結構化 risk_level 與細目。PoC 架構以 SimSat (Docker) 模擬軌道、從 AWS Element84 STAC 目錄供應真實 Sentinel-2 資料、llama-server 運行 VLM、監控迴路輪詢位置與執行推理、SQLite 存儲、Streamlit 前端視覺化 22 個易火災地點（雅典、天使國家森林、婆羅洲等）預測結果。後續計劃涵蓋資料收集標籤、評估、微調以縮小與 Opus 級的性能差距。"
key_points:
  - "邊界推理框架：模型大小非關鍵，頻寬才是瓶頸 → 小型 VLM 在軌道推理優於地面大模型下傳影像；450M 參數自給自足"
  - "多譜信號組合設計：SWIR 擷取植被濕度（真實燃料指標），VLM 整合 SWIR+RGB 的多模態場景理解而非統計分析"
  - "端到端 PoC 成形：SimSat 軌道模擬 + Sentinel-2 真實資料 + llama-server 推理 + SQLite + Streamlit，24 地點監控框架就緒，後續微調望拉近與超大模型的性能差距"
tags: [edge-inference, vision-language-model, satellite, wildfire-detection, geospatial-ai]
topics: []
importance: 4
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Frontier models can't run on satellites. Here's an end-to-end wildfire detection pipeline using a 450M on-board Vision-Language Model (Sentinel-2 + LFM2.5-VL)

開發者分享衛星野火預警系統設計，核心洞見為：設計瓶頸非模型品質而是頻寬。在衛星上執行 450M Vision-Language Model (LFM2.5-VL-450M) 本地推理，只下傳 JSON 風險檔案而非龐大多譜影像矩陣。技術方案：RGB (B4-B3-B2) + SWIR (B12-B8-B4) 多譜 tile 組合，SWIR 擷取植被濕度壓力（真實燃料指標）；VLM 整合多模態獲得場景整體理解而非純像素統計，輸出結構化 risk_level 與細目。PoC 架構以 SimSat (Docker) 模擬軌道、從 AWS Element84 STAC 目錄供應真實 Sentinel-2 資料、llama-server 運行 VLM、監控迴路輪詢位置與執行推理、SQLite 存儲、Streamlit 前端視覺化 22 個易火災地點（雅典、天使國家森林、婆羅洲等）預測結果。後續計劃涵蓋資料收集標籤、評估、微調以縮小與 Opus 級的性能差距。

### 重點
- 邊界推理框架：模型大小非關鍵，頻寬才是瓶頸 → 小型 VLM 在軌道推理優於地面大模型下傳影像；450M 參數自給自足
- 多譜信號組合設計：SWIR 擷取植被濕度（真實燃料指標），VLM 整合 SWIR+RGB 的多模態場景理解而非統計分析
- 端到端 PoC 成形：SimSat 軌道模擬 + Sentinel-2 真實資料 + llama-server 推理 + SQLite + Streamlit，24 地點監控框架就緒，後續微調望拉近與超大模型的性能差距

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t36myv/frontier_models_cant_run_on_satellites_heres_an/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Frontier models can't run on satellites. Here's an end-to-end wildfire detection pipeline using a 450M on-board Vision-Language Model (Sentinel-2 + LFM2.5-VL)

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t36myv/frontier_models_cant_run_on_satellites_heres_an/"> <img alt="Frontier models can't run on satellites. Here's an end-to-end wildfire detection pipeline using a 450M on-board Vision-Language Model (Sentinel-2 + LFM2.5-VL)" src="https://external-preview.redd.it/q-RB-BrpAYxOG2SVwPnlsMXhvONmJgEyABfnnCcu_Mo.jpeg?width=640&amp;crop=smart&amp;auto=webp&amp;s=05ffbf969263cec379a1b0952c96ad198a887e00" title="Frontier models can't run on satellites. Here's an end-to-end wildfire detection pipeline using a 450M on-board Vision-Language Model (Sentinel-2 + LFM2.5-VL)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Sharing a project I've been building: a full end-to-end wildfire prevention pipeline that runs a Vision-Language Model directly on a satellite, using Sentinel-2 imagery.</p> <p>The interesting design constraint isn't model quality. It's bandwidth. A frontier model on the ground means downlinking massive multispectral image matrices per orbit, which doesn't scale. A 450M VLM small enough to run on-board flips it: do inference in space, downlink only the JSON risk profile.</p> <p>The pipeline pairs RGB (B4-B3-B2) with SWIR (B12-B8-B4) tiles. SWIR is the key signal. It captures vegetation moisture stress, which is the actual fuel indicator for fires. The VLM gets holistic scene understanding instead of just pixel stats, and outputs a structured <code>risk_level</code> plus breakdown.</p> <p>For the PoC I'm simulating the on-board pipeline locally:</p> <ul> <li><strong>SimSat</strong> (Docker) simulates orbit and serves real Sentinel-2 from the AWS Element84 STAC catalog</li> <li><strong>LFM2.5-VL-450M</strong> runs locally via <code>llama-server</code></li> <li>A watch loop polls position, fetches the image pair, runs inference, writes to SQLite</li> <li>Streamlit app on top to visualize predictions across 22 fire-prone locations (Attica, Angeles National Forest, Borneo, etc.)</li> </ul> <p>This post covers problem framing and system design. The next ones cover data collection and labelling, evals, and fine-tuning, because out-of-the-box, a 450M VLM is not Opus-tier and you need to close that gap deliberately.</p> <p>Code's in the Liquid AI Cookbook (link below). Curious what people think about on-device or on-edge inference for this kind of geospatial use case. Anyone doing similar work with constrained-bandwidth deployments?</p> <p><strong>Full write-up:</strong> <a href="https://github.com/Liquid4All/cookbook/tree/main/examples/wildfire-prevention">https://github.com/Liquid4All/cookbook/tree/main/examples/wildfire-prevention</a></p> <p><strong>Code:</strong> <a href="https://github.com/Liquid4All/cookbook/tree/main/examples/wildfire-prevention"><strong>https://github.com/Liquid4All/cookbook/tree/main/examples/wildfire-prevention</strong></a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/PauLabartaBajo"> /u/PauLabartaBajo </a> <br /> <span><a href="https://paulabartabajo.substack.com/p/how-to-build-end-2-end-systems-with">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t36myv/frontier_models_cant_run_on_satellites_heres_an/">[comments]</a></span> </td></tr></table>

</details>