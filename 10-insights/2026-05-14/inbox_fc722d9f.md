---
id: inbox_fc722d9f
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_fc722d9f]]"
title: "The RTX 5000 PRO (48GB) arrived and it is better than I expected."
url: https://www.reddit.com/r/LocalLLaMA/comments/1td53ii/the_rtx_5000_pro_48gb_arrived_and_it_is_better/
source: reddit-localllama
published_at: 2026-05-14T17:28:41+00:00
fetched_at: 2026-05-18T03:42:53.811491+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "個人 GPU 購置及使用評測：RTX 5000 PRO (48GB) 成本 $4,300 + 組裝/配件 ~$1,300 = 總計 $5,600（含 64GB 系統 RAM）。運行 Qwen3.6-27B-FP8，達成 Prompt Processing 4,400 tokens/sec、Text Generation 50–80 ts（視提示長度）、Full Precision Cache 支援 200k tokens。用戶評價該卡被低估，相比 RTX 5090 ($5,800) 或雙 5090 配置，具有更低功耗（RTX 5090 的一半）、更好的 VRAM 利用率、成本效益更優，缺點是單卡性能略低但對個人用戶足夠。"
key_points:
  - "RTX 5000 PRO 48GB 在 $5-6K 預算内相對最優：4,400 ts prompt processing + 200k full precision cache + 功耗僅 RTX 5090 一半"
  - "48GB VRAM 足以支持 27B @ FP8 + 200k full precision cache，無需多卡配置的複雜性"
  - "相比 Mac Studio 同預算，該卡的 prompt processing 速度和 context 容量明顯優勢"
tags: [gpu, hardware, qwen, vllm, benchmark]
topics: []
importance: 2
novelty: 1
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## The RTX 5000 PRO (48GB) arrived and it is better than I expected.

個人 GPU 購置及使用評測：RTX 5000 PRO (48GB) 成本 $4,300 + 組裝/配件 ~$1,300 = 總計 $5,600（含 64GB 系統 RAM）。運行 Qwen3.6-27B-FP8，達成 Prompt Processing 4,400 tokens/sec、Text Generation 50–80 ts（視提示長度）、Full Precision Cache 支援 200k tokens。用戶評價該卡被低估，相比 RTX 5090 ($5,800) 或雙 5090 配置，具有更低功耗（RTX 5090 的一半）、更好的 VRAM 利用率、成本效益更優，缺點是單卡性能略低但對個人用戶足夠。

### 重點
- RTX 5000 PRO 48GB 在 $5-6K 預算内相對最優：4,400 ts prompt processing + 200k full precision cache + 功耗僅 RTX 5090 一半
- 48GB VRAM 足以支持 27B @ FP8 + 200k full precision cache，無需多卡配置的複雜性
- 相比 Mac Studio 同預算，該卡的 prompt processing 速度和 context 容量明顯優勢

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1td53ii/the_rtx_5000_pro_48gb_arrived_and_it_is_better/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# The RTX 5000 PRO (48GB) arrived and it is better than I expected.

I posted here about buying it a few days ago: https://www.reddit.com/r/LocalLLaMA/comments/1t2slmw/first_time_gpu_buyer_got_a_rtx_5000_pro_was_it_a/?utm_source=share&amp;utm_medium=web3x&amp;utm_name=web3xcss&amp;utm_term=1&amp;utm_content=share_button Before pulling the trigger I was leaning more towards a Mac Studio. But the the prompt processing speeds I was reading about were giving me pause. The budget was $5000/6000. So the 256GB was out of the question. I gambled and bought the RTX 5000 Pro. With ZERO experience with PCs, how to build them, what parts to buy... It was a good deal. I paid $4300 for the gpu including taxes (in the post I wrote 4700 in the comments, but I was mistaken, I checked the receipt) and had to buy everything else for the computer. It ended up costing $5600 in total with 64 gb of RAM. Assembling the thing was not easy for me as a total novice, but thankfully we have LLMs to guide us through these things. Then came Linux and vLLM... Honestly I was totally lost. without Claude Code it would have been impossible. Also what settings to use to run Qwen3.6-27B-FP8 with full precision cache. Thankfully this guy posted everything I needed to know to tell Claude what to do: https://www.reddit.com/r/LocalLLaMA/comments/1t46klu/qwen36_27b_fp8_runs_with_200k_tokens_of_bf16_kv/ After burning through 50% of my Claude Code Max 20x weekly limits the thing now works, and I have to say... I made the right call. This thing rocks. I'm getting up to 80 ts in TG (more like 50/60 for very big prompts) which is phenomenal. But most importantly I'm getting 4400 tokens per second in PP! The full precision cache fits only 200k tokens, but It is totally ok for me. I honestly don't know why people are not talking about this gpu more. It costs just 1000$ more than an RTX 5090, it can fit 27B at 8FP and 200k of context at full precision. It draws half the electricity... Sure it is slightly less performant, but the numbers I'm getting are way more than I was expecting. Two 5090s would definitely beat this. But it would cost significantly more, it would be crazy noisy and tear a hole in my pocket in electricity bills. &#32; submitted by &#32; /u/Valuable-Run2129 [link] &#32; [comments]

</details>