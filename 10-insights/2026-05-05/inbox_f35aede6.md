---
id: inbox_f35aede6
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/1002-simon-willison-datasette-llm-0-1a7-4a7e]]"
title: "datasette-llm 0.1a7"
url: https://simonwillison.net/2026/May/5/datasette-llm/#atom-everything
source: simon-willison
published_at: 2026-05-05T01:56:55+00:00
fetched_at: 2026-05-06T10:08:20.877216+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-llm 發布 0.1a7，新增為特定 LLM 配置預設選項的機制，允許使用者對所有 enrichment 操作統一指定模型和溫度等參數，簡化 Datasette 內 LLM 外掛的配置流程。"
key_points:
  - "datasette-llm 0.1a7 支援模型預設選項配置（如溫度設定 0.5）"
  - "適用於 datasette-enrichments-llm 外掛的 enrichment 操作"
  - "提升 Datasette 對 LLM 外掛的支援機制"
tags: [datasette, llm, configuration, plugin]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-llm 0.1a7

datasette-llm 發布 0.1a7，新增為特定 LLM 配置預設選項的機制，允許使用者對所有 enrichment 操作統一指定模型和溫度等參數，簡化 Datasette 內 LLM 外掛的配置流程。

### 重點
- datasette-llm 0.1a7 支援模型預設選項配置（如溫度設定 0.5）
- 適用於 datasette-enrichments-llm 外掛的 enrichment 操作
- 提升 Datasette 對 LLM 外掛的支援機制

**原文：** [simon-willison](https://simonwillison.net/2026/May/5/datasette-llm/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong>Release:</strong> <a href="https://github.com/datasette/datasette-llm/releases/tag/0.1a7">datasette-llm 0.1a7</a></p>
        <blockquote>
<ul>
<li>Mechanism for <a href="https://github.com/datasette/datasette-llm/blob/main/README.md#configuration">configuring default options</a> for specific models.</li>
</ul>
</blockquote>
<p>Part of Datasette's evolving support mechanism for plugins that use LLMs. It's now possible to configure a model with default options, e.g. to say all <a href="https://github.com/datasette/datasette-enrichments-llm">enrichment</a> operations should use a specific model with temperature set to 0.5.</p>
    
    
        <p>Tags: <a href="https://simonwillison.net/tags/llm">llm</a>, <a href="https://simonwillison.net/tags/datasette">datasette</a></p>

</details>