---
id: inbox_1e717c2f
date: 2026-04-16
source_ref: "[[00-inbox/.../inbox_1e717c2f]]"
title: "llm-anthropic 0.25"
url: https://simonwillison.net/2026/Apr/16/llm-anthropic/#atom-everything
source: (resumed)
published_at: 2026-04-16T20:37:12+00:00
fetched_at: 2026-04-21T02:37:41.613454+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llm-anthropic 0.25 版本新增對 Claude Opus 4.7 的支持，該模型首次支持 thinking_effort 參數的「xhigh」級別，允許進行更高深度的推理。同時引入了 thinking_display 和 thinking_adaptive 兩個新布爾選項，讓開發者控制內部推理過程的顯示方式。預設 max_tokens 提升至每個模型允許的最大值，提供更大靈活性。此版本並移除了過時的 structured-outputs-2025-11-13 beta 頭支援，簡化 API 集成。這些改進增強了 Anthropic API 與最新 Claude 模型功能的兼容性。"
key_points:
  - "新增 claude-opus-4.7 模型支持，包含 thinking_effort: xhigh 級別用於深度推理"
  - "新增 thinking_display 和 thinking_adaptive 選項以控制推理過程顯示和自適應行為"
  - "預設 max_tokens 提升至模型允許最大值，移除過時 beta 頭依賴"
tags: [claude-opus-4.7, thinking-model, llm-anthropic, extended-reasoning, api-update]
topics: [foundation_models.claude]
importance: 4
novelty: 4
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-anthropic 0.25

llm-anthropic 0.25 版本新增對 Claude Opus 4.7 的支持，該模型首次支持 thinking_effort 參數的「xhigh」級別，允許進行更高深度的推理。同時引入了 thinking_display 和 thinking_adaptive 兩個新布爾選項，讓開發者控制內部推理過程的顯示方式。預設 max_tokens 提升至每個模型允許的最大值，提供更大靈活性。此版本並移除了過時的 structured-outputs-2025-11-13 beta 頭支援，簡化 API 集成。這些改進增強了 Anthropic API 與最新 Claude 模型功能的兼容性。

### 重點
- 新增 claude-opus-4.7 模型支持，包含 thinking_effort: xhigh 級別用於深度推理
- 新增 thinking_display 和 thinking_adaptive 選項以控制推理過程顯示和自適應行為
- 預設 max_tokens 提升至模型允許最大值，移除過時 beta 頭依賴

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/16/llm-anthropic/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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
