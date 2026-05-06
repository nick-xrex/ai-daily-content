---
id: inbox_20b35d44
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/1002-simon-willison-llm-echo-0-5a0-d0a7]]"
title: "llm-echo 0.5a0"
url: https://simonwillison.net/2026/May/5/llm-echo/#atom-everything
source: simon-willison
published_at: 2026-05-05T01:31:54+00:00
fetched_at: 2026-05-06T10:08:20.878975+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llm-echo 0.5a0 發布，新增 `-o thinking 1` 選項支援 LLM 0.32a0+ 的 reasoning block 輸出，允許開發者在測試中模擬 LLM 推理過程，方便自動化測試編寫，可執行 `uvx --with llm==0.32a1 --with llm-echo==0.5a0 llm -m echo hi -o thinking 1` 獲得假推理結果。"
key_points:
  - "llm-echo 0.5a0 新增 `-o thinking 1` 選項支援 reasoning block，相容 LLM 0.32a0+"
  - "輸出假推理到 stderr 並返回 JSON 回應，用於自動化測試的假模型工具"
  - "簡化 LLM thinking 特性的測試流程"
tags: [llm, testing, mock-model, echo]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-echo 0.5a0

llm-echo 0.5a0 發布，新增 `-o thinking 1` 選項支援 LLM 0.32a0+ 的 reasoning block 輸出，允許開發者在測試中模擬 LLM 推理過程，方便自動化測試編寫，可執行 `uvx --with llm==0.32a1 --with llm-echo==0.5a0 llm -m echo hi -o thinking 1` 獲得假推理結果。

### 重點
- llm-echo 0.5a0 新增 `-o thinking 1` 選項支援 reasoning block，相容 LLM 0.32a0+
- 輸出假推理到 stderr 並返回 JSON 回應，用於自動化測試的假模型工具
- 簡化 LLM thinking 特性的測試流程

**原文：** [simon-willison](https://simonwillison.net/2026/May/5/llm-echo/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong>Release:</strong> <a href="https://github.com/simonw/llm-echo/releases/tag/0.5a0">llm-echo 0.5a0</a></p>
        <blockquote>
<ul>
<li>New <code>-o thinking 1</code> option to help test against <a href="https://llm.datasette.io/en/latest/changelog.html#a0-2026-04-28">LLM 0.32a0</a> and higher.</li>
</ul>
</blockquote>
<p>This plugin provides a fake model called "echo" for LLM which doesn't run an LLM at all - it's useful for writing automated tests. You can now do this:</p>
<pre><code>uvx --with llm==0.32a1 --with llm-echo==0.5a0 llm -m echo hi -o thinking 1
</code></pre>
<p>This will fake a reasoning block to standard error before returning JSON echoing the prompt.</p>
    
    
        <p>Tags: <a href="https://simonwillison.net/tags/llm">llm</a></p>

</details>