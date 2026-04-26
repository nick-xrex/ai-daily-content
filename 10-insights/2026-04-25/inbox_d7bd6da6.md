---
id: inbox_d7bd6da6
date: 2026-04-25
source_ref: "[[00-inbox/2026-04-25/1505-simon-willison-gpt-5-5-prompting-guide-c196]]"
title: "GPT-5.5 prompting guide"
url: https://simonwillison.net/2026/Apr/25/gpt-5-5-prompting-guide/#atom-everything
source: simon-willison
published_at: 2026-04-25T04:13:36+00:00
fetched_at: 2026-04-25T15:10:22.034852+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 發布 GPT-5.5 官方提示工程指南，揭露三大核心建議：(1) 多步驟任務應在工具調用前發送短的用戶可見更新，避免長時間沉默，Codex 應用已採用此技巧；(2) GPT-5.5 應視為新模型族而非直接替代品，需從最小提示重新優化 reasoning effort、verbosity、tool descriptions 與輸出格式；(3) OpenAI 提供 `$openai-docs migrate` 工具協助遷移，並發布詳細升級指南。"
key_points:
  - "多步驟任務在工具調用前發送短的用戶可見更新，避免看起來當機（Codex 應用已實踐）"
  - "GPT-5.5 是新模型族而非直接替代品，應從最小提示開始重新優化 reasoning、verbosity、工具描述和輸出格式，不應照搬舊提示"
  - "提供 `$openai-docs migrate` 命令和詳細升級指南協助項目遷移至 GPT-5.5"
tags: [gpt-5-5, prompt-engineering, model-migration]
topics: [foundation_models.gpt]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## GPT-5.5 prompting guide

OpenAI 發布 GPT-5.5 官方提示工程指南，揭露三大核心建議：(1) 多步驟任務應在工具調用前發送短的用戶可見更新，避免長時間沉默，Codex 應用已採用此技巧；(2) GPT-5.5 應視為新模型族而非直接替代品，需從最小提示重新優化 reasoning effort、verbosity、tool descriptions 與輸出格式；(3) OpenAI 提供 `$openai-docs migrate` 工具協助遷移，並發布詳細升級指南。

### 重點
- 多步驟任務在工具調用前發送短的用戶可見更新，避免看起來當機（Codex 應用已實踐）
- GPT-5.5 是新模型族而非直接替代品，應從最小提示開始重新優化 reasoning、verbosity、工具描述和輸出格式，不應照搬舊提示
- 提供 `$openai-docs migrate` 命令和詳細升級指南協助項目遷移至 GPT-5.5

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/25/gpt-5-5-prompting-guide/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://developers.openai.com/api/docs/guides/prompt-guidance?model=gpt-5.5">GPT-5.5 prompting guide</a></strong></p>
Now that GPT-5.5 is <a href="https://developers.openai.com/api/docs/models/gpt-5.5">available in the API</a>, OpenAI have released a wealth of useful tips on how best to prompt the new model.</p>
<p>Here's a neat trick they recommend for applications that might spend considerable time thinking before returning a user-visible response:</p>
<pre><code>Before any tool calls for a multi-step task, send a short user-visible update that acknowledges the request and states the first step. Keep it to one or two sentences.
</code></pre>
<p>I've already noticed their Codex app doing this, and it does make longer running tasks feel less like the model has crashed.</p>
<p>OpenAI suggest running the following in Codex to upgrade your existing code using advice embedded in their <code>openai-docs</code> skill:</p>
<pre><code>$openai-docs migrate this project to gpt-5.5
</code></pre>
<p>The upgrade guide the coding agent will follow <a href="https://github.com/openai/skills/blob/724cd511c96593f642bddf13187217aa155d2554/skills/.curated/openai-docs/references/upgrade-guide.md#model-string--light-prompt-rewrite">is this one</a>, which even includes light instructions on how to rewrite prompts to better fit the model.</p>
<p>Also relevant is the <a href="https://developers.openai.com/api/docs/guides/latest-model">Using GPT-5.5 guide</a>, which opens with this warning:</p>
<blockquote>
<p>To get the most out of GPT-5.5, treat it as a new model family to tune for, not a drop-in replacement for <code>gpt-5.2</code> or <code>gpt-5.4</code>. Begin migration with a fresh baseline instead of carrying over every instruction from an older prompt stack. Start with the smallest prompt that preserves the product contract, then tune reasoning effort, verbosity, tool descriptions, and output format against representative examples.</p>
</blockquote>
<p>Interesting to see OpenAI recommend starting from scratch rather than trusting that existing prompts optimized for previous models will continue to work effectively with GPT-5.5.


    <p>Tags: <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/openai">openai</a>, <a href="https://simonwillison.net/tags/prompt-engineering">prompt-engineering</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/gpt">gpt</a></p>

</details>