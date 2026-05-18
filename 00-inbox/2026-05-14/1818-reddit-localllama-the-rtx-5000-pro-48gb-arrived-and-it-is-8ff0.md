---
id: inbox_fc722d9f
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1td53ii/the_rtx_5000_pro_48gb_arrived_and_it_is_better/"
author: "/u/Valuable-Run2129"
published_at: 2026-05-14T17:28:41+00:00
fetched_at: 2026-05-14T18:18:30.434808+00:00
content_hash: "8ff0ab51de3e132c6a80411e1780a11b5c29284fdcc6446dfccdf46cf0e25c2a"
lang: en
caption_quality: None
raw: true
topics: []
---

# The RTX 5000 PRO (48GB) arrived and it is better than I expected.

I posted here about buying it a few days ago: https://www.reddit.com/r/LocalLLaMA/comments/1t2slmw/first_time_gpu_buyer_got_a_rtx_5000_pro_was_it_a/?utm_source=share&amp;utm_medium=web3x&amp;utm_name=web3xcss&amp;utm_term=1&amp;utm_content=share_button Before pulling the trigger I was leaning more towards a Mac Studio. But the the prompt processing speeds I was reading about were giving me pause. The budget was $5000/6000. So the 256GB was out of the question. I gambled and bought the RTX 5000 Pro. With ZERO experience with PCs, how to build them, what parts to buy... It was a good deal. I paid $4300 for the gpu including taxes (in the post I wrote 4700 in the comments, but I was mistaken, I checked the receipt) and had to buy everything else for the computer. It ended up costing $5600 in total with 64 gb of RAM. Assembling the thing was not easy for me as a total novice, but thankfully we have LLMs to guide us through these things. Then came Linux and vLLM... Honestly I was totally lost. without Claude Code it would have been impossible. Also what settings to use to run Qwen3.6-27B-FP8 with full precision cache. Thankfully this guy posted everything I needed to know to tell Claude what to do: https://www.reddit.com/r/LocalLLaMA/comments/1t46klu/qwen36_27b_fp8_runs_with_200k_tokens_of_bf16_kv/ After burning through 50% of my Claude Code Max 20x weekly limits the thing now works, and I have to say... I made the right call. This thing rocks. I'm getting up to 80 ts in TG (more like 50/60 for very big prompts) which is phenomenal. But most importantly I'm getting 4400 tokens per second in PP! The full precision cache fits only 200k tokens, but It is totally ok for me. I honestly don't know why people are not talking about this gpu more. It costs just 1000$ more than an RTX 5090, it can fit 27B at 8FP and 200k of context at full precision. It draws half the electricity... Sure it is slightly less performant, but the numbers I'm getting are way more than I was expecting. Two 5090s would definitely beat this. But it would cost significantly more, it would be crazy noisy and tear a hole in my pocket in electricity bills. &#32; submitted by &#32; /u/Valuable-Run2129 [link] &#32; [comments]