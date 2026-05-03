---
id: inbox_1fa4ea97
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-localllama-hybrid-on-device-inference-on-android-ll-139f]]"
title: "Hybrid on-device inference on Android: llama.cpp + LiteRT + NPU/GPU routing"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t1l7xj/hybrid_ondevice_inference_on_android_llamacpp/
source: reddit-localllama
published_at: 2026-05-02T09:31:55+00:00
fetched_at: 2026-05-03T02:01:50.206809+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開源項目 Box 是 Google AI Edge Gallery 的分支，實現完全離線 Android 端側 AI 助手。整合 llama.cpp（LLM 推理）、whisper.cpp（語音識別）、stable-diffusion.cpp（圖像生成）與 LiteRT，支持 GPU/NPU/TPU 硬體加速。核心發現包括：LiteRT + llama.cpp 混合推理在新一代 Snapdragon/Pixel NPU 上表現超出預期；模型路由策略的影響力超過原始模型大小；Whisper.cpp 仍是最穩定的完全離線 STT 方案；記憶體與持久化瓶頸往往早於計算瓶頸出現。支持語音對話、即時視覺問答、本地 Stable Diffusion 圖生、文檔內容注入等功能。"
key_points:
  - "LiteRT + llama.cpp 混合推理在 Snapdragon/Pixel NPU 上表現超預期；模型路由比原始模型大小更決定效能"
  - "端側完全離線堆棧整合語音、視覺、圖生，支持 GPU/NPU/TPU 自動選取硬體加速"
  - "記憶體與持久化管理是移動端推理實際瓶頸，優先於原始計算資源"
tags: [on-device-inference, android, llama-cpp, multimodal, npu-optimization]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Hybrid on-device inference on Android: llama.cpp + LiteRT + NPU/GPU routing

開源項目 Box 是 Google AI Edge Gallery 的分支，實現完全離線 Android 端側 AI 助手。整合 llama.cpp（LLM 推理）、whisper.cpp（語音識別）、stable-diffusion.cpp（圖像生成）與 LiteRT，支持 GPU/NPU/TPU 硬體加速。核心發現包括：LiteRT + llama.cpp 混合推理在新一代 Snapdragon/Pixel NPU 上表現超出預期；模型路由策略的影響力超過原始模型大小；Whisper.cpp 仍是最穩定的完全離線 STT 方案；記憶體與持久化瓶頸往往早於計算瓶頸出現。支持語音對話、即時視覺問答、本地 Stable Diffusion 圖生、文檔內容注入等功能。

### 重點
- LiteRT + llama.cpp 混合推理在 Snapdragon/Pixel NPU 上表現超預期；模型路由比原始模型大小更決定效能
- 端側完全離線堆棧整合語音、視覺、圖生，支持 GPU/NPU/TPU 自動選取硬體加速
- 記憶體與持久化管理是移動端推理實際瓶頸，優先於原始計算資源

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t1l7xj/hybrid_ondevice_inference_on_android_llamacpp/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1l7xj/hybrid_ondevice_inference_on_android_llamacpp/"> <img alt="Hybrid on-device inference on Android: llama.cpp + LiteRT + NPU/GPU routing" src="https://preview.redd.it/ty4as6o41pyg1.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=9b178ddbe2328901a1128bf42ae9ddb13183af90" title="Hybrid on-device inference on Android: llama.cpp + LiteRT + NPU/GPU routing" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Hi everyone,</p> <p>I’m the maintainer of <strong>Box</strong> — a fork of Google’s AI Edge Gallery that I’ve been extending into a fully offline AI assistant for Android.</p> <p>Full disclosure: I built this project.</p> <p>It runs entirely on-device (no cloud, no accounts, no external inference), and combines multiple local inference backends in a single app.</p> <hr /> <h2>What I’ve been experimenting with</h2> <p>The goal was to see how far a <em>fully offline mobile AI stack</em> could be pushed using:</p> <ul> <li>llama.cpp (GGUF LLM inference)</li> <li>whisper.cpp (on-device STT)</li> <li>stable-diffusion.cpp (image generation)</li> <li>LiteRT (Google’s on-device runtime)</li> </ul> <p>All running on Android with hardware acceleration where available (GPU / NPU / TPU).</p> <hr /> <h2>Current capabilities</h2> <ul> <li>Voice-to-voice conversation (streaming style, hands-free loop)</li> <li>Vision + voice (live camera frame + natural language Q&amp;A)</li> <li>On-device image generation (Stable Diffusion via GGUF)</li> <li>Document ingestion into context (local files)</li> <li>Custom GGUF model import</li> <li>Runs across CPU / GPU / NPU / TPU (auto-selected)</li> </ul> <hr /> <h2>Architecture focus</h2> <p>What I’ve found interesting while building this:</p> <ul> <li>LiteRT + llama.cpp hybrid inference works better than expected on newer Snapdragon/Pixel NPUs</li> <li>Model routing matters more than raw model size on mobile</li> <li>Whisper.cpp is still the most stable STT layer for fully offline setups</li> <li>Memory + persistence becomes the real bottleneck before compute in many cases</li> </ul> <hr /> <h2>Repo (for reference)</h2> <p><a href="https://github.com/jegly/Box">https://github.com/jegly/Box</a></p> <hr /> <h2>Why I’m posting this here</h2> <p>I’m mainly sharing this for feedback from people also working on local inference systems, especially around:</p> <ul> <li>mobile quantization strategies</li> <li>hybrid runtime routing (CPU/GPU/NPU)</li> <li>multimodal on-device pipelines</li> <li>performance tuning on constrained hardware</li> </ul> <p>Not trying to push adoption — more interested in technical critique than anything else.</p> <hr /> <p>Happy to answer questions or go deeper into any part of the stack if useful.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Healthy_Bedroom5837"> /u/Healthy_Bedroom5837 </a> <br /> <span><a href="https://i.redd.it/ty4as6o41pyg1.png">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1l7xj/hybrid_ondevice_inference_on_android_llamacpp/">[comments]</a></span> </td></tr></table>

</details>