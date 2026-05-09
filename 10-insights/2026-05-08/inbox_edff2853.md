---
id: inbox_edff2853
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0151-medium-tag-llm-structura-vl-intelligent-document-to-mar-74c7]]"
title: "Structura-VL: Intelligent Document-to-Markdown Transformation"
url: https://medium.com/@ah4402852/structura-vl-intelligent-document-to-markdown-transformation-566296808268?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-08T12:38:10+00:00
fetched_at: 2026-05-09T02:03:29.757048+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Structura-VL 是基於 Qwen2-VL-2B-Instruct 和 QLoRA 微調的文件智能轉換工具。在 Kaggle Dual T4 GPU 上運行，使用 Nougat 數據集訓練，聚焦結構元素識別（嵌套列表、標題、空間層次）。評估結果顯示 ROUGE-1 達 0.7470、ROUGE-L 為 0.7447，驗證了模型複製技術格式細節的精確度。已部署於 Hugging Face Spaces，配備自訂 Gradio 介面實現高通量文件解析，可將掃描文件的視覺結構即時轉換為 Markdown。"
key_points:
  - "Structura-VL 架構：Qwen2-VL-2B-Instruct + QLoRA，訓練集 Nougat，ROUGE-1=0.747、ROUGE-L=0.745"
  - "核心功能：空間感知和階層認知將掃描文件視覺結構轉換為結構化 Markdown，支援嵌套列表和標題層級"
  - "部署形式：Hugging Face Spaces + 自訂 Gradio 介面，實現生產級高通量文件解析"
tags: [document-to-markdown, structura-vl, qwen2-vl, qlora, hugging-face]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Structura-VL: Intelligent Document-to-Markdown Transformation

Structura-VL 是基於 Qwen2-VL-2B-Instruct 和 QLoRA 微調的文件智能轉換工具。在 Kaggle Dual T4 GPU 上運行，使用 Nougat 數據集訓練，聚焦結構元素識別（嵌套列表、標題、空間層次）。評估結果顯示 ROUGE-1 達 0.7470、ROUGE-L 為 0.7447，驗證了模型複製技術格式細節的精確度。已部署於 Hugging Face Spaces，配備自訂 Gradio 介面實現高通量文件解析，可將掃描文件的視覺結構即時轉換為 Markdown。

### 重點
- Structura-VL 架構：Qwen2-VL-2B-Instruct + QLoRA，訓練集 Nougat，ROUGE-1=0.747、ROUGE-L=0.745
- 核心功能：空間感知和階層認知將掃描文件視覺結構轉換為結構化 Markdown，支援嵌套列表和標題層級
- 部署形式：Hugging Face Spaces + 自訂 Gradio 介面，實現生產級高通量文件解析

**原文：** [medium-tag-llm](https://medium.com/@ah4402852/structura-vl-intelligent-document-to-markdown-transformation-566296808268?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

By Ali Hamza &amp; Muhammad Bilal Ahmad Continue reading on Medium »

</details>