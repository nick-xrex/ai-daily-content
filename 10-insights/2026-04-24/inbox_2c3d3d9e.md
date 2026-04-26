---
id: inbox_2c3d3d9e
date: 2026-04-24
source_ref: "[[00-inbox/2026-04-24/1505-simon-willison-llm-0-31-9e52]]"
title: "llm 0.31"
url: https://simonwillison.net/2026/Apr/24/llm/#atom-everything
source: simon-willison
published_at: 2026-04-24T23:35:07+00:00
fetched_at: 2026-04-25T15:10:22.035574+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llm 工具發布 v0.31 版本，新增三項主要功能：(1) 支援 GPT-5.5 模型（`llm -m gpt-5.5`）；(2) 新增 verbosity 選項控制 GPT-5+ 輸出冗長度（低/中/高三檔）；(3) 新增 image_detail 選項細控圖像處理細節度（低/高/自動/原始四種模式，其中原始模式僅限 GPT-5.4 與 5.5）；此外 extra-openai-models.yaml 中的模型現已註冊為非同步調用。"
key_points:
  - "llm v0.31 新增 GPT-5.5 支援，使用 `llm -m gpt-5.5`"
  - "新增 `-o verbosity low|medium|high` 選項控制輸出冗長度，適用 GPT-5+ 模型"
  - "新增 `-o image_detail low|high|auto|original` 選項控制圖像細節度，原始模式限 GPT-5.4/5.5"
tags: [llm-tool, gpt-5-5, cli-utility]
topics: [foundation_models.gpt]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## llm 0.31

llm 工具發布 v0.31 版本，新增三項主要功能：(1) 支援 GPT-5.5 模型（`llm -m gpt-5.5`）；(2) 新增 verbosity 選項控制 GPT-5+ 輸出冗長度（低/中/高三檔）；(3) 新增 image_detail 選項細控圖像處理細節度（低/高/自動/原始四種模式，其中原始模式僅限 GPT-5.4 與 5.5）；此外 extra-openai-models.yaml 中的模型現已註冊為非同步調用。

### 重點
- llm v0.31 新增 GPT-5.5 支援，使用 `llm -m gpt-5.5`
- 新增 `-o verbosity low|medium|high` 選項控制輸出冗長度，適用 GPT-5+ 模型
- 新增 `-o image_detail low|high|auto|original` 選項控制圖像細節度，原始模式限 GPT-5.4/5.5

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/24/llm/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong>Release:</strong> <a href="https://github.com/simonw/llm/releases/tag/0.31">llm 0.31</a></p>
    <blockquote>
<ul>
<li>New GPT-5.5 OpenAI model: <code>llm -m gpt-5.5</code>. <a href="https://github.com/simonw/llm/issues/1418">#1418</a></li>
<li>New option to set the <a href="https://developers.openai.com/cookbook/examples/gpt-5/gpt-5_new_params_and_tools#1-verbosity-parameter">text verbosity level</a> for GPT-5+ OpenAI models: <code>-o verbosity low</code>. Values are <code>low</code>, <code>medium</code>, <code>high</code>.</li>
<li>New option for setting the <a href="https://developers.openai.com/api/docs/guides/images-vision#choose-an-image-detail-level">image detail level</a> used for image attachments to OpenAI models: <code>-o image_detail low</code> - values are <code>low</code>, <code>high</code> and <code>auto</code>, and GPT-5.4 and 5.5 also accept <code>original</code>.</li>
<li>Models listed in <code>extra-openai-models.yaml</code> are now also registered as asynchronous. <a href="https://github.com/simonw/llm/issues/1395">#1395</a></li>
</ul>
</blockquote>
    
        <p>Tags: <a href="https://simonwillison.net/tags/gpt">gpt</a>, <a href="https://simonwillison.net/tags/openai">openai</a>, <a href="https://simonwillison.net/tags/llm">llm</a></p>

</details>