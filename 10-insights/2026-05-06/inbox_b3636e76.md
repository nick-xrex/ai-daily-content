---
id: inbox_b3636e76
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/0114-reddit-localllama-get-faster-qwen-3-6-27b-553d]]"
title: "Get faster qwen 3.6 27b"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t5tnzl/get_faster_qwen_36_27b/
source: reddit-localllama
published_at: 2026-05-06T23:33:07+00:00
fetched_at: 2026-05-07T01:29:44.815179+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶分享在 RTX 3090 上使用 Qwen3.6-27B-MTP-Q4_K_M-GGUF 於 100k token 上下文達成 50 tok/s 的配置經驗。建議採用 llama.cpp am17an commit 版本，設置快取量化（KV 快取為 Q4_0）、批次大小 2048、微批次 1024、MTP 推測模式草稿數最多 2（3 個在高上下文時過重）。強調 100k 足夠多數任務，並在必要時壓實續用。"
key_points:
  - "Qwen3.6-27B-MTP-Q4_K_M 在 RTX 3090 上於 100k 上下文達 50 tok/s，使用 llama-cpp am17an commit"
  - "关键配置：KV 快取 Q4_0 量化、批次 2048/微批次 1024、MTP 推測草稿最多 2 token（3 個會導致顯存溢出）"
  - "實踐建議：100k 上下文足夠多數任務，超出該長度後性能明顯下降，建議定期壓實並重新開啟"
tags: [qwen3.6, llama-cpp, kv-cache-quantization, configuration]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Get faster qwen 3.6 27b

用戶分享在 RTX 3090 上使用 Qwen3.6-27B-MTP-Q4_K_M-GGUF 於 100k token 上下文達成 50 tok/s 的配置經驗。建議採用 llama.cpp am17an commit 版本，設置快取量化（KV 快取為 Q4_0）、批次大小 2048、微批次 1024、MTP 推測模式草稿數最多 2（3 個在高上下文時過重）。強調 100k 足夠多數任務，並在必要時壓實續用。

### 重點
- Qwen3.6-27B-MTP-Q4_K_M 在 RTX 3090 上於 100k 上下文達 50 tok/s，使用 llama-cpp am17an commit
- 关键配置：KV 快取 Q4_0 量化、批次 2048/微批次 1024、MTP 推測草稿最多 2 token（3 個會導致顯存溢出）
- 實踐建議：100k 上下文足夠多數任務，超出該長度後性能明顯下降，建議定期壓實並重新開啟

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t5tnzl/get_faster_qwen_36_27b/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Using 100k context with 3090 with MTP GGUF and getting 50 t/s on llama.cpp</p> <p>Thought I would knowledge share</p> <p>Use <a href="https://huggingface.co/RDson/Qwen3.6-27B-MTP-Q4_K_M-GGUF">https://huggingface.co/RDson/Qwen3.6-27B-MTP-Q4_K_M-GGUF</a></p> <p>And am17an commit</p> <p>/media/adam/D_DRIVE/LLM/llama-cpp-am17an/build/bin/llama-server </p> <p>-m &quot;/media/Qwen3.6-27B-Q4/Qwen3.6-27B-MTP-Q4_K_M.gguf&quot; \</p> <p>--ctx-size 100000 \</p> <p>-ngl 99 -fa on \</p> <p>--cache-type-k q4_0 --cache-type-v q4_0 \</p> <p>--batch-size 2048 --ubatch-size 1024 \</p> <p>--spec-type mtp --spec-draft-n-max 2 \</p> <p>--flash-attn</p> <p>Note: Spec draft 3 seemed to much for the 3090 at higher context</p> <p>Why 100k context? Beside it slows down and 100k is enough for most tasks then compact and continue. </p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/admajic"> /u/admajic </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5tnzl/get_faster_qwen_36_27b/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5tnzl/get_faster_qwen_36_27b/">[comments]</a></span>

</details>