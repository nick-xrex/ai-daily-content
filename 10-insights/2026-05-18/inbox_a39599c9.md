---
id: inbox_a39599c9
date: 2026-05-18
source_ref: "[[00-inbox/2026-05-18/0201-reddit-localllama-luce-dflash-pflash-on-7900xtx-qwen3-6-27-4541]]"
title: "Luce DFlash + PFlash on 7900XTX: Qwen3.6-27B at 2.24x decode and 3.05x prefill vs llama.cpp HIP"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tgepbd/luce_dflash_pflash_on_7900xtx_qwen3627b_at_224x/
source: reddit-localllama
published_at: 2026-05-18T06:57:45+00:00
fetched_at: 2026-05-19T02:09:43.217722+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "基於 Lucebox PR #119 的詳細測試報告，在 RX 7900 XTX 上運行 Qwen3.6-27B 達到 2.24 倍解碼加速和 2.29 倍鏈式推測加速。報告揭示核心設計原則：硬體頻寬特性決定最優參數選擇，如 GDDR6（高頻寬）最優 budget=8，而 LPDDR5X（低頻寬）最優 budget=22。提供完整復現步驟和環境配置指南，為 AMD GPU 用戶提供可執行方案。"
key_points:
  - "DFlash DDTree budget=8 在 RX 7900 XTX 達 62.75 tok/s，2.24 倍於 llama.cpp HIP 基線 28.07 tok/s"
  - "核心設計原則：硬體頻寬瓶頸決定預投機樹深度——GDDR6 高頻寬用 budget=8，LPDDR5X 低頻寬用 budget=22 以攤銷啟動開銷"
  - "提供完整復現指南含 ROCm 頭文件安裝、CMake 編譯、模型下載、基準對標腳本"
tags: [dflash-pflash, speculative-decoding, amd-rocm, qwen-inference, gpu-optimization]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Luce DFlash + PFlash on 7900XTX: Qwen3.6-27B at 2.24x decode and 3.05x prefill vs llama.cpp HIP

基於 Lucebox PR #119 的詳細測試報告，在 RX 7900 XTX 上運行 Qwen3.6-27B 達到 2.24 倍解碼加速和 2.29 倍鏈式推測加速。報告揭示核心設計原則：硬體頻寬特性決定最優參數選擇，如 GDDR6（高頻寬）最優 budget=8，而 LPDDR5X（低頻寬）最優 budget=22。提供完整復現步驟和環境配置指南，為 AMD GPU 用戶提供可執行方案。

### 重點
- DFlash DDTree budget=8 在 RX 7900 XTX 達 62.75 tok/s，2.24 倍於 llama.cpp HIP 基線 28.07 tok/s
- 核心設計原則：硬體頻寬瓶頸決定預投機樹深度——GDDR6 高頻寬用 budget=8，LPDDR5X 低頻寬用 budget=22 以攤銷啟動開銷
- 提供完整復現指南含 ROCm 頭文件安裝、CMake 編譯、模型下載、基準對標腳本

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tgepbd/luce_dflash_pflash_on_7900xtx_qwen3627b_at_224x/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tested a bit on my XTX, a bit share hope helpful, thanks to Lucebox! Lucebox DFlash + PFlash PR #119 Reproduction Report (RX 7900 XTX) Hardware Environment Component Spec GPU AMD Radeon RX 7900 XTX (Navi 31, gfx1100) VRAM 24 GiB GDDR6 (~936 GB/s) System RAM 62 GiB DDR5 ROCm 7.1 OS Ubuntu 26.04, Linux 7.0.0-14-generic Benchmark Results Model : Qwen3.6-27B Q4_K_M (15.65 GiB) + Lucebox Q8_0 DFlash drafter (1.84 GiB) Test : 10-prompt HumanEval-style, --n-gen 128 , --fast-rollback Baseline : llama.cpp HIP AR (tg128) — 28.07 tok/s Config Mean tok/s Mean AL Speedup (vs llama.cpp HIP) llama.cpp HIP AR 28.07 — 1.00x DFlash (chain speculation) 64.23 5.36 2.29x DFlash DDTree budget=8 62.75 4.93 2.24x DFlash DDTree budget=22 60.94 6.11 2.17x Key Findings Budget=8 is optimal on 7900 XTX (62.75 tok/s), consistent with the blog. GDDR6's high bandwidth favors smaller trees to avoid tile waste; Strix Halo's LPDDR5X needs budget=22 to amortize launch overhead. 2.24x speedup matches the blog's 2.23x on Strix Halo. The 7900 XTX absolute speed of 62.75 tok/s far exceeds 26.85 tok/s, thanks to its ~9x bandwidth advantage. Standard chain speculation (no DDTree) is slightly faster (64.23 tok/s), showing simpler strategies have lower overhead for short generations (128 tokens). Full Reproduction Steps 1. Clone repo and checkout PR #119 git clone https://github.com/Luce-Org/lucebox-hub.git cd lucebox-hub git fetch origin pull/119/head:pr119 &amp;&amp; git checkout pr119 git submodule update --init --recursive 2. Install rocWMMA headers (optional but recommended, enables Phase 2 FlashPrefill) If you don't have sudo to install the rocwmma package, fetch headers directly from GitHub: git clone --depth 1 https://github.com/ROCm/rocWMMA.git /tmp/rocwmma mkdir -p /tmp/rocm_include/include cp -r /tmp/rocwmma/library/include/rocwmma /tmp/rocm_include/include/rocwmma 3. Build (gfx1100 / 7900 XTX) cd dflash cmake -B build -S . \ -DCMAKE_BUILD_TYPE=Release \ -DDFLASH27B_GPU_BACKEND=hip \ -DDFLASH27B_HIP_ARCHITECTURES=gfx1100 \ -DDFLASH27B_HIP_SM80_EQUIV=ON \ -DROCM_PATH=/tmp/rocm_include # path from step 2; omit if rocwmma is system-installed cmake --build build --target test_dflash -j$(nproc) Replace gfx1100 with your GPU arch, e.g. gfx1151 (Strix Halo), gfx1030 (Navi 21), etc. To skip rocWMMA, set -DDFLASH27B_HIP_SM80_EQUIV=OFF to use the q8 fallback. 4. Download models mkdir -p models/draft wget -c -O models/Qwen3.6-27B-Q4_K_M.gguf \ &quot;https://huggingface.co/unsloth/Qwen3.6-27B-GGUF/resolve/main/Qwen3.6-27B-Q4_K_M.gguf&quot; wget -c -O models/draft/dflash-draft-3.6-q8_0.gguf \ &quot;https://huggingface.co/Lucebox/Qwen3.6-27B-DFlash-GGUF/resolve/main/dflash-draft-3.6-q8_0.gguf&quot; 5. Install Python dependencies (for bench script) pip3 install --break-system-packages transformers torch 6. Run the benchmark # DFlash DDTree budget=8 (recommended for gfx1100) cd dflash LD_LIBRARY_PATH=/opt/rocm/lib:$LD_LIBRARY_PATH \ DFLASH_BIN=$PWD/build/test_dflash \ DFLASH_TARGET=$PWD/models/Qwen3.6-27B-Q4_K_M.gguf \ DFLASH_DRAFT=$PWD/models/draft/dflash-draft-3.6-q8_0.gguf \ DFLASH27B_DRAFT_SWA=2048 \ DFLASH27B_PREFILL_UBATCH=512 \ python3 scripts/bench_he.py --n-gen 128 --ddtree-budget 8 Environment variables Variable Meaning DFLASH_BIN Path to test_dflash binary DFLASH_TARGET Path to target model GGUF DFLASH_DRAFT Path to draft model GGUF DFLASH27B_DRAFT_SWA Draft sliding window attention window for Qwen3.6 (2048) DFLASH27B_PREFILL_UBATCH Compressed prefill micro-batch size (512, applies PR #159) bench_he.py common arguments Argument Description --n-gen N Tokens to generate per prompt (default 128) --ddtree-budget N DDTree node budget (8/22/32/48/64/96/128) --ddtree-temp T Draft logits temperature (T&lt;1 widens top-1/top-2 gap) --max-ctx N Maximum context length --target-tokenizer REPO Target model tokenizer (default Qwen/Qwen3.5-27B) --target-split-dflash Use target layer-split mode (shows prefill timing) --skip-tokenize Skip tokenization step (reuse cache) 7. Build and run llama.cpp baseline for comparison # Build separately from dflash/deps/llama.cpp BUILD_DIR=/tmp/llama-bench-build cmake -B $BUILD_DIR -S dflash/deps/llama.cpp \ -DCMAKE_BUILD_TYPE=Release \ -DGGML_HIP=ON \ -DLLAMA_BUILD_TOOLS=ON cmake --build $BUILD_DIR --target llama-bench -j$(nproc) # Run baseline LD_LIBRARY_PATH=/opt/rocm/lib:$LD_LIBRARY_PATH \ $BUILD_DIR/bin/llama-bench \ -m models/Qwen3.6-27B-Q4_K_M.gguf \ -n 128 -p 128 -o md Comparison with Blog Data Metric Strix Halo (gfx1151) Blog 7900 XTX (gfx1100) This Run llama.cpp HIP AR 12.02 tok/s 28.07 tok/s DFlash (optimal budget) 26.85 tok/s (budget=22) 62.75 tok/s (budget=8) Speedup 2.23x 2.24x Optimal budget 22 (LPDDR5X bandwidth bottleneck) 8 (GDDR6 high bandwidth) Blog: https://www.lucebox.com/blog/amd Notes BSA scoring kernel is not implemented on HIP — it falls back to ggml flash_attn_ext (~3.4x slower than CUDA BSA). This is the remaining PFlash optimization headroom. PR #159 ubatch=512 is applied via the DFLASH27B_PREFILL_UBATCH=512 env variable (manually layered on top of PR #119). VRAM limitation : The 7900 XTX's 24 GiB is insufficient for a full 16K context PFlash test. 16K KV cache + model weights (~16 GiB + ~6 GiB KV cache) exceeds 24 GiB. Strix Halo's 128 GiB unified memory is needed for large context + large model workloads. &#32; submitted by &#32; /u/Fit-Courage5400 [link] &#32; [comments]

</details>