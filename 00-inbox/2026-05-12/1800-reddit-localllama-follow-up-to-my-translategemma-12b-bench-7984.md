---
id: inbox_054199c4
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1taxrm6/followup_to_my_translategemma12b_benchmark_post/"
author: "/u/ritis88"
published_at: 2026-05-12T10:41:29+00:00
fetched_at: 2026-05-12T18:00:40.926313+00:00
content_hash: "7984721976ca0f527fc9cbcc8ad887ee772043259a18ac9131e569f88302d9c9"
lang: en
caption_quality: None
raw: true
topics: []
---

# Follow-up to my TranslateGemma-12b benchmark post: human reviewers flagged 71% of the segments automated metrics rated clean

A couple of weeks ago I shared the results of a benchmark here showing TranslateGemma-12b beating frontier general models (Claude Sonnet, GPT-5.4, DeepSeek, Gemini Flash Lite) on subtitle translation across 6 languages. The result was strong enough that we wanted to verify it ourselves - was TranslateGemma really that good, or were the metrics easy on it? So we added a layer of human review. Setup: 21 English subtitle segments from one tutorial video. TranslateGemma's translations into 4 languages (ES, JA, TH, ZH-CN - Korean and Traditional Chinese got dropped). 84 translations total, all chosen because they scored well on both automated metrics. Then we sent every translation to human MQM review. Under the dashboard's own red-flag threshold ( MX ≥ 5 OR CK &lt; 0.70 ): auto-flagged human-flagged (any) human-flagged (Major) ES 0/21 11/21 2/21 JA 0/21 17/21 3/21 TH 0/21 17/21 5/21 ZH-CN 1/21 15/21 3/21 Total 1/84 (1.2%) 60/84 (71%) 13/84 (15%) Of 25 Accuracy-class errors humans found (mistranslation, omission, addition, untranslated), every single one was in the metric-blind quadrant. The metrics caught zero accuracy errors in this sample. Per-language failure modes look quite different: Japanese is the &quot;fluent but wrong meaning&quot; pattern - high COMETKiwi (0.86 mean), reasonable MetricX, but 10 of the 15 total mistranslations in the dataset are in JA. In the original report we'd already seen the same pattern in Claude Sonnet 4.6 on Japanese (TQI 0.5364, MetricX 3.90, COMETKiwi 0.79 - fluent-sounding but drifting from source). Looks like the failure mode generalises across model families on JA. Thai is over-production: 5 Accuracy/Addition errors where the model inserted content not in the source, plus a bunch of punctuation errors driven by English-style periods that Thai doesn't use. Spanish is mostly tone inconsistencies (formal/informal switches), genuinely the easiest of the four. Chinese ZH-CN had 4 Major errors total, including the one segment automated metrics flagged (Style - &quot;unidiomatic collocation and inappropriate style&quot;; humans agreed with the metric on that one). The other 3 Majors: another Style (&quot;literal translation&quot;), an Accuracy/Omission where &quot;store&quot; was dropped and the meaning changed, and a Fluency/Inconsistency where &quot;ticket&quot; was translated inconsistently across segments. Caveat: small audit on one model, one content set, so the numbers are directional rather than definitive. &#32; submitted by &#32; /u/ritis88 [link] &#32; [comments]