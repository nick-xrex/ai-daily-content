---
id: inbox_ce66ecce
date: 2026-05-09
source_ref: "[[00-inbox/2026-05-09/0151-reddit-localllama-qwen3-6-35b-a3b-uncensored-heretic-nativ-c09e]]"
title: "Qwen3.6 35B A3B uncensored heretic Native MTP Preserved is Out Now With KLD 0.0015, 10/100 Refusals and the Full 19 MTPs Preserved and Retained, Available in Safetensors, GGUFs. NVFP4, NVFP4 GGUFs and GPTQ-Int4 Formats"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t7qfaq/qwen36_35b_a3b_uncensored_heretic_native_mtp/
source: reddit-localllama
published_at: 2026-05-09T01:06:22+00:00
fetched_at: 2026-05-09T02:26:09.331180+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Qwen3.6-35B-A3B uncensored版本发布，提供Safetensors、GGUF、NVFP4、GPTQ-Int4等多种量化格式。发布版本明确保留完整的19/20个MTP（Multi-Token Prediction）张量，并验证了格式间的结构一致性。这是基于Qwen3.6的社区微调模型。"
key_points:
  - "Qwen3.6-35B-A3B uncensored版本支持4种量化格式（Safetensors / GGUF / NVFP4 / GPTQ-Int4）"
  - "完整保留MTP张量：Safetensors格式显示19个条目，GGUF格式20个（因gate_up_proj的融合方式）"
  - "KLD 0.0015，refusal rate 10/100，适合需要低审查的应用场景"
tags: [qwen3.6, model-release, quantization, mtp-preservation, uncensored]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3.6 35B A3B uncensored heretic Native MTP Preserved is Out Now With KLD 0.0015, 10/100 Refusals and the Full 19 MTPs Preserved and Retained, Available in Safetensors, GGUFs. NVFP4, NVFP4 GGUFs and GPTQ-Int4 Formats

Qwen3.6-35B-A3B uncensored版本发布，提供Safetensors、GGUF、NVFP4、GPTQ-Int4等多种量化格式。发布版本明确保留完整的19/20个MTP（Multi-Token Prediction）张量，并验证了格式间的结构一致性。这是基于Qwen3.6的社区微调模型。

### 重點
- Qwen3.6-35B-A3B uncensored版本支持4种量化格式（Safetensors / GGUF / NVFP4 / GPTQ-Int4）
- 完整保留MTP张量：Safetensors格式显示19个条目，GGUF格式20个（因gate_up_proj的融合方式）
- KLD 0.0015，refusal rate 10/100，适合需要低审查的应用场景

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t7qfaq/qwen36_35b_a3b_uncensored_heretic_native_mtp/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved: https://huggingface.co/llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved-GGUF: https://huggingface.co/llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved-GGUF llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved-NVFP4-Experts-Only: https://huggingface.co/llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved-NVFP4-Experts-Only llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved-NVFP4-Experts-Only-GGUF: https://huggingface.co/llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved-NVFP4-Experts-Only-GGUF llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved-GPTQ-Int4: https://huggingface.co/llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-Native-MTP-Preserved-GPTQ-Int4 People asked for it, so here it is, all realeases are confirmed to have their full MTP count* retained and preserved. Comes with benchmark too. Find all my models here: HuggingFace-LLMFan46 *All releases have been verified to retain the full MTP tensors. In safetensors format, the Qwen3.6-35B-A3B MTP tensors appear as 19 entries because `gate_up_proj` is stored as one fused tensor. In GGUF format, that fused tensor is split into separate gate/up expert tensors, so the same MTP component appears as 20 entries. The count differs by format, but the MTP tensors are preserved. &#32; submitted by &#32; /u/LLMFan46 [link] &#32; [comments]

</details>