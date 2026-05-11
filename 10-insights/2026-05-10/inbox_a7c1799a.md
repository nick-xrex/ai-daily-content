---
id: inbox_a7c1799a
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_a7c1799a]]"
title: "I cannot decide for local OCR model for most of the tasks preferably I would like more individual experiences than reviews."
url: https://www.reddit.com/r/LocalLLaMA/comments/1t993om/i_cannot_decide_for_local_ocr_model_for_most_of/
source: reddit-localllama
published_at: 2026-05-10T14:54:47+00:00
fetched_at: 2026-05-11T02:24:43.312194+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者有 16GB VRAM GPU，尋求本地 OCR 模型且限制在 9-10GB 記憶體用量（不超過 60%）以保持 GPU 待命。應用場景包括截圖、掃描 PDF 文件、收據與表單識別。評估的候選方案有 PaddleOCR、Surya、Tesseract 等，期望 2026 年實戰經驗而非基準評測。"
key_points:
  - "本地 OCR 模型在 VRAM 限制下選擇困難（目標 <10GB for 16GB GPU）"
  - "常見候選模型：PaddleOCR、Surya、Tesseract、小型視覺語言模型"
  - "使用者重視實用可靠性與資源效率而非基準分數"
tags: [ocr, local-deployment, vram-optimization, paddleocr, surya]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## I cannot decide for local OCR model for most of the tasks preferably I would like more individual experiences than reviews.

使用者有 16GB VRAM GPU，尋求本地 OCR 模型且限制在 9-10GB 記憶體用量（不超過 60%）以保持 GPU 待命。應用場景包括截圖、掃描 PDF 文件、收據與表單識別。評估的候選方案有 PaddleOCR、Surya、Tesseract 等，期望 2026 年實戰經驗而非基準評測。

### 重點
- 本地 OCR 模型在 VRAM 限制下選擇困難（目標 <10GB for 16GB GPU）
- 常見候選模型：PaddleOCR、Surya、Tesseract、小型視覺語言模型
- 使用者重視實用可靠性與資源效率而非基準分數

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t993om/i_cannot_decide_for_local_ocr_model_for_most_of/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I cannot decide for local OCR model for most of the tasks preferably I would like more individual experiences than reviews.

I have a 16GB VRAM GPU and I'm looking for a reliable local OCR model. Ideally it should stay under ~60% VRAM usage, so around 9–10GB max, because I want to keep it available on-demand rather than loading a huge model only for occasional batch jobs. There are a lot of OCR models claiming to be &quot;the best&quot;, but I care more about reliability and practical day-to-day use than benchmark hype. Use cases: screenshots scanned documents / PDFs eceipts or forms general image-to-text extraction I'm looking at options like PaddleOCR, Surya, Tesseract, and maybe small vision-language models, but I'm not sure what people are actually using locally in 2026. What would you recommend for a good balance of accuracy, VRAM usage, and reliability? &#32; submitted by &#32; /u/thecowmilk_ [link] &#32; [comments]

</details>