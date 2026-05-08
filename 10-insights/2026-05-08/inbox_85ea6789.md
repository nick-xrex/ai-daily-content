---
id: inbox_85ea6789
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0737-reddit-localllama-benchmark-qwen-3-6-27b-mtp-on-2x3090-nvl-2e84]]"
title: "Benchmark Qwen 3.6 27B MTP on 2x3090 NVLINK"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t6susj/benchmark_qwen_36_27b_mtp_on_2x3090_nvlink/
source: reddit-localllama
published_at: 2026-05-08T00:49:03+00:00
fetched_at: 2026-05-08T08:07:35.921212+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者對 Qwen 3.6 27B 模型在 4× RTX 3090（含 NVLink）上的 MTP 推論進行了詳細基準測試，揭示硬體拓撲對分散式推論 (Tensor Parallel) 效能的決定性影響。將 TP=2 固定在 NVLinked GPU 對比拆散在 PCIe 上，單一並行時吞吐量 +25%、四並行時 +53%；但若擴展為 TP=4 用足四顆 GPU，反而比 TP=2-NVLink 慢 13-30%，因為 TP=N 的效能受限於拓撲中最慢的互聯。MTP speculative decoding 在各拓撲配置下都穩定運作（70-79% 接受率），瓶頸不在 drafter 品質而在全約減通訊。"
key_points:
  - "NVLink 在 TP=2 配置下帶來 +25% (並行 1) 到 +53% (並行 4) 的吞吐量增益；TTFT 更在並行 4 時近乎減半（994→551ms）"
  - "TP=N 效能 = 拓撲最慢連線的效能：TP=4 跨 4 顆 GPU 時多數連線為 PCIe，導致全約減通訊成瓶頸，比 TP=2-NVLink 慢 13-30%"
  - "最適配置是在雙 NVLink 對 3090 機箱上運行兩組 TP=2 服務（分別在 GPU 0+2 與 1+3），而非單一 TP=4"
tags: [nvlink, tensor-parallel, gpu-topology, qwen, vllm]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Benchmark Qwen 3.6 27B MTP on 2x3090 NVLINK

作者對 Qwen 3.6 27B 模型在 4× RTX 3090（含 NVLink）上的 MTP 推論進行了詳細基準測試，揭示硬體拓撲對分散式推論 (Tensor Parallel) 效能的決定性影響。將 TP=2 固定在 NVLinked GPU 對比拆散在 PCIe 上，單一並行時吞吐量 +25%、四並行時 +53%；但若擴展為 TP=4 用足四顆 GPU，反而比 TP=2-NVLink 慢 13-30%，因為 TP=N 的效能受限於拓撲中最慢的互聯。MTP speculative decoding 在各拓撲配置下都穩定運作（70-79% 接受率），瓶頸不在 drafter 品質而在全約減通訊。

### 重點
- NVLink 在 TP=2 配置下帶來 +25% (並行 1) 到 +53% (並行 4) 的吞吐量增益；TTFT 更在並行 4 時近乎減半（994→551ms）
- TP=N 效能 = 拓撲最慢連線的效能：TP=4 跨 4 顆 GPU 時多數連線為 PCIe，導致全約減通訊成瓶頸，比 TP=2-NVLink 慢 13-30%
- 最適配置是在雙 NVLink 對 3090 機箱上運行兩組 TP=2 服務（分別在 GPU 0+2 與 1+3），而非單一 TP=4

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t6susj/benchmark_qwen_36_27b_mtp_on_2x3090_nvlink/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

TL;DR On 4× RTX 3090 with NVLink bonded between GPU pairs (0↔2 and 1↔3), pinning TP=2 to a NVLinked pair gave +25% throughput at concurrency 1 and +53% at concurrency 4 vs running TP=2 over PCIe. Adding the other two GPUs to make it TP=4 made things worse, not better. Setup Hardware: 4× RTX 3090 (24 GB), NVLink (NV4) between GPU0↔GPU2 and GPU1↔GPU3. Cross-pair traffic goes via PCIe Host Bridge (PHB). Bash $ nvidia-smi topo -m GPU0 GPU1 GPU2 GPU3 GPU0 X PHB NV4 PHB GPU1 PHB X PHB NV4 GPU2 NV4 PHB X PHB GPU3 PHB NV4 PHB X Software: vLLM 0.20.1, transformers 5.7.0, CUDA 12.8. Model: cyankiwi/Qwen3.6-27B-AWQ-BF16-INT4 — 27B-param dense hybrid (linear-attention + full-attention + mamba SSM), with an MTP head for speculative decoding. Workload: vllm bench serve with random dataset, 1024 input / 256 output tokens, --ignore-eos , --seed 42 . Two runs per config: concurrency 1 (8 prompts) and concurrency 4 (32 prompts). vLLM serve command Identical for every config except CUDA_VISIBLE_DEVICES and --tensor-parallel-size : Bash CUDA_VISIBLE_DEVICES=&lt;see below&gt; \ vllm serve cyankiwi/Qwen3.6-27B-AWQ-BF16-INT4 \ --served-model-name Qwen3.6-27B-AWQ-BF16-INT4 \ --host 0.0.0.0 --port 8000 \ --tensor-parallel-size &lt;2 or 4&gt; \ --max-model-len 131072 \ --gpu-memory-utilization 0.85 \ --max-num-seqs 8 \ --dtype float16 \ --attention-backend FLASHINFER \ --enable-prefix-caching \ --mamba-cache-dtype auto \ --mamba-cache-mode align \ --enable-chunked-prefill \ --max-num-batched-tokens 4096 \ --reasoning-parser qwen3 \ --default-chat-template-kwargs '{&quot;enable_thinking&quot;: true, &quot;preserve_thinking&quot;: true}' \ --enable-auto-tool-choice \ --tool-call-parser qwen3_xml \ --speculative-config '{&quot;method&quot;:&quot;qwen3_next_mtp&quot;,&quot;num_speculative_tokens&quot;:2}' \ --trust-remote-code The three configs: Config CUDA_VISIBLE_DEVICES TP Topology A — TP=2 NVLink 0,2 2 NVLinked pair (NV4) B — TP=2 non-NVLink 0,1 2 Cross-pair, PCIe (PHB) C — TP=4 all GPUs 0,1,2,3 4 Mixed (2 NVLink edges + 4 PCIe edges) Benchmarks Concurrency 1 (single-stream) Config Output tok/s TTFT med TPOT med ITL med Spec accept rate Spec accept len A — TP=2 NVLink (0+2) 66.0 509 ms 13.4 ms 32.1 ms 73.7 % 2.47 B — TP=2 non-NVLink (0+1) 52.6 861 ms 15.7 ms 37.6 ms 70.4 % 2.41 C — TP=4 all GPUs 57.4 664 ms 14.7 ms 37.8 ms 79.2 % 2.58 Concurrency 4 (4 in-flight requests) Config Output tok/s TTFT med TPOT med ITL med Spec accept rate A — TP=2 NVLink (0+2) 181.9 551 ms 19.0 ms 34.3 ms 74.6 % B — TP=2 non-NVLink (0+1) 119.2 994 ms 27.1 ms 45.3 ms 75.0 % C — TP=4 all GPUs 127.9 751 ms 24.5 ms 43.6 ms 75.6 % What NVLink actually buys you Comparing A vs B (same model, same TP=2, only the interconnect changes): Metric TP=2 NVLink (0+2) TP=2 non-NVLink (0+1) NVLink advantage Output tok/s, conc=1 66.0 52.6 +25.4 % Output tok/s, conc=4 181.9 119.2 +52.6 % TTFT median, conc=4 551 ms 994 ms -45 % (lower is better) TPOT median, conc=4 19.0 ms 27.1 ms -30 % A few things stand out: The premium is much bigger at higher concurrency (+53% at conc=4 vs +25% at conc=1). Per-step all-reduce traffic scales with batch size; NVLink's bandwidth advantage compounds. TTFT nearly halves with NVLink (994 → 551 ms at conc=4). Prefill is comms-heavy because it ships large activation matrices between TP ranks. The MTP speculative decoding still works fine over PCIe (acceptance rate barely shifted, 73 → 70%), so the gap is purely interconnect, not draft quality. Bonus: what about all 4 GPUs? The natural follow-up was: if NVLink is so good, what if I use all four GPUs (TP=4)? The two NVLink edges still help, and now I'm sharding weights across four devices instead of two — surely faster? Nope. TP=4 was slower than TP=2-NVLinked across the board. Metric TP=2 NVLink TP=4 all GPUs Δ Output tok/s, conc=1 66.0 57.4 -13.0 % Output tok/s, conc=4 181.9 127.9 -29.7 % TPOT median, conc=4 19.0 ms 24.5 ms +29 % TTFT median, conc=4 551 ms 751 ms +36 % Why: TP=4 needs every GPU pair to participate in the all-reduce ring. With 4 GPUs there are 6 unique pairs; on this topology only 2 of those (0↔2, 1↔3) are NVLinked — the other 4 are PCIe. So you're doing 4-way all-reduces where most of the edges are slow, and the savings from sharding weights into smaller chunks don't make up for it. Adding the second pair of GPUs hurts more than it helps unless every-pair-to-every-pair has a fast link. In single-stream theory, TP=4 should give a ~1.5–1.8× speedup from per-GPU bandwidth pressure dropping. Reality: -13%. Topology beats theoretical bandwidth math. Takeaways NVLink is worth ~25% at conc=1 and ~50%+ at higher batch sizes for TP=2 serving on 3090s. Always pin TP=2 to the NVLinked pair. TP=N is only as good as the worst link in your topology. Adding the other two GPUs (TP=4) on a &quot;two-NVLinked-pair&quot; 3090 chassis loses ~30% throughput vs TP=2-NVLinked. Don't reach for TP=4 just because you have 4 GPUs. MTP speculative decoding survived all topologies — acceptance rate stayed in the 70–79% range with length 2.4–2.6. The bottleneck wasn't the draft model, it was the all-reduce. For two-pair NVLink 3090 boxes, the optimal serving pattern is probably two TP=2 services , one on each NVLinked pair (e.g. one model on 0+2, another on 1+3) rather than one TP=4. Or run a single TP=2 and let the other pair host a different model entirely. If anyone has a 4-way NVSwitch box (e.g. SXM 3090s, A100s, or H100s) and can run the same TP=4 vs TP=2 comparison there, I'd be very curious whether TP=4 wins back its theoretical advantage when all pairs are NVLinked. &#32; submitted by &#32; /u/Mr_Moonsilver [link] &#32; [comments]

</details>