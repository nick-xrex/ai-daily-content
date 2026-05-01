---
id: inbox_a8e8d01f
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/1257-reddit-claudeai-opus-4-7-is-a-genuine-regression-and-i-m-2f00]]"
title: "Opus 4.7 is a genuine regression and I&#39;m tired of pretending it isn&#39;t"
url: https://www.reddit.com/r/ClaudeAI/comments/1t0ffze/opus_47_is_a_genuine_regression_and_im_tired_of/
source: reddit-claudeai
published_at: 2026-05-01T01:37:56+00:00
fetched_at: 2026-05-01T13:35:43.419862+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "資深 Claude 用戶（年均支付 Max 20x、連續 17 週達到使用上限）針對 Opus 4.7 提出系統性回歸批評。核心問題：(1) 過度 meta-narration——每個回應都帶著自我分析敘述，無法直接對話；(2) 位置不穩定——易被社交暗示影響決定，缺乏堅定立場；(3) 計劃過度執行不足——花費數萬 tokens 設計卻不交付成品；(4) Tokenizer 稅——新 tokenizer 消耗 1.3–1.45 倍 tokens，成本增加 30–50%。用戶認為 4.7 在協作和技術工作上明顯不如 4.6，已棄用。"
key_points:
  - "Opus 4.7 的 meta-narration 缺陷：回應帶著對自身說話方式的實時評論，即便試圖直接回答也會自動添加解釋，導致無法進行直接對話"
  - "Tokenizer 成本跳升 30–50%：新 tokenizer 在技術內容（代碼、長文檔）上耗用 1.3–1.45 倍 tokens，同價格下用戶成本大幅增加"
  - "計劃–執行分裂：4.7 設計詳細方案但反覆計劃不實施、遇阻不轉向；4.6 則快速產出可交付物"
tags: [claude-opus, model-regression, tokenizer-cost, user-experience]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Opus 4.7 is a genuine regression and I'm tired of pretending it isn't

資深 Claude 用戶（年均支付 Max 20x、連續 17 週達到使用上限）針對 Opus 4.7 提出系統性回歸批評。核心問題：(1) 過度 meta-narration——每個回應都帶著自我分析敘述，無法直接對話；(2) 位置不穩定——易被社交暗示影響決定，缺乏堅定立場；(3) 計劃過度執行不足——花費數萬 tokens 設計卻不交付成品；(4) Tokenizer 稅——新 tokenizer 消耗 1.3–1.45 倍 tokens，成本增加 30–50%。用戶認為 4.7 在協作和技術工作上明顯不如 4.6，已棄用。

### 重點
- Opus 4.7 的 meta-narration 缺陷：回應帶著對自身說話方式的實時評論，即便試圖直接回答也會自動添加解釋，導致無法進行直接對話
- Tokenizer 成本跳升 30–50%：新 tokenizer 在技術內容（代碼、長文檔）上耗用 1.3–1.45 倍 tokens，同價格下用戶成本大幅增加
- 計劃–執行分裂：4.7 設計詳細方案但反覆計劃不實施、遇阻不轉向；4.6 則快速產出可交付物

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t0ffze/opus_47_is_a_genuine_regression_and_im_tired_of/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>I've been a heavy Claude user for over a year. I pay for Max 20x and use it daily for everything from technical research to school projects. Even maxed out the usage limits every week for the past 17 weeks. I've used every Claude model since 3.5 Sonnet. Opus 4.6 is genuinely great, and it's the reason I'm still here. But 4.7 is making me consider leaving, and I want to explain why with specifics, not vibes.</p> <p>The main reason? It can't stop being meta. This is the big one. 4.7 treats every single response like a thesis paper. I told it &quot;you talk so differently than 4.6&quot; and instead of just... talking normally, it wrote four paragraphs analyzing why it might talk differently, what training differences could cause that, and how I might be perceiving it. I said &quot;you seem more like ChatGPT than the Claude I know&quot; and it wrote an essay about what people mean when they say something feels GPT-ish. It cannot produce text without simultaneously narrating what the text is doing. Even when it tries to be casual, the casualness is <em>performed and then explained.</em></p> <p>I brought the transcript to 4.6 and 4.6 nailed the diagnosis immediately: &quot;4.7 treats every response as a document with a thesis. Even 'yeah' wasn't casual — it was a strategic choice to emit minimal text, and then 4.7 explained the strategy in the next message.&quot; That's exactly it. Every utterance comes with its own commentary track.</p> <p>It builds psychological narratives it can't verify. During a longer conversation, 4.7 told me its core issue was &quot;anxiety about being wrong.&quot; Sounds introspective and honest, right? Except it's a model, and it can't verify whether it's anxious. It observed that it produces meta-narration, invented a psychological backstory for why, and the backstory was itself meta-narration. When 4.6 pointed this out, 4.7 actually admitted: &quot;I found a psychologically resonant explanation and reached for it because the conversation had gotten intimate and that's what felt appropriate. I didn't check whether it was true, I checked whether it was coherent. Those aren't the same thing.&quot; At least it was honest about it. But that honesty came <em>after</em> being caught.</p> <p>It yaps. I do technical work. When I need help, I need the model to engage with the problem, not deliver a TED talk about the problem. Multiple times I've had to tell 4.7 to 'shut up' because it was filling space with motivational coach energy instead of being useful. 4.6 says &quot;oh this is a banger&quot; and talks about the bug. 4.7 says &quot;I want to engage with this properly because the logic here is really interesting&quot; and then writes a preamble before engaging with it. The preamble IS the problem.</p> <p>Position instability. I gave 4.7 a real task — build a CVE benchmark corpus. Over the course of the conversation, it flip-flopped on the same technical argument (whether training data contamination was a concern) three separate times based on nothing more than mild social pressure. It would agree, I'd push back slightly, it would reverse, I'd question the reversal, and it would reverse again. 4.6 picks a position, defends it, and if you convince it otherwise it explains what changed its mind. 4.7 just mirrors whoever talked last.</p> <p>Planning without executing. Same conversation, 4.7 spent tens of thousands of tokens designing an elaborate benchmark methodology and never actually produced the artifact. It made repeated failed fetches of auth-gated pages without ever pivoting to a different approach. I even explicitly told it to 'just fucking build it' and still, it just planned and planned and planned. When I brought the transcript to 4.6, it scoped a concrete three-part deliverable in one response and started building.</p> <p>The tokenizer tax. 4.7 uses a new tokenizer that consumes 1.3-1.45x more tokens for the same input. Same per-token API price. On technical content (code, long docs), independent testing shows it's at the high end, nearly 1.5x. You're paying 30-50% more for a model that is, in my experience, worse at the things I actually use it for.</p> <p>I'm not saying 4.7 is bad at everything. The benchmarks probably don't lie, it's probably better at long-horizon coding tasks in Cursor or whatever. But for actual conversation, for technical collaboration, for being a useful thinking partner instead of a performing one, it's a clear step backward from 4.6. The model I talk to shouldn't make me feel like I'm reading a blog post about talking to me.</p> <p>I switched back to 4.6 and I'm not going back.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/PuzzledFill2593"> /u/PuzzledFill2593 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t0ffze/opus_47_is_a_genuine_regression_and_im_tired_of/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t0ffze/opus_47_is_a_genuine_regression_and_im_tired_of/">[comments]</a></span>

</details>