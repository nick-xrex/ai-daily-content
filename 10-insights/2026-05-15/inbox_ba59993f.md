---
id: inbox_ba59993f
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_ba59993f]]"
title: "ByteDance-Seed/Cola-DLM · Hugging Face"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdtaqt/bytedanceseedcoladlm_hugging_face/
source: reddit-localllama
published_at: 2026-05-15T11:19:29+00:00
fetched_at: 2026-05-18T03:57:49.591885+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ByteDance-Seed 發布 Cola-DLM（Continuous Latent Diffusion Language Model），新型分層連續潛在空間擴散語言模型。核心架構：Text VAE 將文本編碼為連續潛在序列，block-causal Diffusion Transformer (DiT) 通過 Flow Matching 進行潛在先驗傳輸，再解碼回 token。採用兩階段訓練（Text VAE 預訓練 + 聯合訓練），OLMo 2 tokenizer（100,278 詞彙表），2000 EFLOPs 計算檢查點，PyTorch 2.1+ 與 Transformers 4.40+ 支持，Apache 2.0 開源。論文已刊登 (arXiv:2605.06548)，GitHub 和 Hugging Face 可取模型。"
key_points:
  - "Cola-DLM 架構：Text VAE + block-causal Diffusion Transformer (DiT) + Flow Matching，實現潛在空間擴散語言建模"
  - "兩階段訓練策略（VAE 預訓練後聯合訓練），OLMo 2 tokenizer，2000 EFLOPs 檢查點報告可重複性"
  - "Apache 2.0 開源，PyTorch 2.1+ / Transformers 4.40+ 技術棧，代表擴散型語言模型的新方向"
tags: [cola-dlm, diffusion-model, language-model, bytedance, latent-diffusion]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## ByteDance-Seed/Cola-DLM · Hugging Face

ByteDance-Seed 發布 Cola-DLM（Continuous Latent Diffusion Language Model），新型分層連續潛在空間擴散語言模型。核心架構：Text VAE 將文本編碼為連續潛在序列，block-causal Diffusion Transformer (DiT) 通過 Flow Matching 進行潛在先驗傳輸，再解碼回 token。採用兩階段訓練（Text VAE 預訓練 + 聯合訓練），OLMo 2 tokenizer（100,278 詞彙表），2000 EFLOPs 計算檢查點，PyTorch 2.1+ 與 Transformers 4.40+ 支持，Apache 2.0 開源。論文已刊登 (arXiv:2605.06548)，GitHub 和 Hugging Face 可取模型。

### 重點
- Cola-DLM 架構：Text VAE + block-causal Diffusion Transformer (DiT) + Flow Matching，實現潛在空間擴散語言建模
- 兩階段訓練策略（VAE 預訓練後聯合訓練），OLMo 2 tokenizer，2000 EFLOPs 檢查點報告可重複性
- Apache 2.0 開源，PyTorch 2.1+ / Transformers 4.40+ 技術棧，代表擴散型語言模型的新方向

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdtaqt/bytedanceseedcoladlm_hugging_face/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# ByteDance-Seed/Cola-DLM · Hugging Face

Cola DLM ( Co ntinuous La tent D iffusion L anguage M odel) is a hierarchical continuous latent-space diffusion language model. It combines a Text VAE with a block-causal Diffusion Transformer (DiT) prior: the VAE maps text into continuous latent sequences and decodes latents back to tokens, while the DiT performs latent prior transport through Flow Matching. This model repository contains the HuggingFace-format checkpoint for the paper Continuous Latent Diffusion Language Model . Links Model repository: https://huggingface.co/ByteDance-Seed/Cola-DLM GitHub repository: https://github.com/ByteDance-Seed/Cola-DLM Paper: https://arxiv.org/abs/2605.06548 HuggingFace Daily Paper: https://huggingface.co/papers/2605.06548 Project page: https://hongcanguo.github.io/Cola-DLM/ Blog post: https://hongcanguo.github.io/posts/2026-cola-dlm.html Zhihu article: https://zhuanlan.zhihu.com/p/2038324180920313704 Model Details Architecture: Text VAE + block-causal DiT latent prior. Training objective: two-stage training with Text VAE pretraining followed by joint Text VAE + DiT training using Flow Matching. Training-compute checkpoint: the released weights correspond to the 2000 EFLOPs checkpoint reported in the paper's RQ4 scaling curve. Tokenizer: OLMo 2 tokenizer with a 100,278-entry vocabulary. Special token ids: pad_token_id=100277 , eos_token_id=100257 , im_end_token_id=100265 . Framework: PyTorch 2.1+ and HuggingFace Transformers 4.40+. License: Apache License 2.0. &#32; submitted by &#32; /u/pmttyji [link] &#32; [comments]

</details>