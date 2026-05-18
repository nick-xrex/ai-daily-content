---
id: inbox_d9c6eca4
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_d9c6eca4]]"
title: "Automated AI researcher running locally with llama.cpp"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tcu5r8/automated_ai_researcher_running_locally_with/
source: reddit-localllama
published_at: 2026-05-14T10:32:04+00:00
fetched_at: 2026-05-18T03:42:53.808518+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hugging Face 發布 ml-intern：自動 AI 研究員工具，原為 Claude Opus 設計，現已支援本地模型 via llama.cpp/ollama。Qwen3.6-35B-A3B 可端到端自動執行監督微調（SFT），包含 CPU/GPU 沙箱與 Hub 基礎設施編排。核心價值：AI 研究員可在筆記本 24/7 運行，無 token 限制，同時與 HF 生態（transformers、datasets、trl）緊密整合。"
key_points:
  - "開源模型（如 Qwen3.6-35B-A3B）已足以勝任多步 agent 工作流，打破「agent 必須用 Claude Opus」的認知"
  - "本地化 + 開源 = 24/7 自動研究無 token 限制成本，降低企業和研究機構的成本負擔"
  - "與 Hugging Face Hub 深度整合，簡化模型上傳、資料集載入、訓練任務編排"
tags: [huggingface, agents, local-llm, qwen, research]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Automated AI researcher running locally with llama.cpp

Hugging Face 發布 ml-intern：自動 AI 研究員工具，原為 Claude Opus 設計，現已支援本地模型 via llama.cpp/ollama。Qwen3.6-35B-A3B 可端到端自動執行監督微調（SFT），包含 CPU/GPU 沙箱與 Hub 基礎設施編排。核心價值：AI 研究員可在筆記本 24/7 運行，無 token 限制，同時與 HF 生態（transformers、datasets、trl）緊密整合。

### 重點
- 開源模型（如 Qwen3.6-35B-A3B）已足以勝任多步 agent 工作流，打破「agent 必須用 Claude Opus」的認知
- 本地化 + 開源 = 24/7 自動研究無 token 限制成本，降低企業和研究機構的成本負擔
- 與 Hugging Face Hub 深度整合，簡化模型上傳、資料集載入、訓練任務編排

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tcu5r8/automated_ai_researcher_running_locally_with/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Automated AI researcher running locally with llama.cpp

Hi everyone, I'm happy to share ml-intern, which is a harness for agents to have tighter integration with Hugging Face's open-source libraries (transformers, datasets, trl, etc) and Hub infrastructure: https://github.com/huggingface/ml-intern The harness is quite simple (basically tools + system prompt) and we built it initially for Claude Opus. However, now that open models are getting really good at agentic workflows, I just added support for running ml-intern with local models via llama.cpp or ollama. As you can see in the video, Qwen3.6-35B-A3B is able to SFT a model end-to-end by orchestrating CPU/GPU sandboxes and jobs on the Hub. I find this pretty neat because we can now have an AI researcher running 24/7 on a laptop, without maxing out token limits :) Anyway, I hope this is useful to the community and please let me know if there are any features that you'd like us to include. &#32; submitted by &#32; /u/lewtun [link] &#32; [comments]

</details>