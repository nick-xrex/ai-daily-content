---
id: inbox_5b25f7b3
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1251-reddit-localllama-qwen3-6-27b-with-mtp-grafted-on-unsloth-2e8c]]"
title: "Qwen3.6-27B with MTP grafted on Unsloth UD XL: 2.5x throughput via unmerged llama.cpp PR"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t5ageq/qwen3627b_with_mtp_grafted_on_unsloth_ud_xl_25x/
source: reddit-localllama
published_at: 2026-05-06T11:45:46+00:00
fetched_at: 2026-05-06T13:02:06.217211+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Qwen3.6-27B 基礎模型與 Unsloth UD XL 低位元寬度量化的組合方案，透過在頂層嫁接 Q8_0 MTP（Multi-Token Prediction）草稿層，實現 2.5x token 吞吐量提升。該方案將基礎模型保持在低位元寬度（如 IQ3_M、IQ4_XS），而 MTP 層採用 Q8_0 以保持投機解碼精度。作者分享了完整的 GGUF 文件、原始 MTP 層源碼及嫁接腳本，並提供了自訂 llama.cpp 的編譯指引（基於仍未合併的 PR #22673）。此方案為本地用戶帶來了易於部署的高效推理。"
key_points:
  - "Qwen3.6-27B + Unsloth UD XL 低位寬度量化 + Q8_0 MTP 層達 2.5x 加速"
  - "基礎模型低位元寬度 + MTP 層保持 Q8_0 精度，最小化額外 VRAM 開銷"
  - "提供可複用的嫁接腳本與完整編譯指引，支援 OpenAI/Anthropic API 相容端點"
tags: [qwen, unsloth, quantization, mtp, llama-cpp]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3.6-27B with MTP grafted on Unsloth UD XL: 2.5x throughput via unmerged llama.cpp PR

Qwen3.6-27B 基礎模型與 Unsloth UD XL 低位元寬度量化的組合方案，透過在頂層嫁接 Q8_0 MTP（Multi-Token Prediction）草稿層，實現 2.5x token 吞吐量提升。該方案將基礎模型保持在低位元寬度（如 IQ3_M、IQ4_XS），而 MTP 層採用 Q8_0 以保持投機解碼精度。作者分享了完整的 GGUF 文件、原始 MTP 層源碼及嫁接腳本，並提供了自訂 llama.cpp 的編譯指引（基於仍未合併的 PR #22673）。此方案為本地用戶帶來了易於部署的高效推理。

### 重點
- Qwen3.6-27B + Unsloth UD XL 低位寬度量化 + Q8_0 MTP 層達 2.5x 加速
- 基礎模型低位元寬度 + MTP 層保持 Q8_0 精度，最小化額外 VRAM 開銷
- 提供可複用的嫁接腳本與完整編譯指引，支援 OpenAI/Anthropic API 相容端點

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t5ageq/qwen3627b_with_mtp_grafted_on_unsloth_ud_xl_25x/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Hey everyone, I've been working on getting Multi-Token Prediction (MTP) working with quantized GGUFs for Qwen3-27B and the results are pretty impressive. Here's what I put together: <a href="https://huggingface.co/havenoammo/Qwen3.6-27B-MTP-UD-GGUF">https://huggingface.co/havenoammo/Qwen3.6-27B-MTP-UD-GGUF</a></p> <p>These are Unsloth's UD XL quantizations of Qwen3-27B with the MTP draft heads grafted on top in Q8_0. The base model stays in its usual low-bit quantization, while the 3 MTP layers stay at Q8 to preserve speculative accuracy.</p> <p>Sharing the grafted GGUF files (UD XL base + Q8 MTP), the raw MTP layer source I extracted (MTP_Q8_0.gguf), and <a href="https://huggingface.co/havenoammo/Qwen3.6-27B-MTP-UD-GGUF/blob/main/convert.py">convert.py</a>, the grafting script I adapted from <a href="https://gist.github.com/buzz/1c439684d5e3f36492ae9f64ef7e3f67">this gist</a> in case anyone wants to do this for other models. Also included are full build instructions for the custom llama.cpp.</p> <p>Qwen3 was trained with 3 MTP steps, meaning each forward pass predicts 4 tokens at once. llama.cpp's main branch doesn't support MTP yet, so I pulled in the speculative decoding support from the still-open <a href="https://github.com/ggml-org/llama.cpp/pull/22673">PR #22673</a>, merged it on top of master, and built llama-server from that. Run it with: <code>--spec-type mtp --spec-draft-n-max 3</code></p> <p>The results: roughly 2.5x token throughput compared to running the same UD XL GGUF without MTP, with a solid acceptance rate where most draft tokens are kept, meaning the MTP heads are genuinely useful and not just burning compute. The Q8 MTP layers also add very little VRAM overhead since they're a tiny fraction of the full model.</p> <p>MTP is one of the biggest efficiency wins available for speculative decoding, but it's basically unsupported outside of official Qwen3 deployments on SGLang and vLLM. This brings it to GGUF and llama.cpp, meaning you can run it locally with the same tooling you already use. PR #22673 will hopefully land soon and this will all just work out of the box. In the meantime, the merge process is straightforward (3 git commands).</p> <p>Happy to answer questions or help anyone get it running. Let me know if you try it and what speeds you see!</p> <p>Full step by step instructions are in the HuggingFace repo, but here's the short version:</p> <pre><code># 1. Build llama.cpp with MTP support git clone https://github.com/ggml-org/llama.cpp.git cd llama.cpp git fetch origin git fetch origin pull/22673/head:pr-22673 git checkout master git reset --hard origin/master git merge --no-ff pr-22673 -m &quot;Merge PR #22673: llama + spec: MTP Support&quot; cmake -B build -DGGML_CUDA=ON cmake --build build --config Release --target llama-server # 2. Grab the GGUF from HF # https://huggingface.co/havenoammo/Qwen3.6-27B-MTP-UD-GGUF # 3. Run with MTP ./build/bin/llama-server -m your-model.gguf --spec-type mtp --spec-draft-n-max 3 </code></pre> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/havenoammo"> /u/havenoammo </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5ageq/qwen3627b_with_mtp_grafted_on_unsloth_ud_xl_25x/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5ageq/qwen3627b_with_mtp_grafted_on_unsloth_ud_xl_25x/">[comments]</a></span>

</details>