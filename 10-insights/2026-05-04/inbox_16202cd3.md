---
id: inbox_16202cd3
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_16202cd3]]"
title: "Most of my Claude usage was on work that didn&#39;t need Claude. Cut my bill 60x on bulk tasks with a tiny side model."
url: https://www.reddit.com/r/ClaudeAI/comments/1t3elab/most_of_my_claude_usage_was_on_work_that_didnt/
source: reddit-claudeai
published_at: 2026-05-04T11:12:10+00:00
fetched_at: 2026-05-04T14:33:05.557412+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者發現 Claude 大量使用被浪費在 JSON 格式化、字段提取、文件分類等機械任務，決定將其卸載給廉價小模型解決。他透過建立工具搭配 CLAUDE.md 的負面框架規則（deny list：「不要用 Claude 做 X」），將 217 個機械任務轉移給 DeepSeek V4 Flash，3 週內成本僅 $0.41，相比 Sonnet 的 ~$7 節省 60 倍。關鍵發現是負面框架遵循率遠高於正面框架（後者被忽視率 30%），且此方案採用監督型架構（無工具調用、無自動化鏈），延遲 3-25 秒，輸出由人類審核。"
key_points:
  - "DeepSeek V4 Flash 於 217 個機械任務上的成本為 $0.41，對比 Claude Sonnet 的 ~$7 節省 60 倍"
  - "負面框架 CLAUDE.md 規則（deny list）的遵循率遠高於正面框架（30% vs 0% 忽視率）"
  - "監督型工作者架構：無工具調用、無文件訪問、無鏈式推理，延遲 3-25 秒，必須人工審核輸出"
tags: [cost-optimization, multi-model-routing, deepseek-v4-flash, prompt-engineering, mcp]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Most of my Claude usage was on work that didn't need Claude. Cut my bill 60x on bulk tasks with a tiny side model.

使用者發現 Claude 大量使用被浪費在 JSON 格式化、字段提取、文件分類等機械任務，決定將其卸載給廉價小模型解決。他透過建立工具搭配 CLAUDE.md 的負面框架規則（deny list：「不要用 Claude 做 X」），將 217 個機械任務轉移給 DeepSeek V4 Flash，3 週內成本僅 $0.41，相比 Sonnet 的 ~$7 節省 60 倍。關鍵發現是負面框架遵循率遠高於正面框架（後者被忽視率 30%），且此方案採用監督型架構（無工具調用、無自動化鏈），延遲 3-25 秒，輸出由人類審核。

### 重點
- DeepSeek V4 Flash 於 217 個機械任務上的成本為 $0.41，對比 Claude Sonnet 的 ~$7 節省 60 倍
- 負面框架 CLAUDE.md 規則（deny list）的遵循率遠高於正面框架（30% vs 0% 忽視率）
- 監督型工作者架構：無工具調用、無文件訪問、無鏈式推理，延遲 3-25 秒，必須人工審核輸出

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t3elab/most_of_my_claude_usage_was_on_work_that_didnt/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Most of my Claude usage was on work that didn't need Claude. Cut my bill 60x on bulk tasks with a tiny side model.

<!-- SC_OFF --><div class="md"><p>I looked at what was actually eating my Claude usage and it was embarrassing. Classifying files. Reformatting json. Pulling fields out of text. Summarizing docs I was going to skim anyway. None of that needed Sonnet. All of it cost the same as the work that did.</p> <p>Tried the obvious fixes first. Switching to Haiku for simple stuff (still wasteful at volume). Tighter prompts (helps a little). /compact (delays the problem). None of it changed the shape of the spend.</p> <p>What actually worked: a small cheap model running as a side worker, with one rule in CLAUDE.md telling Claude not to do the mechanical stuff itself.</p> <p>The setup is one tool. Send it text, get text back. Claude calls it for the bounded mechanical work I'd review anyway. Default model is DeepSeek V4 Flash because it's cheap and has 1M context, but the endpoint is one config line and works with anything openai-compatible (local ollama, vllm, lm studio).</p> <p><strong>3 weeks of real usage:</strong></p> <ul> <li>217 mechanical calls offloaded</li> <li>DeepSeek total spend: $0.41</li> <li>Same workload on Sonnet would have been roughly $7</li> </ul> <p>The CLAUDE.md rule that actually works is negative framing. Not &quot;use deepseek for X&quot; but &quot;do NOT use Claude for: json formatting, field extraction, file classification, summarization you will review anyway.&quot; Positive framing got ignored maybe 30% of the time. Deny list catches it.</p> <p>It's a supervised worker, not an agent. No tool calls, no file access, no chains. Latency 3-25s. You review the output. That's the whole shape.</p> <p>Repo with setup steps: <a href="https://github.com/arizen-dev/deepseek-mcp">https://github.com/arizen-dev/deepseek-mcp</a> (MIT, Python 3.10+)</p> <p>Happy to answer questions about the routing rules or the model choice.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/petburiraja"> /u/petburiraja </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3elab/most_of_my_claude_usage_was_on_work_that_didnt/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3elab/most_of_my_claude_usage_was_on_work_that_didnt/">[comments]</a></span>

</details>