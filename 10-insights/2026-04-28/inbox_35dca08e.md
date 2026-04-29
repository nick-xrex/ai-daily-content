---
id: inbox_35dca08e
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0657-reddit-localllama-i-ve-created-a-lora-for-gemma-3-270m-mak-aa17]]"
title: "I&#39;ve created a LoRA for Gemma 3 270M making it probably the smallest thinking model?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1sy9x65/ive_created_a_lora_for_gemma_3_270m_making_it/
source: reddit-localllama
published_at: 2026-04-28T18:30:16+00:00
fetched_at: 2026-04-29T07:24:28.359431+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者為 Gemma 3 270M 創建了一個 LoRA 適配器（gemma-3-270M-it-smol-thinker），為該模型添加了「思考」能力，可能成為最小的思考模型。訓練數據來自程序生成數據集、Qwen 3.6 35B A3B (Q4)、GLM 5.1 三個來源。核心技術：(1) LoRA rank=24, max_length=768；(2) 定製損失函數，對未使用正確標籤的位置施加 20 倍懲罰，使訓練損失穩定在~7；(3) 訓練參數：batch_size=1，gradient_accumulation_steps=2（解決了梯度累積導致的亂碼問題）；(4) 在 RTX 3050 4GB Mobile 上訓練可行。模型能從少數 in-context 例子學會函數調用，後續計劃包括更多適配器實驗和 FunctionGemma 思考適配器。"
key_points:
  - "LoRA 訓練關鍵參數組合：rank=24, alpha=24（不能用推薦的 2x 倍數），定製損失函數（非標籤格式 20 倍懲罰），gradient_accumulation_steps=2（有效批次大小）"
  - "梯度累積步數決定有效批次大小，該參數誤配導致 40% 訓練問題（亂碼和垃圾字符）"
  - "Gemma 3 270M 可在 4GB 顯存上通過 LoRA 微調獲得思考能力（6K 上下文長度）"
tags: [lora-fine-tuning, gemma-3-270m, thinking-model, small-model]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## I've created a LoRA for Gemma 3 270M making it probably the smallest thinking model?

開發者為 Gemma 3 270M 創建了一個 LoRA 適配器（gemma-3-270M-it-smol-thinker），為該模型添加了「思考」能力，可能成為最小的思考模型。訓練數據來自程序生成數據集、Qwen 3.6 35B A3B (Q4)、GLM 5.1 三個來源。核心技術：(1) LoRA rank=24, max_length=768；(2) 定製損失函數，對未使用正確標籤的位置施加 20 倍懲罰，使訓練損失穩定在~7；(3) 訓練參數：batch_size=1，gradient_accumulation_steps=2（解決了梯度累積導致的亂碼問題）；(4) 在 RTX 3050 4GB Mobile 上訓練可行。模型能從少數 in-context 例子學會函數調用，後續計劃包括更多適配器實驗和 FunctionGemma 思考適配器。

### 重點
- LoRA 訓練關鍵參數組合：rank=24, alpha=24（不能用推薦的 2x 倍數），定製損失函數（非標籤格式 20 倍懲罰），gradient_accumulation_steps=2（有效批次大小）
- 梯度累積步數決定有效批次大小，該參數誤配導致 40% 訓練問題（亂碼和垃圾字符）
- Gemma 3 270M 可在 4GB 顯存上通過 LoRA 微調獲得思考能力（6K 上下文長度）

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1sy9x65/ive_created_a_lora_for_gemma_3_270m_making_it/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p><a href="https://huggingface.co/firstbober/gemma-3-270M-it-smol-thinker">https://huggingface.co/firstbober/gemma-3-270M-it-smol-thinker</a></p> <p>Here is an example of the output:<br /> ```<br /> ==================== THINKING ==================== Here is the thinking process:</p> <ul> <li>This is a large community with a wide range of interests</li> <li>Users can ask questions, share experiences, and discuss local events</li> <li>The rules are generally open-ended and allow for creativity</li> <li>However, the rules may be unclear or incomplete &lt;|thinking_end|&gt;</li> </ul> <p>==================== RESPONSE ====================</p> <p><a href="https://www.reddit.com/r/LocalLLaMA">r/LocalLLaMA</a> is a large, open-source question answering subreddit. Its rules are generally open-ended, allowing users to ask questions and share their experiences. However, the rules might be unclear or incomplete depending on the current state of the community.</p> <p>&lt;|response_end|&gt;<br /> ```</p> <p>It doesn't have much knowledge baked in, but with prompting it can give some interesting results.</p> <p>Lore:</p> <p>I've been working for a few days on it. First I just wanted to adapt it locally for function calling without using FunctionGemma. When it worked out (more or less) I moved to adding some thinking. The dataset was procedurally generated + some with Qwen 3.6 35B A3B (Q4 quants) + GLM 5.1.</p> <p>The biggest hurdle was figuring out how to make it keep the format, I settled for rank 24, 768 max length for training data, and customized loss function which gives 20x for not using proper tags. Due to that the loss stayed at around 7, but the effect is there.</p> <p>I've wanted to add longer examples, but my RTX 3050 4GB Mobile is kinda not enough, with train batch size of 1 and gradient accumulation step of 2 this is the best I could do.</p> <p>Another interesting thing, Claude/Gemini were saying that bigger <code>gradient_accumulation_steps</code> essentially meant larger batch size but without actually increasing the batch size. This accounted for like 40% of all of my headaches, with model spitting utter garbage and random chinese slop characters.</p> <p>Well, I think that's all, here are all the relevant training parameters:<br /> ```<br /> SFTConfig:</p> <p>per_device_train_batch_size=1, gradient_accumulation_steps=2, per_device_eval_batch_size=1, learning_rate=1e-4, lr_scheduler_type=&quot;cosine&quot;, warmup_ratio=0.10, weight_decay = 0.1, load_best_model_at_end=True,</p> <p>LoraConfig:</p> <p>n_rank = 24 r=n_rank, lora_alpha=n_rank, target_modules=[&quot;q_proj&quot;, &quot;v_proj&quot;, &quot;k_proj&quot;, &quot;o_proj&quot;, &quot;gate_proj&quot;, &quot;up_proj&quot;, &quot;down_proj&quot;], lora_dropout=0.15, task_type=&quot;CAUSAL_LM&quot;,<br /> ```</p> <p>Oh, also increasing alpha to 2x rank as recommended in paper kinda broke everything, this is another thing that was pretty frustrating to figure out.</p> <p>I plan to continue and train some more adapters with other ideas, maybe I'll switch to Qwen 3.5 0.8B when I buy a card with enough VRAM? I don't know. One thing I'll definitely do is thinking adapter for FunctionGemma, as it would fix my issues with function calling to some degree.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Firstbober"> /u/Firstbober </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1sy9x65/ive_created_a_lora_for_gemma_3_270m_making_it/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1sy9x65/ive_created_a_lora_for_gemma_3_270m_making_it/">[comments]</a></span>

</details>