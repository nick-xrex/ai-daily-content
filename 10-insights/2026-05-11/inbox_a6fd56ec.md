---
id: inbox_a6fd56ec
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/0113-reddit-localllama-computer-build-using-intel-optane-persis-b31c]]"
title: "Computer build using Intel Optane Persistent Memory - Can run 1 trillion parameter model at over 4 tokens/sec"
url: https://www.reddit.com/r/LocalLLaMA/comments/1taeg8h/computer_build_using_intel_optane_persistent/
source: reddit-localllama
published_at: 2026-05-11T19:54:25+00:00
fetched_at: 2026-05-12T01:21:05.062761+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者成功構建專用推理系統，採用 768GB Intel Optane Persistent Memory，在 ~4 tokens/sec 速度運行 1 兆參數模型（Kimi K2.5 Unsloth Q2_K_XL 量化版）。系統採用混合 GPU/CPU 推理，llama.cpp 自動分配 attention weights 和 shared experts 駐 12GB RTX 3060，sparse experts 駐 PMem/DRAM。Optane 已停產但二手價遠低於等量 DRAM，驗證了記憶體層級化在大模型推理中的可行性。```mermaid
graph TB
  A[\"1T Param Model<br/>Kimi K2.5 Q2_K_XL\"] --> B{\"張量分配\"}
  B -->|\"Attention + Dense<br/>+ Shared Expert\"| C[\"RTX 3060<br/>12GB VRAM\"]
  B -->|\"Sparse Experts\"| D[\"Intel Optane PMem<br/>768GB<br/>+ DDR4 DRAM\"]
  D -->|\"Memory Mode<br/>PMem as Swap\"| E[\"Result: ~4 tok/sec\"]
  C --> E
```"
key_points:
  - "1 兆參數模型在 RTX 3060 12GB + 768GB Optane PMem 上達 ~4 tokens/sec，MoE 架構理想契合層級化記憶體"
  - "Intel Optane PMem 在 Memory Mode 下充當 DRAM 緩存層，成本遠低於等量 DRAM；二手市場價格具競爭力"
  - "llama.cpp override-tensor 和 cmoe 自動調度，sparse MoE 將 bulk 權重駐放 PMem，規避 GPU 顯存溢出"
tags: [optane-pmem, trillion-param-inference, kimi-k2.5, memory-tiering, llama-cpp]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Computer build using Intel Optane Persistent Memory - Can run 1 trillion parameter model at over 4 tokens/sec

開發者成功構建專用推理系統，採用 768GB Intel Optane Persistent Memory，在 ~4 tokens/sec 速度運行 1 兆參數模型（Kimi K2.5 Unsloth Q2_K_XL 量化版）。系統採用混合 GPU/CPU 推理，llama.cpp 自動分配 attention weights 和 shared experts 駐 12GB RTX 3060，sparse experts 駐 PMem/DRAM。Optane 已停產但二手價遠低於等量 DRAM，驗證了記憶體層級化在大模型推理中的可行性。```mermaid
graph TB
  A["1T Param Model<br/>Kimi K2.5 Q2_K_XL"] --> B{"張量分配"}
  B -->|"Attention + Dense<br/>+ Shared Expert"| C["RTX 3060<br/>12GB VRAM"]
  B -->|"Sparse Experts"| D["Intel Optane PMem<br/>768GB<br/>+ DDR4 DRAM"]
  D -->|"Memory Mode<br/>PMem as Swap"| E["Result: ~4 tok/sec"]
  C --> E
```

### 重點
- 1 兆參數模型在 RTX 3060 12GB + 768GB Optane PMem 上達 ~4 tokens/sec，MoE 架構理想契合層級化記憶體
- Intel Optane PMem 在 Memory Mode 下充當 DRAM 緩存層，成本遠低於等量 DRAM；二手市場價格具競爭力
- llama.cpp override-tensor 和 cmoe 自動調度，sparse MoE 將 bulk 權重駐放 PMem，規避 GPU 顯存溢出

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1taeg8h/computer_build_using_intel_optane_persistent/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

As the title states, my build is indeed able to run a 1 trillion parameter model (in this case Kimi K2.5) locally at ~4 tokens/second. I thought r/LocalLLaMA would be interested in the build due to that stat line, and also due to the inclusion of an unusual part, Intel Optane Persistent Memory, which I haven’t seen anyone use in an LLM inference build before. Optane PMem is a DIMM form factor memory unit that can function in a way that is somewhere between DRAM and an SSD. Intel has discontinued the line, and I found sticks on the secondhand market for much less than what the equivalent DRAM capacity would cost. It is this large PMem capacity (768GB) that allows me to host such large models on my system. For my build I used the PMem in Memory Mode, which is where the PMem is available to the computer as RAM, with the computer’s DRAM sticks functioning as a cache. Kimi K2.5’s mixture-of-experts architecture is an ideal test model for my build. To get the results I did, I used hybrid GPU/CPU inference with llama.cpp. Kimi K2.5’s (Unsloth Q2_K_XL quant) attention weights, the dense layer, the shared expert in each MoE layer, and the routing components are actually able to fit on my 12GB GPU using llama.cpp’s “override-tensor” flag, although I also did pretty good results just using llama.cpp’s “ngl auto” and “cmoe” flags and letting llama.cpp decide tensor placement as it sees fit too. Regardless, the sparse experts’ weights (the bulk of the model size) generally live on PMem/DRAM and get processed as needed from there. The end result from my testing with this setup is around 4 tokens per second for generation! Given the fact that this is a trillion parameter frontier-class model running on such a limited hardware budget, I would consider it to be a great success. It’s a shame Intel discontinued Optane Persistent Memory, because the current direction of some local inference innovation, including SSD offloading and broader memory tiering approaches, could have been really interesting with this specific kind of memory tier on modern hardware platforms. Overall I was pleased with this Optane PMem-centric build, it allows me to run very big models at surprisingly acceptable speeds, and the process was highly educational. Parts: - Intel Xeon Gold 6246 CPU - TYAN S5630GMRE-CGN motherboard - ASUS Dual GeForce RTX 3060 OC 12GB GPU - 6x 32GB Samsung 2666MHz DDR4 ECC DRAM sticks - 6x 128GB Intel Optane DCPMM PC4-2666 NMA1XBD128GQS persistent memory modules - Western Digital WD SN850X 2TB M.2 2280 NVMe SSD - ASRock Steel Legend SL-850G 850W 80 PLUS GOLD &amp; Cybenetics PLATINUM Full Modular Power Supply - Silverstone SST-GD08B (Black) Grandia Series Home Theater PC Case I hope you enjoyed this rundown. There is a lot more detail that I didn’t include here, so I’m happy to answer questions about the build, the configuration, or the reasoning behind any of the component choices in the comments. Also if anyone else has explored similarly unusual hardware/builds for LLM inference, I’d love to discuss! &#32; submitted by &#32; /u/APFrisco [link] &#32; [comments]

</details>