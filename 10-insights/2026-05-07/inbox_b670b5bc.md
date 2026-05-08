---
id: inbox_b670b5bc
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-localllama-qwen-webworld-32b-14b-8b-qwen3-finetune-110b]]"
title: "Qwen/WebWorld 32B/14B/8B (Qwen3 finetune)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t6c6vs/qwenwebworld_32b14b8b_qwen3_finetune/
source: reddit-localllama
published_at: 2026-05-07T14:28:47+00:00
fetched_at: 2026-05-08T08:05:33.122211+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Qwen 開源發佈 WebWorld 世界模型系列（32B、14B、8B），這是基於 1M+ 真實網絡交互軌跡訓練的大規模網絡智能體模型。支持長視野模擬（30+ 步）、多格式狀態表示 (A11y Tree、HTML、XML、Markdown、自然語言)、以及跨域泛化到代碼、GUI 和遊戲環境。在 MiniWob++ 和 WebArena 基準測試上分別達到 +9.9% 和 +10.9% 的改進，推理時前向搜尋超越 GPT-5 的世界模型性能。"
key_points:
  - "WebWorld 基於 1M+ 真實網絡交互軌跡訓練，支持 30+ 步長視野模擬"
  - "在 MiniWob++ (+9.9%) 和 WebArena (+10.9%) 上顯著超越基線"
  - "推理時前向搜尋性能超越 GPT-5 作為世界模型"
tags: [qwen, world-model, web-agent, foundation-model, finetune]
topics: []
importance: 4
novelty: 5
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen/WebWorld 32B/14B/8B (Qwen3 finetune)

Qwen 開源發佈 WebWorld 世界模型系列（32B、14B、8B），這是基於 1M+ 真實網絡交互軌跡訓練的大規模網絡智能體模型。支持長視野模擬（30+ 步）、多格式狀態表示 (A11y Tree、HTML、XML、Markdown、自然語言)、以及跨域泛化到代碼、GUI 和遊戲環境。在 MiniWob++ 和 WebArena 基準測試上分別達到 +9.9% 和 +10.9% 的改進，推理時前向搜尋超越 GPT-5 的世界模型性能。

### 重點
- WebWorld 基於 1M+ 真實網絡交互軌跡訓練，支持 30+ 步長視野模擬
- 在 MiniWob++ (+9.9%) 和 WebArena (+10.9%) 上顯著超越基線
- 推理時前向搜尋性能超越 GPT-5 作為世界模型

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t6c6vs/qwenwebworld_32b14b8b_qwen3_finetune/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

WebWorld is a large-scale open-web world model series for training and evaluating web agents. It is trained on 1M+ real-world web interaction trajectories via a scalable hierarchical data pipeline, supporting: Long-horizon simulation (30+ steps) Multi-format state representations : A11y Tree, HTML, XML, Markdown, and natural language CoT-activated reasoning for transition prediction Cross-domain generalization to code, GUI, and game environments Agents trained on WebWorld-synthesized trajectories achieve +9.9% on MiniWob++ and +10.9% on WebArena . When used for inference-time lookahead search, WebWorld outperforms GPT-5 as a world model. https://huggingface.co/Qwen/WebWorld-32B https://huggingface.co/Qwen/WebWorld-14B https://huggingface.co/Qwen/WebWorld-8B &#32; submitted by &#32; /u/jacek2023 [link] &#32; [comments]

</details>