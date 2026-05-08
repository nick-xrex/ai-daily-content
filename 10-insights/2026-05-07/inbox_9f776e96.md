---
id: inbox_9f776e96
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-localllama-running-qwen3-5-qwen3-6-with-nextn-mtp-m-43bb]]"
title: "Running Qwen3.5 / Qwen3.6 with NextN MTP (Multi-Token Prediction) speculative decode in llama.cpp — single RTX 3090 Ti GPU guide"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t65vl8/running_qwen35_qwen36_with_nextn_mtp_multitoken/
source: reddit-localllama
published_at: 2026-05-07T09:56:06+00:00
fetched_at: 2026-05-08T08:05:33.116337+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 用戶分享了 Qwen3.5/3.6 在 llama.cpp 中使用 NextN MTP (多語元預測) 投機解碼的完整指南。NextN MTP 相比原生版本提升約 2.9 倍解碼速度，35B-A3B MoE 模型在單塊 RTX 3090 Ti GPU 上可達約 150 tok/s，無品質損失。指南涵蓋了兩個必要的上游 PR 的 cherry-pick、CUDA 構建步驟、正確的量化方法（使用 --tensor-type nextn=q8_0 避免 Q4 量化損失）、以及功率調優（350W + 1700MHz 鎖定以達到最佳 tok/W）。提供了具體的性能基準數據（4B 達 181 tok/s、27B 達 47 tok/s），並詳列了常見問題排除步驟。"
key_points:
  - "NextN MTP 相比原生 llama.cpp 提升 2.9 倍解碼速度；35B-A3B-MTP 在 3090 Ti 上達 150–157 tok/s"
  - "量化時必須使用 --tensor-type nextn=q8_0 保留 nextn block 的 Q8 精度，否則無速度提升"
  - "功率調優 (350W + 1700MHz) 提升約 17% tps；KV cache 從 f16 降為 q8 節省 50% VRAM 無品質損失"
tags: [llama-cpp, speculative-decode, qwen3, mtp, gpu-optimization]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Running Qwen3.5 / Qwen3.6 with NextN MTP (Multi-Token Prediction) speculative decode in llama.cpp — single RTX 3090 Ti GPU guide

Reddit 用戶分享了 Qwen3.5/3.6 在 llama.cpp 中使用 NextN MTP (多語元預測) 投機解碼的完整指南。NextN MTP 相比原生版本提升約 2.9 倍解碼速度，35B-A3B MoE 模型在單塊 RTX 3090 Ti GPU 上可達約 150 tok/s，無品質損失。指南涵蓋了兩個必要的上游 PR 的 cherry-pick、CUDA 構建步驟、正確的量化方法（使用 --tensor-type nextn=q8_0 避免 Q4 量化損失）、以及功率調優（350W + 1700MHz 鎖定以達到最佳 tok/W）。提供了具體的性能基準數據（4B 達 181 tok/s、27B 達 47 tok/s），並詳列了常見問題排除步驟。

### 重點
- NextN MTP 相比原生 llama.cpp 提升 2.9 倍解碼速度；35B-A3B-MTP 在 3090 Ti 上達 150–157 tok/s
- 量化時必須使用 --tensor-type nextn=q8_0 保留 nextn block 的 Q8 精度，否則無速度提升
- 功率調優 (350W + 1700MHz) 提升約 17% tps；KV cache 從 f16 降為 q8 節省 50% VRAM 無品質損失

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t65vl8/running_qwen35_qwen36_with_nextn_mtp_multitoken/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I was asked for this guide, so here it is. Some overlap with someone else’s post from yesterday. YMMV! Too busy with work to write myself, so I asked Opus to write for me (I have validated the content!). I’m sure there will be debate over using q4 blah blah. I’m happy with how it works with my models. I am happy to create higher q models as far as my hardware allows, if asked! NextN MTP gives ~2.9× decode on the Qwen3.5/3.6 family vs vanilla, zero quality loss (head ships with the model). Heavy MoE arch like 35B-A3B hits ~150 tok/s on a 3090 Ti. Catch: it's not merged upstream as of this writing — you need to pull the open PRs. Required PRs (cherry-pick or build off the branch they live on) Both open as of May 2026 — track + rebuild when they ship: #22400 — llama: allow partial seq_rm for GDN models for speculative decoding https://github.com/ggml-org/llama.cpp/pull/22400 Prerequisite. Adds keep_intermediates path for GDN/SSM models so spec-decode can rollback partial draft. Without this, MTP doesn't function on hybrid-attn models (27B). #22673 — llama + spec: MTP Support https://github.com/ggml-org/llama.cpp/pull/22673 The main course. Adds qwen35_mtp + qwen35moe_mtp arch loaders, NextN graph forward, --spec-type mtp flag, and the speculative state machine. Either rebase both onto current upstream master, or pull am17an's branches directly. My fork (FYI — has both PRs merged + extras) https://github.com/nickstx/llama.cpp branch crucible Has #22400 + #22673 plus a qwen3moe_mtp arch (Qwen3-Coder base — work-in-progress for coder-30B MTP head training, not needed for Qwen3.5/3.6 release models). For ready-to-build, this is the simplest pull. Also includes some unmerged slot PRs, that added support for cross-PID slot resumes. Build (CUDA) bash git clone https://github.com/nickstx/llama.cpp.git cd llama.cpp git checkout crucible cmake -B build -DGGML_CUDA=on -DCMAKE_BUILD_TYPE=Release cmake --build build -j$(nproc) --target llama-server Get a working GGUF You want the Q8nextn variants — these have the NextN block override applied (most public quants either strip nextn or quantize it to Q4 →s less ancceptance). Model Tier Repo Qwen3.5-4B-MTP Q5_K_M / IMAT-IQ4_XS / IMAT-Q4_K_M localweights/Qwen3.5-4B-MTP-* Qwen3.6-27B-MTP IQ4_XS-Q8nextn / IMAT-IQ4_XS-Q8nextn localweights/Qwen3.6-27B-MTP-* Qwen3.6-35B-A3B-MTP IMAT-IQ4_XS-Q8nextn / IMAT-Q4_K_M-Q8nextn localweights/Qwen3.6-35B-A3B-MTP-* Collection: https://hf.co/collections/localweights/qwen36-mtp-crucible-release-69fbdeadca3472e779dff9d2 Or roll your own from a bf16 source: ```bash Optional: imatrix calibration (5-8% PPL gain) ./build/bin/llama-imatrix -m model-bf16.gguf -f calibration.txt -ngl 999 \ --chunks 200 -o imatrix.dat Quantize WITH nextn override (this is the part everyone misses) ./build/bin/llama-quantize \ --imatrix imatrix.dat \ --tensor-type nextn=q8_0 \ model-bf16.gguf model-IMAT-IQ4_XS-Q8nextn.gguf IQ4_XS ``` --tensor-type nextn=q8_0 overrides quant for any tensor matching nextn . Without it: //////// output. Run bash ./build/bin/llama-server \ -m Qwen3.6-35B-A3B-MTP-IMAT-Q4_K_M-Q8nextn.gguf \ --port 8080 -ngl 999 -fa on --parallel 1 \ --ctx-size 131072 -ctk q8_0 -ctv q8_0 \ --kv-unified \ --spec-type mtp --spec-draft-n-max 4 \ --metrics --jinja Key flags: - --spec-type mtp — enables NextN draft path (this is the new flag from #22673) - --spec-draft-n-max 4 — propose 4 tokens/step. Bump to 6 for chat (longer ctx, predictable). Drop to 2 for code. Default 4 fine. - -ctk q8_0 -ctv q8_0 — KV at q8 saves ~half VRAM, no quality cost on this family. - --kv-unified — required for spec-decode. Speed (3090 Ti, 350W/1700MHz, q8 KV, ~50-tok prompt → 1600-tok decode) Model tps 4B-MTP IMAT-IQ4_XS 181 4B-MTP IMAT-Q4_K_M 168 35B-A3B-MTP IMAT-Q4_K_M-Q8nextn 157 35B-A3B-MTP IMAT-IQ4_XS-Q8nextn 149 27B-MTP IMAT-IQ4_XS-Q8nextn 47 35B-A3B beats 27B 3× (A3B = 3B active params, MoE wins). 27B is dense+SSM hybrid → slow link. Power tuning (3090 Ti) For sustained MTP workloads, 350W + 1700MHz lock is the tok/W sweet spot: bash sudo nvidia-smi -pl 350 sudo nvidia-smi -lgc 0,1700 300W default makes the clock collapse to ~1080MHz under MTP draft passes — costs ~17% tps. Don't drop below 280W. Persist via systemd if you want it across reboots. Gotchas ** //// output** = nextn block was Q4-quantized. Re-quant with --tensor-type nextn=q8_0 . No speedup = --spec-type mtp not on, or model has no nextn tensors. Verify: llama-gguf model.gguf r | grep nextn . OOM long ctx = drop KV f16→q8, shrink ctx, partial offload. 27B bf16 dump has inf at blk.18.ffn_up . IQ4 kernels handle it; Q4_K_M validation aborts. Use IQ4_XS for 27B if Q4 fails. Spec draft accept rate : check /metrics endpoint — spec_decode_*_total . Code: ~50-65%. Chat: 70%+. Credits am17an / Aman Gupta for both upstream PRs Qwen team for shipping NextN-trained heads ggml-org for the runtime &#32; submitted by &#32; /u/yes_i_tried_google [link] &#32; [comments]

</details>