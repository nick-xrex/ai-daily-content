---
id: inbox_2c4f90c5
date: 2026-05-18
source_ref: "[[00-inbox/.../inbox_2c4f90c5]]"
title: "Qwen 3.6 27B Q8 on four Nvidia RTX A4000 (16GB each) with Llama.cpp and MTP enabled"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tgb8lv/qwen_36_27b_q8_on_four_nvidia_rtx_a4000_16gb_each/
source: reddit-localllama
published_at: 2026-05-18T03:58:21+00:00
fetched_at: 2026-05-19T02:37:37.552744+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶分享在4張RTX A4000 16GB顯卡上運行Qwen 3.6 27B Q8 GGUF，搭配Llama.cpp與MTP推理優化。設定--spec-draft-n-max 4時性能最佳，推理時45 tokens/sec，編碼時60 tokens/sec。同時運行Qwen 3.6 35B A3B MoE模型（layer split模式）達80-90 tokens/sec但編碼能力較弱。驗證舊型顯卡（購入$865、現值$1,500）通過軟件優化仍能提供競爭力性能。"
key_points:
  - "MTP推理最佳參數--spec-draft-n-max 4，Qwen 3.6 27B達45-60 tokens/sec（推理/編碼）"
  - "Qwen 3.6 35B A3B MoE達80-90 tokens/sec但編碼能力相對較弱，單模型27B在coding場景更優"
  - "4×RTX A4000 16GB總成本$3,460新價，125W單卡功耗設定穩定運行"
tags: [qwen-mtp-inference, llama-cpp-optimization, gpu-throughput-benchmark]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen 3.6 27B Q8 on four Nvidia RTX A4000 (16GB each) with Llama.cpp and MTP enabled

用戶分享在4張RTX A4000 16GB顯卡上運行Qwen 3.6 27B Q8 GGUF，搭配Llama.cpp與MTP推理優化。設定--spec-draft-n-max 4時性能最佳，推理時45 tokens/sec，編碼時60 tokens/sec。同時運行Qwen 3.6 35B A3B MoE模型（layer split模式）達80-90 tokens/sec但編碼能力較弱。驗證舊型顯卡（購入$865、現值$1,500）通過軟件優化仍能提供競爭力性能。

### 重點
- MTP推理最佳參數--spec-draft-n-max 4，Qwen 3.6 27B達45-60 tokens/sec（推理/編碼）
- Qwen 3.6 35B A3B MoE達80-90 tokens/sec但編碼能力相對較弱，單模型27B在coding場景更優
- 4×RTX A4000 16GB總成本$3,460新價，125W單卡功耗設定穩定運行

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tgb8lv/qwen_36_27b_q8_on_four_nvidia_rtx_a4000_16gb_each/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Qwen 3.6 27B Q8 on four Nvidia RTX A4000 (16GB each) with Llama.cpp and MTP enabled

Qwen 3.6 27B Q8 on four Nvidia RTX A4000 (16GB each) with Llama.cpp and MTP enabled My setup is heterogenous, I originally acquired my server (Lenovo ThinkStation P3 Tower Gen 2) to run OpenShift/K8s clusters (because I work on that), and later on I started purchasing one by one those cards Nvidia RTX A4000 with 16GB of VRAM each, yes, old technology, but hear me out, 140W each card, one PCIe slot per card. I can accommodate four cards on my server. I've capped the cards to 125W as I was reading that at max power the performance is not that good, and I agree, performance remains quite good and stable. These are my options, --spec-draft-n-max 4 for MTP is yielding the best performance for me. I use Fedora 43 with CUDA drivers, of course. ExecStart=/usr/bin/bash -lc '\ /home/user/llama-server-experiments/llama.cpp/build/bin/llama-server \ --models-dir /home/user/qwen3.6/mtp-variations \ --chat-template &quot;$(cat /home/user/qwen3.6/chat_template.jinja)&quot; \ --ctx-size 262114 \ --fit on \ --n-gpu-layers 999 \ --split-mode tensor \ --parallel 1 \ --flash-attn on \ --host 0.0.0.0 \ --port 8081 \ --timeout 2200 \ --spec-type mtp \ --spec-draft-n-max 4' I'm running the Q8 variant of Qwen 3.6 27B on GGUF with MTP enabled. https://huggingface.co/froggeric/Qwen3.6-27B-MTP-GGUF For reasoning I see 45-ish tokens per second. For coding, as you can see it speeds up quite a lot to 60s tokens per second. I'm running at full context without any KV cache quantization. I finally feel that my cards were not that bad purchase at the end of the day. $865 dollars when I've purchased them, now these are around $1,300 used, almost $1,500 new. I also have Qwen 3.6 35B A3B Q8 MoE running with --split-mode layer and that achieves 90-ish tokens per second when coding, while 80-ish tokens per second when reasoning. That MoE model does not fit on tensor mode, only on layer mode, and it uses way less energy. However I'm not totally happy with its real life coding skills; don't get me wrong, it converges to a solution, but at the second or third attempt. While Qwen 2.6 27B dense, tends towards first shot more often than not, or at most with some good feedback on the second attempt. I was really discouraged one year and a half ago, I honestly was not even involved on local inference community, sitting on a 7k duck of server, I was only running my OCP/K8s workloads and that's it. Now I feel redeemed. The moral of the story is that we need to keep making pressure on the market to get more out of our hardware. And we will, even for 2020 graphic cards. https://preview.redd.it/s5ymj3eqgt1h1.png?width=1720&amp;format=png&amp;auto=webp&amp;s=f99870b093a58259e9668ca6cd6db0127e84a6eb https://preview.redd.it/7mpdprjrgt1h1.png?width=825&amp;format=png&amp;auto=webp&amp;s=8ad21d68aaee6b611381818f884d70117fc96e0a &#32; submitted by &#32; /u/Alternative_Ad4267 [link] &#32; [comments]

</details>