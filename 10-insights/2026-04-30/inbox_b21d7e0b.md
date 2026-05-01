---
id: inbox_b21d7e0b
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-claudeai-open-source-we-built-a-local-code-search-deb1]]"
title: "[Open Source] We built a local code search MCP for Claude Code that uses ~98% fewer tokens than grep+read"
url: https://www.reddit.com/r/ClaudeAI/comments/1szvo7t/open_source_we_built_a_local_code_search_mcp_for/
source: reddit-claudeai
published_at: 2026-04-30T13:11:07+00:00
fetched_at: 2026-05-01T13:35:43.429490+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開源專案 Semble 推出針對 Claude Code 的本地代碼搜尋 MCP 伺服器，解決傳統 grep+read 流程耗 token 過多的問題。核心指標：(1) Token 效率——相比 grep+read 節省 98%；(2) 性能——索引 250ms、查詢 1.5ms，完全 CPU 執行無需 GPU；(3) 檢索質量 NDCG@10=0.854，接近最佳 transformer hybrid 方案且快 200 倍。採用靜態 embedding + BM25 + 代碼優化 reranker 的混合方案，完全本地運行無需 API 密鑰。基準涵蓋 19 種語言、63 個開源代碼庫。"
key_points:
  - "Token 節省 98%：搜索代碼片段的成本從傳統流程降至 2%，直接降低 Claude Code 使用成本"
  - "毫秒級性能 + 無外部依賴：索引 ~250ms、查詢 ~1.5ms，全在本地 CPU 執行，無 GPU/API 密鑰需求"
  - "混合檢索架構可複用：靜態 embedding + BM25 + 代碼優化 reranker 的組合在 19 語言、63 代碼庫上驗證有效，質量相當於最佳 transformer 方案"
tags: [mcp, code-search, claude-code, token-efficiency, open-source]
topics: [agents.mcp]
importance: 4
novelty: 5
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## [Open Source] We built a local code search MCP for Claude Code that uses ~98% fewer tokens than grep+read

開源專案 Semble 推出針對 Claude Code 的本地代碼搜尋 MCP 伺服器，解決傳統 grep+read 流程耗 token 過多的問題。核心指標：(1) Token 效率——相比 grep+read 節省 98%；(2) 性能——索引 250ms、查詢 1.5ms，完全 CPU 執行無需 GPU；(3) 檢索質量 NDCG@10=0.854，接近最佳 transformer hybrid 方案且快 200 倍。採用靜態 embedding + BM25 + 代碼優化 reranker 的混合方案，完全本地運行無需 API 密鑰。基準涵蓋 19 種語言、63 個開源代碼庫。

### 重點
- Token 節省 98%：搜索代碼片段的成本從傳統流程降至 2%，直接降低 Claude Code 使用成本
- 毫秒級性能 + 無外部依賴：索引 ~250ms、查詢 ~1.5ms，全在本地 CPU 執行，無 GPU/API 密鑰需求
- 混合檢索架構可複用：靜態 embedding + BM25 + 代碼優化 reranker 的組合在 19 語言、63 代碼庫上驗證有效，質量相當於最佳 transformer 方案

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1szvo7t/open_source_we_built_a_local_code_search_mcp_for/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1szvo7t/open_source_we_built_a_local_code_search_mcp_for/"> <img alt="[Open Source] We built a local code search MCP for Claude Code that uses ~98% fewer tokens than grep+read" src="https://preview.redd.it/n6lg2gbstbyg1.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=d4018017470ab0bb061b7095fc5e06ed0dfcb0e9" title="[Open Source] We built a local code search MCP for Claude Code that uses ~98% fewer tokens than grep+read" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Working on large codebases with Claude Code, we kept running into the same issue: when Claude looks for relevant code, it falls back to grep, reading full files, or launching multiple subagents. This burns through tokens, and often misses the relevant code. There are some existing solutions (that we also benchmarked against), but they all had issues (too slow, needs API keys, quality not good enough, etc).</p> <p>We built <a href="https://github.com/MinishLab/semble">Semble</a> to fix this. It's a local MCP server that gives Claude Code high quality code search: instead of reading files to find what's relevant, it returns only the matching chunks. On average it uses <strong>98% fewer tokens</strong> than grep+read, while indexing repos we benchmarked in <strong>~250ms</strong> and answering queries in <strong>~1.5ms</strong>, all on CPU. Note that the indexing time scales linearly with the amount of chunks, so large codebases may take several seconds. It makes use of a combination of static embeddings, BM25, and a code-optimized reranking stack. </p> <p><strong>Install:</strong></p> <pre><code>claude mcp add semble -s user -- uvx --from &quot;semble[mcp]&quot; semble </code></pre> <p>Once installed, Claude Code can search any repo directly (both local and remote). It's fully local: <strong>no API keys, no GPU, no heavy dependencies</strong>.</p> <p>We've run extensive benchmarks for Semble, and quality-wise it reaches 99% of the performance of the best transformer hybrid we tested (NDCG@10 of 0.854), while being ~200x faster. We've also compared it directly to existing methods such as grepai, probe, colgrep, and more. The benchmark covers ~1250 query/document pairs in 19 programming languages from 63 popular codebases. Let me know if you have any feedback!</p> <p><strong>Links:</strong></p> <ul> <li>Semble: <a href="https://github.com/MinishLab/semble">https://github.com/MinishLab/semble</a></li> <li>Benchmarks: <a href="https://github.com/MinishLab/semble/tree/main/benchmarks">https://github.com/MinishLab/semble/tree/main/benchmarks</a></li> </ul> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Pringled101"> /u/Pringled101 </a> <br /> <span><a href="https://i.redd.it/n6lg2gbstbyg1.png">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1szvo7t/open_source_we_built_a_local_code_search_mcp_for/">[comments]</a></span> </td></tr></table>

</details>