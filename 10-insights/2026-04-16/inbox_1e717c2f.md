---
id: inbox_1e717c2f
date: 2026-04-16
source_ref: "[[00-inbox/.../inbox_1e717c2f]]"
title: "llm-anthropic 0.25"
url: https://simonwillison.net/2026/Apr/16/llm-anthropic/#atom-everything
source: simon-willison
published_at: 2026-04-16T20:37:12+00:00
fetched_at: 2026-04-21T03:13:26.218973+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llm-anthropic 0.25 發布，新增對 Claude Opus 4.7 的支援，該新模型支援 thinking_effort: xhigh 極限思考模式。新增 thinking_display 和 thinking_adaptive 布林選項，用於控制思考過程的顯示，其中 thinking_display 的摘要輸出目前僅在 JSON 輸出或 JSON 日誌中提供。預設 max_tokens 參數已增加到每個模型允許的最大值。移除了舊版本保留的過時 structured-outputs 測試版標頭。"
key_points:
  - "新增 Claude Opus 4.7 模型支援，含 thinking_effort: xhigh 極限思考模式"
  - "新增 thinking_display 和 thinking_adaptive 選項控制思考過程顯示"
  - "預設 max_tokens 調整為每個模型最大允許值，移除過時 beta 標頭"
tags: [claude-opus-4.7, thinking-mode, anthropic-sdk, llm-cli]
topics: [foundation_models.claude]
importance: 4
novelty: 4
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-anthropic 0.25

llm-anthropic 0.25 發布，新增對 Claude Opus 4.7 的支援，該新模型支援 thinking_effort: xhigh 極限思考模式。新增 thinking_display 和 thinking_adaptive 布林選項，用於控制思考過程的顯示，其中 thinking_display 的摘要輸出目前僅在 JSON 輸出或 JSON 日誌中提供。預設 max_tokens 參數已增加到每個模型允許的最大值。移除了舊版本保留的過時 structured-outputs 測試版標頭。

### 重點
- 新增 Claude Opus 4.7 模型支援，含 thinking_effort: xhigh 極限思考模式
- 新增 thinking_display 和 thinking_adaptive 選項控制思考過程顯示
- 預設 max_tokens 調整為每個模型最大允許值，移除過時 beta 標頭

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/16/llm-anthropic/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# llm-anthropic 0.25

<p><strong>Release:</strong> <a href="https://github.com/simonw/llm-anthropic/releases/tag/0.25">llm-anthropic 0.25</a></p>
    <blockquote>
<ul>
<li>New model: <code>claude-opus-4.7</code>, which supports <code>thinking_effort</code>: <code>xhigh</code>. #66</li>
<li>New <code>thinking_display</code> and <code>thinking_adaptive</code> boolean options. <code>thinking_display</code> summarized output is currently only available in JSON output or JSON logs.</li>
<li>Increased default <code>max_tokens</code> to the maximum allowed for each model.</li>
<li>No longer uses obsolete <code>structured-outputs-2025-11-13</code> beta header for older models.</li>
</ul>
</blockquote>
    
        <p>Tags: <a href="https://simonwillison.net/tags/llm">llm</a>, <a href="https://simonwillison.net/tags/anthropic">anthropic</a>, <a href="https://simonwillison.net/tags/claude">claude</a></p>

</details>