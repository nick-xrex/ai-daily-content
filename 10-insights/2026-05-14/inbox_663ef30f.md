---
id: inbox_663ef30f
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_663ef30f]]"
title: "I Let a Small Model Train on Its Own Mistakes. It Reached 80% on HumanEval and Beat GPT-3.5 on Math"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tde3m1/i_let_a_small_model_train_on_its_own_mistakes_it/
source: reddit-localllama
published_at: 2026-05-14T22:55:05+00:00
fetched_at: 2026-05-18T03:56:37.264332+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "一位研究者展示了無需人工標註數據的自我修正微調方法，利用 Python 解釋器作為唯一評判標準讓模型在自己的錯誤上迭代學習。Qwen 2.5 7B 在 HumanEval 測試中從 25 躍升到 112（+87 道題目），Qwen 2.5 14B 經 95 分鐘 H100 運行（成本僅 $3.50）達到官方 RLHF 版本的性能。方法跨越多個模型家族（Llama 3.2 3B、Qwen 3）皆有驗證效果，3B 模型甚至在數學推理上超越 ChatGPT 3.5。最關鍵發現：訓練和測試時採樣間存在臨界點，數據量過小時直接採樣優於微調——這是未在文獻中被明確記錄的現象。"
key_points:
  - "自我修正微調：Qwen 2.5 7B HumanEval +348%（25→112），Qwen 2.5 14B 達官方 RLHF 性能，成本僅 $3.50 H100 時長"
  - "跨模型通用性：Llama 3.2 3B、Qwen 3 等不同架構與廠商都驗證有效，非 Qwen 專屬現象"
  - "訓練-採樣臨界值：小數據集（<36 對）時直接採樣優於微調；訓練會削弱採樣的多樣性收益"
tags: [self-correction-training, low-resource-optimization, cross-model-generalization]
topics: []
importance: 4
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## I Let a Small Model Train on Its Own Mistakes. It Reached 80% on HumanEval and Beat GPT-3.5 on Math

一位研究者展示了無需人工標註數據的自我修正微調方法，利用 Python 解釋器作為唯一評判標準讓模型在自己的錯誤上迭代學習。Qwen 2.5 7B 在 HumanEval 測試中從 25 躍升到 112（+87 道題目），Qwen 2.5 14B 經 95 分鐘 H100 運行（成本僅 $3.50）達到官方 RLHF 版本的性能。方法跨越多個模型家族（Llama 3.2 3B、Qwen 3）皆有驗證效果，3B 模型甚至在數學推理上超越 ChatGPT 3.5。最關鍵發現：訓練和測試時採樣間存在臨界點，數據量過小時直接採樣優於微調——這是未在文獻中被明確記錄的現象。

### 重點
- 自我修正微調：Qwen 2.5 7B HumanEval +348%（25→112），Qwen 2.5 14B 達官方 RLHF 性能，成本僅 $3.50 H100 時長
- 跨模型通用性：Llama 3.2 3B、Qwen 3 等不同架構與廠商都驗證有效，非 Qwen 專屬現象
- 訓練-採樣臨界值：小數據集（<36 對）時直接採樣優於微調；訓練會削弱採樣的多樣性收益

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tde3m1/i_let_a_small_model_train_on_its_own_mistakes_it/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I Let a Small Model Train on Its Own Mistakes. It Reached 80% on HumanEval and Beat GPT-3.5 on Math

A few months ago, I got stuck on one line in the DeepSeek-R1 paper. It said models could improve through verifiable rewards. That sounded almost magical to me. Not because it was impossible, but because it made me wonder something very simple: What if a model could teach itself to code, without humans writing the training data? I did not have a lab. I did not have a grant. I had a 24GB MacBook, a RunPod account with some credits and a Python interpreter. So I tried. THE PLAN In plain English. I'd ask a base model to invent a coding problem and write a few small tests for it. Then ask the same model to solve its own problem several times. Sometimes it gets the answer right, sometimes wrong. I'd save the pairs of (broken attempt, working attempt) and fine-tune the model on its own corrections. Nothing human written. The Python interpreter is the only judge in the loop. https://preview.redd.it/l5c80d0vm61h1.png?width=1200&amp;format=png&amp;auto=webp&amp;s=5474f9a3f0ae632b663db47245c4701dc2d0ff43 THE PART WHICH WASN'T IN PLAN I started with Qwen 2.5 7B base. Trained on its own mined pairs. Ran HumanEval (a standard set of 164 coding problems). The base model got 25 right. After training, 2 I'd made the model worse. I spent the next day pair-debugging with Claude Code and Codex. The model was producing what looked like correct code in the logs. The grader kept rejecting it. We found the bug around 2am: the grader was stopping too early, cutting the model's function in half before scoring it. The model was writing complete correct functions. The grader was scoring the truncated halves. THE PART THAT WORKED Once I fixed it and re-ran, Qwen 2.5 7B base went from 25 to 112 on HumanEval. That's +87 problems. From a model trained on zero human-written code. So I tried it bigger. Qwen 2.5 14B base. Mined 100 of its own pairs. Trained. 95 minute H100 run, $3.50 of cloud credit. https://preview.redd.it/dyyuocezm61h1.png?width=1200&amp;format=png&amp;auto=webp&amp;s=30bd5008daffd6e1f690db9d7daf9c45281f2115 The base model, trained only on its own mistakes, lands within 4 points of the same company's RLHF version of itself. https://preview.redd.it/6bbb5x12n61h1.png?width=1200&amp;format=png&amp;auto=webp&amp;s=2ff3f3c53649a3eaf13109d4014e6c1956cbda6d I didn't believe it. So I ran a test that would kill the whole thing if it failed. What if the model was just getting smarter from training on any data in this format? I built fake training pairs of the same length and shape as my real ones, but with random garbage code inside that didn't pass anything. Trained on those. Score: 25 out of 164. Same as the base. Zero lift. So the model wasn't getting smarter from generic training. It was getting smarter specifically from training on its own mistakes and corrections. The signal was real. Now I got more curious. Was this a Qwen-only thing, or would it work on other model families? I tried Llama 3.2 3B from Meta. Different architecture, different tokenizer, different training corpus. After self-mining 32 pairs and training, HumanEval went from 39 to 43. The lift is small but the sign is right. The recipe transfers across families. I tried Qwen 2.5 Coder 7B base, which is already a code-specialized model. After self-mining: HumanEval 83 to 87, MBPP 122 to 124. Even a model already optimized for code picked up a small lift. I tried Qwen 3, a newer generation than what I'd been using. Qwen 3 4B base specifically. After the recipe: HumanEval 79 to 106 (+27 problems), MBPP 135 to 148. https://preview.redd.it/sdufx1a7n61h1.png?width=1200&amp;format=png&amp;auto=webp&amp;s=a122a7ad505bf96a217354433e688f267b318692 Different architectures, different generations, different vendors. The recipe is not a Qwen quirk. THE UNEXPECTED THAT WASN'T PLAN EITHER Then I got more curious about whether it'd work for math. The trick is the judge. Python checks code. SymPy can check math. Same loop should apply. First attempt failed. When I asked the base model to invent its own math problems, it produced easy arithmetic. That didn't transfer to GSM8K, which is grade-school word problems with multiple reasoning steps. So I added a twist. When the model solved its own made-up problem on every try, the next problem had to be harder. When it kept failing, the next had to be easier. The model gradually drifted toward problems at the edge of its ability. https://preview.redd.it/uubxde4cn61h1.png?width=1200&amp;format=png&amp;auto=webp&amp;s=4922a14f233814224a9d0da7d3cc2a36739f25ab A 3B model, trained on 13 math problems it wrote for itself, beats the version of ChatGPT that broke the internet in 2022. Then, the finding I'm most proud of. There are two ways to improve a model. One is training: change the model itself. The other is test-time sampling: don’t change the model, just ask it multiple times and keep the answer that passes the tests. I expected them to add up. Training should make the model better. Sampling should give the better model more chances. So training + sampling should beat sampling alone. But that is not always what happened. https://preview.redd.it/mmlkmh7fn61h1.png?width=1199&amp;format=png&amp;auto=webp&amp;s=89361ebd350ca17317b5b2902816447c02a6ba10 At 100 mined pairs, training and sampling compound. At 36 pairs, they fight each other. The training narrows the model's output diversity so much that sampling loses the variety that made it useful. There's a threshold. I have not seen this written down anywhere. If you have a small dataset, you might be better off not fine-tuning and just sampling from the base. The standard advice (&quot;always fine-tune when you can&quot;) is wrong below the threshold. This is the finding I most want other researchers to test and try to break. The list of things that didn't work, because the field hides these and shouldn't: Training on (wrong answer, then corrected answer) for math destroyed the model. Qwen 3 4B went from 60% to 14% on MATH-500. Training only on corrections taught the model to always doubt itself, even when it was right. Fix: mix in examples where a correct answer stays correct. Recipe trained on code does almost nothing on math. +2 problems on GSM8K. The signal doesn't carry across domains. Iterating (using the trained model to mine more, retrain) plateaus by round 2. Recipe doesn't work on already-strong models. Qwen 3 8B, Qwen 3 14B, Qwen 2.5 72B all got slightly worse. Not enough wrong attempts to mine from. Recipe doesn't work on too-weak models either. OLMo 2 7B at 3% on HumanEval can't produce enough right answers to mine from. HumanEval-style problems don't transfer to real-world Python that uses libraries like pandas. Different worlds. https://preview.redd.it/1pzr1isgn61h1.png?width=1200&amp;format=png&amp;auto=webp&amp;s=dc7e8153a73d38057ca3ef7925fdb4c867bdea66 THE HARDEST PART BY COLDPLAY The hardest part of this whole thing wasn't the math or the code. It was learning to suspect my own results before celebrating them. The stop-token bug almost killed the project on day one. Without an advisor to catch me, I had to learn to be the person who catches me. Everything is open: Code and reproduction guide: github.com/ranausmanai/tinyforge-zero 14B adapter weights: huggingface.co/ranausmans/tinyforge-zero-qwen25-14b-lora Paper: arXiv link as soon as moderation clears. &#32; submitted by &#32; /u/QuantumSeeds [link] &#32; [comments]

</details>