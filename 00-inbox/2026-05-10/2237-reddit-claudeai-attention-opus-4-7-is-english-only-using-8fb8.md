---
id: inbox_ac29a564
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t8xtcf/attention_opus_47_is_english_only_using_foreign/"
author: "/u/WickOfDeath"
published_at: 2026-05-10T05:21:27+00:00
fetched_at: 2026-05-10T22:37:16.868376+00:00
content_hash: "8fb8a19bd1c84c42d4d6a05e77cc1dcdf2cddb2faa9ce9a3c3f00ef839e09535"
lang: en
caption_quality: None
raw: true
topics: []
---

# Attention - Opus 4.7 is english only. USing foreign languages (here German) burns tokens

I am a pro subscriber. I developped a not too sophisticated prompt in German. Then I wanted to to a quality check... Sonnet just did the job. Opis 4.6 did the job but two graphs in the output were incomplete. Opus 4.7 extended... I used a fresh session, 0% and bang it consumed the whole session tokens in seconds where the other models took around 5 minutes to complete the task. I asked it... On German consuming your whole session limit. This one's real and not a bug per se, it's how tokenization works: Claude tokenizes text. English text averages roughly 1 token per 0.75 words. German averages closer to 1 token per 0.5 words — sometimes worse — because of compound nouns (&quot;Aktienmarktanalyse&quot; tokenizes into more pieces than &quot;stock market analysis&quot;), umlauts, and less training-data coverage. For the same semantic content, a German prompt + German response can consume 1.5× to 2× the tokens of the English equivalent. Combined with tool calls, web searches, and a long Excel-building output, that adds up fast. Session limits on Claude.ai are token-based, not message-based. So yes — running this exact workflow in German legitimately eats more of your quota. Workarounds: prompt in German but ask for the response/output in English (the spreadsheet labels could stay English while we converse in German), or ask me to be terser. Anthropic is aware of the multilingual token-cost issue but it's a structural property of the tokenizer, not something I can fix on my end. The prompt: Please provide me with a forecast for the stocks of The Trade Desk, Coreweave, and Cloudflare for the next 6 months. Also analyze the impact of earnings misses and fundamental data such as margin growth and the market’s overreaction to minor corrections. The result should be an Excel spreadsheet. Create a chart covering the last 24 months and a forecast for the next 6 months, then a chart for the last 30 days and a forecast for the next 30 days. Then do the same again for the last 7 days and the next 7 days. Also include the options (calls and puts) on the three stocks mentioned, any short interest, and the positioning of major investors in the 13F filings. In english opus 4.7 extended consumes 37% of the session, 4.6 did 33% and Sonnet around 28%. In German.. 100% in seconds. The other models I could even feed with 3 page prompts, those which materialize as text file when pasting them... this is completely ridiculous. &#32; submitted by &#32; /u/WickOfDeath [link] &#32; [comments]