---
id: inbox_4a0e3cb6
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-localllama-i-built-a-transformer-in-c-17-from-scrat-9d33]]"
title: "I built a transformer in C++17 from scratch — no PyTorch, no BLAS, no dependencies. Trains on CPU. 0.83M params, full analytical backprop, 76 min to val loss 1.64."
url: https://www.reddit.com/r/LocalLLaMA/comments/1t1x9jv/i_built_a_transformer_in_c17_from_scratch_no/
source: reddit-localllama
published_at: 2026-05-02T18:11:34+00:00
fetched_at: 2026-05-03T01:59:12.936686+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者從零實現 Quadtrix.cpp：純 C++17 完整 GPT 式語言模型，僅依賴標準庫與 POSIX sockets，零外部依賴。模型規格：4 層 × 4 頭 × 200d 解碼器，826K 參數，128 字元 context，31.4M 字元訓練語料（童話故事），最佳驗證 loss 1.637，單 CPU 核心訓練 76.2 分鐘。手寫張量庫、完整前向與後向傳播（梯度推導耗時約一週），OpenMP 並行化達 5-7 倍加速（8 核），GPU 版本（LibTorch + RTX 3080）快 75 倍。"
key_points:
  - "0.83M 參數模型，76 分鐘 CPU 訓練達 val loss 1.637；展示小規模 transformer CPU 訓練可行性"
  - "手推所有梯度（尤其 LayerNorm 3 項公式、causal attention 反傳、dropout mask 追蹤）；關鍵：前向保存 mu/inverse-std/x-hat 才能正確反傳"
  - "零依賴實現對比 GPU 自動微分：自寫 600 行 backward.h vs PyTorch autograd 削除梯度代碼，凸顯依賴帶來的便利與運行效率權衡"
tags: [c++17, transformer-from-scratch, analytical-backprop, cpu-training, zero-dependencies]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## I built a transformer in C++17 from scratch — no PyTorch, no BLAS, no dependencies. Trains on CPU. 0.83M params, full analytical backprop, 76 min to val loss 1.64.

開發者從零實現 Quadtrix.cpp：純 C++17 完整 GPT 式語言模型，僅依賴標準庫與 POSIX sockets，零外部依賴。模型規格：4 層 × 4 頭 × 200d 解碼器，826K 參數，128 字元 context，31.4M 字元訓練語料（童話故事），最佳驗證 loss 1.637，單 CPU 核心訓練 76.2 分鐘。手寫張量庫、完整前向與後向傳播（梯度推導耗時約一週），OpenMP 並行化達 5-7 倍加速（8 核），GPU 版本（LibTorch + RTX 3080）快 75 倍。

### 重點
- 0.83M 參數模型，76 分鐘 CPU 訓練達 val loss 1.637；展示小規模 transformer CPU 訓練可行性
- 手推所有梯度（尤其 LayerNorm 3 項公式、causal attention 反傳、dropout mask 追蹤）；關鍵：前向保存 mu/inverse-std/x-hat 才能正確反傳
- 零依賴實現對比 GPU 自動微分：自寫 600 行 backward.h vs PyTorch autograd 削除梯度代碼，凸顯依賴帶來的便利與運行效率權衡

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t1x9jv/i_built_a_transformer_in_c17_from_scratch_no/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>For the past few months I've been working on Quadtrix.cpp — a complete GPT-style language model implemented in C++17. No PyTorch. No LibTorch. No BLAS. No auto-differentiation library of any kind. The only dependency is the C++17 standard library and POSIX sockets.</p> <p>Repo: <a href="https://github.com/Eamon2009/Quadtrix.cpp">https://github.com/Eamon2009/Quadtrix.cpp</a></p> <p>Everything is hand-written: the tensor library, all forward pass operations, and the full analytical backward pass with explicit gradient derivations for every operator.</p> <p><strong>Training run v1.0</strong></p> <ul> <li>Architecture: 4 layers x 4 heads x 200d decoder-only transformer</li> <li>Parameters: 826,985 (0.83 M)</li> <li>Context window: 128 characters</li> <li>Corpus: 31.4 M characters of children's stories</li> <li>Best val loss: 1.6371 nats</li> <li>Training time: 76.2 minutes on a single CPU core</li> <li>External dependencies: zero</li> </ul> <p><strong>What is actually implemented</strong></p> <ul> <li>Lightweight CPU float tensor library (2D/3D, row-major storage)</li> <li>Token and position embeddings, LayerNorm, Linear, Dropout</li> <li>Multi-head causal self-attention with causal mask</li> <li>Feed-forward blocks: Linear -&gt; ReLU -&gt; Linear</li> <li>Complete backward pass: cross-entropy, softmax, layer normalisation (Ba et al. 3-term formula), scaled dot-product attention, Q/K/V gradients, ReLU, dropout, embedding scatter-add</li> <li>AdamW optimiser with bias correction</li> <li>Character-level tokeniser and batch sampler</li> <li>OpenMP parallelisation across all CPU cores — matmul, bmm, softmax, and layernorm all parallelised. Around 5-7x speedup on an 8-core machine</li> </ul> <p><strong>The gradient derivations alone took about a week.</strong></p> <p>The layernorm backward is the part that trips everyone up. You need to save mu, inverse-std, and x-hat per row during the forward pass and apply the full 3-term formula in the backward. The attention backward requires careful tracking of which dropout mask was applied to the attention weights versus the projection output.</p> <p><strong>Sample output after training</strong></p> <p>```</p> <p>You &gt; Once upon a time</p> <p>Quadtrix &gt; , and said askiced and so owas said sri. The his brickerys and stew hhat and saw and stark a din't. She stingry and asked day. Timmy watch and played to cones.</p> <p>You &gt; Timmy is a</p> <p>Quadtrix &gt; bog the scated justo prove the bret you. Timmy nevery some the gecid. Her neplay to bet starked a way, that litked cliend.</p> <p>You &gt; what is life</p> <p>Quadtrix &gt; st happe. It happ a liked back abp happy thing flongs way. Lily lood take maked a fiside apie? Tom and abed Timm.</p> <p>```</p> <p>Yes it is gibberish. It is a 0.83M parameter model trained for 76 minutes on a CPU. But it is my gibberish, produced by gradients I derived and implemented myself, running in a binary that links to absolutely nothing outside the standard library.</p> <p>The LibTorch GPU port is also done as a separate branch. Same architecture, same hyperparameters, same training loop. The only difference is model-&gt;to(torch::CUDA) and the entire 600-line backward.h gets deleted because autograd handles it. Roughly 75x faster on an RTX 3080.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Suspicious_Gap1121"> /u/Suspicious_Gap1121 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1x9jv/i_built_a_transformer_in_c17_from_scratch_no/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1x9jv/i_built_a_transformer_in_c17_from_scratch_no/">[comments]</a></span>

</details>