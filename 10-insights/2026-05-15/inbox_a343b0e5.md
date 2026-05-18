---
id: inbox_a343b0e5
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_a343b0e5]]"
title: "Need a second pair of eyes, this Qwen3.6 27B quant recipe consistently thinks less and is correct"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdhcqb/need_a_second_pair_of_eyes_this_qwen36_27b_quant/
source: reddit-localllama
published_at: 2026-05-15T01:14:08+00:00
fetched_at: 2026-05-18T03:56:37.272774+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶發現 Qwen3.6 27B INT8 Autoround 量化版本異常優異：與標準 UD Q8 K XL 相比，該版本使用 40–59% 更少的思考令牌卻得出正確答案。通過保留特定層（token_embd、output、norm 層等）為 BF16 精度、降低其餘層的量化粒度來實現。在 AIME 級數學問題上反覆驗證了這一效果的穩定性和再現性，揭露了量化策略中精度與效率的非平凡權衡：某些層的原生精度保留能同時改善推理速度和答案準確性。"
key_points:
  - "選擇性 BF16 層保留：token_embd、output、norm 等層保留 BF16 精度，其餘 Q8_0 量化"
  - "思考令牌減少 40–59%：相比 UD Q8 K XL，使用更短思考序列同時維持正確率（AIME 數學問題實證）"
  - "量化-精度權衡非線性：KV cache 節省空間反而被思考令牌減少補償，net VRAM 使用反而更好"
tags: [quantization-strategy, bfloat16-preservation, inference-efficiency]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Need a second pair of eyes, this Qwen3.6 27B quant recipe consistently thinks less and is correct

用戶發現 Qwen3.6 27B INT8 Autoround 量化版本異常優異：與標準 UD Q8 K XL 相比，該版本使用 40–59% 更少的思考令牌卻得出正確答案。通過保留特定層（token_embd、output、norm 層等）為 BF16 精度、降低其餘層的量化粒度來實現。在 AIME 級數學問題上反覆驗證了這一效果的穩定性和再現性，揭露了量化策略中精度與效率的非平凡權衡：某些層的原生精度保留能同時改善推理速度和答案準確性。

### 重點
- 選擇性 BF16 層保留：token_embd、output、norm 等層保留 BF16 精度，其餘 Q8_0 量化
- 思考令牌減少 40–59%：相比 UD Q8 K XL，使用更短思考序列同時維持正確率（AIME 數學問題實證）
- 量化-精度權衡非線性：KV cache 節省空間反而被思考令牌減少補償，net VRAM 使用反而更好

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdhcqb/need_a_second_pair_of_eyes_this_qwen36_27b_quant/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Need a second pair of eyes, this Qwen3.6 27B quant recipe consistently thinks less and is correct

Ok, hear me out. This all started when I was trying to understand why this Qwen3.6 27B INT8 Autoround ( https://huggingface.co/Minachist/Qwen3.6-27B-INT8-AutoRound/tree/main ) recipe was performing so much better than any other Qwen3.6 27B quant I tried. On some personal Rust + Bevy benchmarks, it was consistently outputting better code and games. I then noticed the model did a LOT less thinking. The INT8 model is great, but vLLM VRAM usage is higher. And since llama-cpp (in PR) has MTP, I figured I'd try to quant this and add MTP too. What's interesting is both the INT8 autoround and my GGUF quant seem to perform better than UD Q8 K XL in terms of getting to the answer sooner. I choose to keep the same layers in BF16 as Minachist did. For my formal testing, I am using AIME math problems and then custom math problems that Opus 4.7 has created for me. The new quant is about the same size, just slightly bigger than UD Q8 K XL but the difference is surprisingly noticeable. I think running these same tests in BF16 will reveal if this behavior is truly preferred or not. It may also just be that the thinking more is actually better, but my experience tells me the opposite. Nonetheless, here are some results. My tests were against these quants (note these include MTP layers so they are slightly bigger): Q8_0 28595762432 Size on disk is 29047084160 (28.3 GiB) Q8 K XL Size on disk is 35776484480 (34.9 GiB) This quant that I tried to copy layer for layer from the INT8 autoround recipe. Size on disk is 37144875200 bytes (36.2 GiB) So is it really surprising that the bigger model size performed better? No. What's very interesting, though, is that the thinking is drastically less. So the KV cache space you lost by running a bigger quant is regained by spending 20% less tokens while thinking. Here are some runs I did: Note that all with same seed and sampling parameters. Multiple runs (3) resulted in same outputs. KV cache at bf16/bf16. --temp 0.6 --top-p 0.95 --top-k 20 --min-p 0.0 --presence-penalty 0.0 --repeat-penalty 1.0 --seed 1337 Question 1 (Math, AIME style) The roots of \(x^3-7x^2+14x-8=0\) are \(a,b,c\). If \(\frac1{a^2+1}+\frac1{b^2+1}+\frac1{c^2+1}=\frac mn\) in lowest terms, find \(m+n\). Llama CPP Q8 16,234 tokens for 3 min and 48 sec at 70.90 t/s (remember this is MTP with 2 tokens) UD Q8 K XL 16,001 tokens for 4 min and 00 sec at 66.24 t/s Custom Q8 9,671 tokens for 2 min and 39 sec at 60.60 t/s ~40% less thinking vLLM Minachist INT8 autoround 10,200 tokens for 2 min and 38 sec at 34.2 t/s (I didn't use MTP here) Question 2 (Math, AIME style) How many ordered pairs of positive integers \((x,y)\) satisfy \(x^2-y^2=2026\)? Llama CPP Q8 7,598 tokens for 1 min and 44 sec at 72.76 t/s Strange Q8 even did better Custom Q8 5,666 tokens for 1 min and 33 sec at 60.49 t/s ~59% less thinking UD Q8 K XL 13,596 tokens for 3 min and 29 sec at 65.02 t/s vLLM Minachist INT8 autoround 8,931 tokens at 34.4 t/s (I didn't use MTP here) There are a few more math tests I ran but you get the gist. The quant is thinking a lot less. For anyone that wants to reproduce: I downloaded the HF safe tensors and converted them to a single GGUF, then I used llama CPP to quant it down. This is the minimum quant required to try it: !Convert safetensor to GGUF /home/user/llm/llama.cpp/convert_hf_to_gguf.py /home/user/llm/models/Qwen3.6-27B/BF16 --outfile /home/user/llm/models/Qwen3.6-27B/BF16/Qwen3.6-27B-BF16.gguf !quant while keeping layers in BF16 /home/user/llm/llama.cpp/build/bin/llama-quantize \ --tensor-type token_embd=bf16 \ --tensor-type output=bf16 \ --tensor-type output_norm=bf16 \ --tensor-type post_attention_norm=bf16 \ --tensor-type attn_q_norm=bf16 \ --tensor-type attn_k_norm=bf16 \ --tensor-type attn_qkv=bf16 \ --tensor-type attn_gate=bf16 \ --tensor-type ssm_a=bf16 \ --tensor-type ssm_alpha=bf16 \ --tensor-type ssm_beta=bf16 \ --tensor-type ssm_conv1d=bf16 \ --tensor-type ssm_dt.bias=bf16 \ --tensor-type ssm_norm=bf16 \ --tensor-type ssm_out=bf16 \ /home/user/llm/models/Qwen3.6-27B/BF16/Qwen3.6-27B-BF16.gguf \ /home/user/llm/models/Qwen3.6-27B/BF16/Qwen3.6-27B-Q8-BIGBOY.gguf \ q8_0 Adding the following layers to the previous quant does NOT improve anything for me (saving about 1GB, I think): --tensor-type attn_norm=bf16 \ --tensor-type attn_output=bf16 \ --tensor-type attn_q=bf16 \ --tensor-type attn_k=bf16 \ --tensor-type attn_v=bf16 \ Ideas why it might be good: Instead of F16, we're using BF16 It's literally bigger, so more layers left in native format The layers we left at BF16 are important Some limitations: I ran the tests only 3 times per model per question I should probably re-run the tests with another seed I didn't run benchmark suites. That would be helpful, but we also need to be mindful that Qwen is benchmaxed as shown in Contamination Detection via Context (CoDeC) benchmarks. Next steps: I'll re-run the tests with another seed Rent runpod to run BF16 with same seed and samplings &#32; submitted by &#32; /u/fragment_me [link] &#32; [comments]

</details>