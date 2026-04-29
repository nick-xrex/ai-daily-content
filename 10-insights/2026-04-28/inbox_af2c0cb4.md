---
id: inbox_af2c0cb4
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0658-reddit-claudeai-talkie-a-13b-llm-trained-only-on-pre-193-591c]]"
title: "Talkie: a 13B LLM trained only on pre-1931 text used Claude Sonnet to help test the model and judge its output"
url: https://www.reddit.com/r/ClaudeAI/comments/1sy7rry/talkie_a_13b_llm_trained_only_on_pre1931_text/
source: reddit-claudeai
published_at: 2026-04-28T17:16:29+00:00
fetched_at: 2026-04-29T07:24:28.368093+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "研究人員（包括 GPT/CLIP/Whisper 之父 Alec Radford）發布了 Talkie：13 億參數語言模型，訓練數據**完全來自 1931 年前出版的文本**，知識截止於 1930 年 12 月 31 日。該研究旨在打破現代 LLM（GPT、Claude、Gemini、Llama）都源自現代網路的共同祖先，用分布外數據隔離推理能力 vs 記憶能力的根本問題。**Claude 直接參與開發**：Claude Sonnet 4.6 充當線上 DPO 強化學習管道的評判者，Claude Opus 4.6 生成最終微調階段的合成多轉對話（團隊承認這存在汙染風險，計劃後續改進）。驚人發現：Talkie 能從少數 in-context 例子自行開發 Python 編寫能力，儘管訓練數據中零現代程式碼——純粹來自 19 世紀數學文本的泛化推理。研究焦點包括長期預測、發明能力、LLM 身份定義。模型 Apache 2.0 開源，Hugging Face 發布，計劃今年發布 GPT-3 規模古代文本版本。"
key_points:
  - "古代文本作為 OOD 測試集：用 1931 年前數據訓練的模型隔離「架構推理」vs「網路吸收記憶」，突破現代 LLM 無法分離二者的困局"
  - "Claude 的雙重角色：Sonnet 4.6 作 DPO 評判者，Opus 4.6 生成合成訓練數據——現代 LLM 塑造古代 LLM，反向污染提示了下一步改進方向"
  - "泛化證據：零代碼訓練數據下學會 Python 編寫，證明 LLM 能從數學文本進行真實推理而非記憶"
tags: [talkie-lm, vintage-training-data, memorization-vs-generalization, ood-evaluation, claude-integration]
topics: [foundation_models.claude]
importance: 4
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Talkie: a 13B LLM trained only on pre-1931 text used Claude Sonnet to help test the model and judge its output

研究人員（包括 GPT/CLIP/Whisper 之父 Alec Radford）發布了 Talkie：13 億參數語言模型，訓練數據**完全來自 1931 年前出版的文本**，知識截止於 1930 年 12 月 31 日。該研究旨在打破現代 LLM（GPT、Claude、Gemini、Llama）都源自現代網路的共同祖先，用分布外數據隔離推理能力 vs 記憶能力的根本問題。**Claude 直接參與開發**：Claude Sonnet 4.6 充當線上 DPO 強化學習管道的評判者，Claude Opus 4.6 生成最終微調階段的合成多轉對話（團隊承認這存在汙染風險，計劃後續改進）。驚人發現：Talkie 能從少數 in-context 例子自行開發 Python 編寫能力，儘管訓練數據中零現代程式碼——純粹來自 19 世紀數學文本的泛化推理。研究焦點包括長期預測、發明能力、LLM 身份定義。模型 Apache 2.0 開源，Hugging Face 發布，計劃今年發布 GPT-3 規模古代文本版本。

### 重點
- 古代文本作為 OOD 測試集：用 1931 年前數據訓練的模型隔離「架構推理」vs「網路吸收記憶」，突破現代 LLM 無法分離二者的困局
- Claude 的雙重角色：Sonnet 4.6 作 DPO 評判者，Opus 4.6 生成合成訓練數據——現代 LLM 塑造古代 LLM，反向污染提示了下一步改進方向
- 泛化證據：零代碼訓練數據下學會 Python 編寫，證明 LLM 能從數學文本進行真實推理而非記憶

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1sy7rry/talkie_a_13b_llm_trained_only_on_pre1931_text/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Researchers Alec Radford (GPT, CLIP, Whisper), Nick Levine, and David Duvenaud just released <strong>talkie</strong>: a 13 billion parameter language model trained <em>exclusively</em> on text published before 1931. No internet. No Wikipedia. No World War II. Its worldview is frozen at December 31, 1930.</p> <p><strong>Why does this matter?</strong></p> <p>Every major LLM today (GPT, Claude, Gemini, Llama) ultimately shares a common ancestor: the modern web. That makes it nearly impossible to tell what these models genuinely <em>reason</em> versus what they simply <em>memorized</em>.</p> <p>Talkie breaks that lineage entirely. From the team:</p> <blockquote> <p><em>&quot;It's an important question how much LM capabilities arise from memorization vs generalization. Vintage LMs enable unique generalization tests.&quot;</em></p> </blockquote> <p>Interestingly, Claude has a direct role in talkie's creation: <strong>Claude Sonnet 4.6</strong> was used as the judge in talkie's reinforcement learning pipeline (online DPO), and Claude Opus 4.6 generated synthetic multi-turn conversations used in the final fine-tuning stage. The team even notes the irony: using a thoroughly modern LLM to help shape a model that's supposed to be frozen in 1930, and flagging it as a contamination risk they're actively working to eliminate in future versions.</p> <p>The most striking example: <strong>talkie can learn to write Python code from just a few in-context examples... despite having zero modern code in its training data.</strong> It's reasoning from 19th-century mathematics texts, not retrieval.</p> <p><strong>What it's being used to study</strong></p> <ul> <li><strong>Long-range forecasting</strong>: how well can a model &quot;predict&quot; the future from its frozen vantage point?</li> <li><strong>Invention</strong>: can it develop ideas that postdate its knowledge cutoff?</li> <li><strong>LLM identity</strong>: what makes a model <em>itself</em>? Talkie's alien data distribution helps isolate what's architecture vs. what's just &quot;vibes absorbed from the web&quot;</li> </ul> <p><strong>Links</strong></p> <ul> <li><a href="https://talkie-lm.com/chat">Chat with talkie live</a></li> <li><a href="https://talkie-lm.com/introducing-talkie">Official blog post</a></li> <li><a href="https://x.com/status_effects/status/2048878495539843211?s=20">Original announcement on X</a></li> <li><a href="https://reddit.com/r/accelerate/comments/1sxmjeq/new_research_from_alec_radford_key_openai/">Discussion on r/accelerate</a></li> <li><a href="https://www.reddit.com/r/singularity/s/qQnKdFHjWs">Discussion on r/singularity</a></li> </ul> <p>Both models are <strong>Apache 2.0 licensed</strong> and open-weight on Hugging Face. The team is already planning a GPT-3-scale vintage model for later this year.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/BatPlack"> /u/BatPlack </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1sy7rry/talkie_a_13b_llm_trained_only_on_pre1931_text/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1sy7rry/talkie_a_13b_llm_trained_only_on_pre1931_text/">[comments]</a></span>

</details>