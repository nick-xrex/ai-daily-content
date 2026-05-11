---
id: inbox_ac29a564
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_ac29a564]]"
title: "Attention - Opus 4.7 is english only. USing foreign languages (here German) burns tokens"
url: https://www.reddit.com/r/ClaudeAI/comments/1t8xtcf/attention_opus_47_is_english_only_using_foreign/
source: reddit-claudeai
published_at: 2026-05-10T05:21:27+00:00
fetched_at: 2026-05-11T02:25:28.920538+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Pro 訂閱用戶發現 Opus 4.7 在德語提示中的 token 消耗異常高。使用德文詢問股票預測 + 圖表分析 + Excel 輸出時，Opus 4.7 在數秒內耗盡整個會話 token 限額（100%），而 Opus 4.6 耗時約 5 分鐘消耗 33%、Sonnet 消耗 28%。根本原因：德語複合詞（如「Aktienmarktanalyse」vs「stock market analysis」）、變音符（umlaut）、訓練數據覆蓋不足，導致 tokenization 成本約為英文的 1.5–2 倍。Claude 會話限額是以 token 計，非訊息數計，故德文工作流消耗額度更快。"
key_points:
  - "德語文本的 token 成本為英文的 1.5–2 倍（複合詞、變音符、訓練數據不足）"
  - "相同工作流在 Opus 4.7 中：英文 37%、德文 100%；Opus 4.6 分別為 33% 與 100%"
  - "Claude 會話限額是 token 制而非訊息制；非英文工作流會更快消耗配額"
tags: [multilingual-cost, tokenization, opus-4.7]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Attention - Opus 4.7 is english only. USing foreign languages (here German) burns tokens

Pro 訂閱用戶發現 Opus 4.7 在德語提示中的 token 消耗異常高。使用德文詢問股票預測 + 圖表分析 + Excel 輸出時，Opus 4.7 在數秒內耗盡整個會話 token 限額（100%），而 Opus 4.6 耗時約 5 分鐘消耗 33%、Sonnet 消耗 28%。根本原因：德語複合詞（如「Aktienmarktanalyse」vs「stock market analysis」）、變音符（umlaut）、訓練數據覆蓋不足，導致 tokenization 成本約為英文的 1.5–2 倍。Claude 會話限額是以 token 計，非訊息數計，故德文工作流消耗額度更快。

### 重點
- 德語文本的 token 成本為英文的 1.5–2 倍（複合詞、變音符、訓練數據不足）
- 相同工作流在 Opus 4.7 中：英文 37%、德文 100%；Opus 4.6 分別為 33% 與 100%
- Claude 會話限額是 token 制而非訊息制；非英文工作流會更快消耗配額

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t8xtcf/attention_opus_47_is_english_only_using_foreign/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Attention - Opus 4.7 is english only. USing foreign languages (here German) burns tokens

I am a pro subscriber. I developped a not too sophisticated prompt in German. Then I wanted to to a quality check... Sonnet just did the job. Opis 4.6 did the job but two graphs in the output were incomplete. Opus 4.7 extended... I used a fresh session, 0% and bang it consumed the whole session tokens in seconds where the other models took around 5 minutes to complete the task. I asked it... On German consuming your whole session limit. This one's real and not a bug per se, it's how tokenization works: Claude tokenizes text. English text averages roughly 1 token per 0.75 words. German averages closer to 1 token per 0.5 words — sometimes worse — because of compound nouns (&quot;Aktienmarktanalyse&quot; tokenizes into more pieces than &quot;stock market analysis&quot;), umlauts, and less training-data coverage. For the same semantic content, a German prompt + German response can consume 1.5× to 2× the tokens of the English equivalent. Combined with tool calls, web searches, and a long Excel-building output, that adds up fast. Session limits on Claude.ai are token-based, not message-based. So yes — running this exact workflow in German legitimately eats more of your quota. Workarounds: prompt in German but ask for the response/output in English (the spreadsheet labels could stay English while we converse in German), or ask me to be terser. Anthropic is aware of the multilingual token-cost issue but it's a structural property of the tokenizer, not something I can fix on my end. The prompt: Please provide me with a forecast for the stocks of The Trade Desk, Coreweave, and Cloudflare for the next 6 months. Also analyze the impact of earnings misses and fundamental data such as margin growth and the market’s overreaction to minor corrections. The result should be an Excel spreadsheet. Create a chart covering the last 24 months and a forecast for the next 6 months, then a chart for the last 30 days and a forecast for the next 30 days. Then do the same again for the last 7 days and the next 7 days. Also include the options (calls and puts) on the three stocks mentioned, any short interest, and the positioning of major investors in the 13F filings. In english opus 4.7 extended consumes 37% of the session, 4.6 did 33% and Sonnet around 28%. In German.. 100% in seconds. The other models I could even feed with 3 page prompts, those which materialize as text file when pasting them... this is completely ridiculous. &#32; submitted by &#32; /u/WickOfDeath [link] &#32; [comments]

</details>