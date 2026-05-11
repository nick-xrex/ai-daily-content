---
id: inbox_ca7f7849
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_ca7f7849]]"
title: "NCCL-Free Tensor Parallelism on Dual Blackwell PCIe llama.cpp b9095 released!"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t96l6r/ncclfree_tensor_parallelism_on_dual_blackwell/
source: reddit-localllama
published_at: 2026-05-10T13:12:33+00:00
fetched_at: 2026-05-11T02:22:04.457833+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llama.cpp 發佈 b9095 版本，首次實現無 NCCL 張量並列在雙 Blackwell PCIe GPU 上的運行。此前，消費級 Blackwell GPU（如 RTX 5060 Ti）雙卡配置無法使用 -sm 張量並列參數，新版本解決了此限制，使 NCCL 依賴不再是必要條件。"
key_points:
  - "llama.cpp b9095 支援 -sm 無 NCCL 張量並列，首次在雙 Blackwell PCIe GPU 上運行"
  - "移除了消費級 GPU（如 RTX 5060 Ti）配置的 NCCL 依賴限制"
tags: [llama-cpp, tensor-parallelism, blackwell-gpu, nccl-free]
topics: []
importance: 3
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## NCCL-Free Tensor Parallelism on Dual Blackwell PCIe llama.cpp b9095 released!

llama.cpp 發佈 b9095 版本，首次實現無 NCCL 張量並列在雙 Blackwell PCIe GPU 上的運行。此前，消費級 Blackwell GPU（如 RTX 5060 Ti）雙卡配置無法使用 -sm 張量並列參數，新版本解決了此限制，使 NCCL 依賴不再是必要條件。

### 重點
- llama.cpp b9095 支援 -sm 無 NCCL 張量並列，首次在雙 Blackwell PCIe GPU 上運行
- 移除了消費級 GPU（如 RTX 5060 Ti）配置的 NCCL 依賴限制

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t96l6r/ncclfree_tensor_parallelism_on_dual_blackwell/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# NCCL-Free Tensor Parallelism on Dual Blackwell PCIe llama.cpp b9095 released!

b9095 finally makes -sm tensor work on dual consumer Blackwell PCIe GPUs without NCCL If youre on dual Blackwell gpus this look like it could be big. I'll have my own results for 2x5060ti asap &#32; submitted by &#32; /u/Bulky-Priority6824 [link] &#32; [comments]

</details>