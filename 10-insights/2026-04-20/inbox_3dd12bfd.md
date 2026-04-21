---
id: inbox_3dd12bfd
date: 2026-04-20
source_ref: "[[00-inbox/.../inbox_3dd12bfd]]"
title: "Claude Token Counter, now with model comparisons"
url: https://simonwillison.net/2026/Apr/20/claude-token-counts/#atom-everything
source: simon-willison
published_at: 2026-04-20T00:50:45+00:00
fetched_at: 2026-04-21T03:11:17.625237+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 升級 Claude Token Counter 工具，支持跨模型 token 計數對比。Claude Opus 4.7 採用新 tokenizer，輸入相同內容時 token 數增加 1.0–1.46 倍（官方公示 1.0–1.35 倍）；由於定價與 4.6 相同（輸入 $5/百萬 token），預期實際成本增加約 40%。Opus 4.7 支持更高分辨率圖像（最多 2,576 像素、~3.75 百萬像素），相比前代增加 3 倍。測試表明高分辨率圖像 token 成本增加 3.01 倍主要源於分辨率支持能力；低分辨率圖像成本基本相當；PDF 文檔增加倍數僅 1.08 倍，遠低於原始文本。"
key_points:
  - "Opus 4.7 tokenizer 導致相同輸入增加 1.0–1.46× token，定價相同但預期成本升高約 40%"
  - "Opus 4.7 支持最高 2,576 像素/3.75 百萬像素圖像，較前代增加 3 倍；3.01× token 成本增加仅因分辨率能力，實際處理成本接近"
  - "Token 增幅因內容類型異差：文本 1.46×、高分辨率圖像 3.01×、PDF 1.08×，說明新 tokenizer 對不同媒體影響不一"
tags: [token-counting, claude-pricing, opus-4-7, tokenizer-changes, cost-analysis]
topics: [foundation_models.claude]
importance: 4
novelty: 4
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Token Counter, now with model comparisons

Simon Willison 升級 Claude Token Counter 工具，支持跨模型 token 計數對比。Claude Opus 4.7 採用新 tokenizer，輸入相同內容時 token 數增加 1.0–1.46 倍（官方公示 1.0–1.35 倍）；由於定價與 4.6 相同（輸入 $5/百萬 token），預期實際成本增加約 40%。Opus 4.7 支持更高分辨率圖像（最多 2,576 像素、~3.75 百萬像素），相比前代增加 3 倍。測試表明高分辨率圖像 token 成本增加 3.01 倍主要源於分辨率支持能力；低分辨率圖像成本基本相當；PDF 文檔增加倍數僅 1.08 倍，遠低於原始文本。

### 重點
- Opus 4.7 tokenizer 導致相同輸入增加 1.0–1.46× token，定價相同但預期成本升高約 40%
- Opus 4.7 支持最高 2,576 像素/3.75 百萬像素圖像，較前代增加 3 倍；3.01× token 成本增加仅因分辨率能力，實際處理成本接近
- Token 增幅因內容類型異差：文本 1.46×、高分辨率圖像 3.01×、PDF 1.08×，說明新 tokenizer 對不同媒體影響不一

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/20/claude-token-counts/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Claude Token Counter, now with model comparisons

<p><strong><a href="https://tools.simonwillison.net/claude-token-counter">Claude Token Counter, now with model comparisons</a></strong></p>
I <a href="https://github.com/simonw/tools/pull/269">upgraded</a> my Claude Token Counter tool to add the ability to run the same count against different models in order to compare them.</p>
<p>As far as I can tell Claude Opus 4.7 is the first model to change the tokenizer, so it's only worth running comparisons between 4.7 and 4.6. The Claude <a href="https://platform.claude.com/docs/en/build-with-claude/token-counting">token counting API</a> accepts any Claude model ID though so I've included options for all four of the notable current models (Opus 4.7 and 4.6, Sonnet 4.6, and Haiku 4.5).</p>
<p>In the Opus 4.7 announcement <a href="https://www.anthropic.com/news/claude-opus-4-7#migrating-from-opus-46-to-opus-47">Anthropic said</a>:</p>
<blockquote>
<p>Opus 4.7 uses an updated tokenizer that improves how the model processes text. The tradeoff is that the same input can map to more tokens—roughly 1.0–1.35× depending on the content type.</p>
</blockquote>
<p>I pasted the <a href="https://github.com/simonw/research/blob/2cf912666ba08ef0c00a1b51ee07c9a8e64579ef/extract-system-prompts/claude-opus-4-7.md?plain=1">Opus 4.7 system prompt</a> into the token counting tool and found that the Opus 4.7 tokenizer used 1.46x the number of tokens as Opus 4.6.</p>
<p><img alt="Screenshot of a token comparison tool. Models to compare: claude-opus-4-7 (checked), claude-opus-4-6 (checked), claude-opus-4-5, claude-sonnet-4-6, claude-haiku-4-5. Note: &quot;These models share the same tokenizer&quot;. Blue &quot;Count Tokens&quot; button. Results table — Model | Tokens | vs. lowest. claude-opus-4-7: 7,335 tokens, 1.46x (yellow badge). claude-opus-4-6: 5,039 tokens, 1.00x (green badge)." src="https://static.simonwillison.net/static/2026/claude-token-count.jpg" /></p>
<p>Opus 4.7 uses the same pricing is Opus 4.6 - $5 per million input tokens and $25 per million output tokens - but this token inflation means we can expect it to be around 40% more expensive.</p>
<p>The token counter tool also accepts images. Opus 4.7 has improved image support, described like this:</p>
<blockquote>
<p>Opus 4.7 has better vision for high-resolution images: it can accept images up to 2,576 pixels on the long edge (~3.75 megapixels), more than three times as many as prior Claude models.</p>
</blockquote>
<p>I tried counting tokens for a 3456x2234 pixel 3.7MB PNG and got an even bigger increase in token counts - 3.01x times the number of tokens for 4.7 compared to 4.6:</p>
<p><img alt="Same UI, this time with an uploaded screenshot PNG image. claude-opus-4-7: 4,744 tokens, 3.01x (yellow badge). claude-opus-4-6: 1,578 tokens, 1.00x (green badge)." src="https://static.simonwillison.net/static/2026/claude-token-count-image.jpg" /></p>
<p><strong>Update</strong>: That 3x increase for images is <em>entirely</em> due to Opus 4.7 being able to handle higher resolutions. I tried that again with a 682x318 pixel image and it took 314 tokens with Opus 4.7 and 310 with Opus 4.6, so effectively the same cost.</p>
<p><strong>Update 2</strong>: I tried a 15MB, 30 page text-heavy PDF and Opus 4.7 reported 60,934   tokens while 4.6 reported 56,482 - that's a 1.08x multiplier, significantly lower than the multiplier I got for raw text.


    <p>Tags: <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/anthropic">anthropic</a>, <a href="https://simonwillison.net/tags/claude">claude</a>, <a href="https://simonwillison.net/tags/llm-pricing">llm-pricing</a>, <a href="https://simonwillison.net/tags/tokenization">tokenization</a></p>

</details>