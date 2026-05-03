---
id: inbox_6035c8bd
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-claudeai-i-reverse-engineered-the-perplexity-app-8844]]"
title: "I reverse-engineered the Perplexity app and built an MCP that turns your Perplexity/Comet account into a Claude MCP, so Claude can search like crazy and read 200+ sources in one answer with your personal account subscription without API product needed. [Experiment - Educational Purpose]"
url: https://www.reddit.com/r/ClaudeAI/comments/1t1pdqc/i_reverseengineered_the_perplexity_app_and_built/
source: reddit-claudeai
published_at: 2026-05-02T13:05:38+00:00
fetched_at: 2026-05-03T02:05:03.126193+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者反向工程 Perplexity 應用，構建了一個 MCP（模型上下文協議）整合模組，讓 Claude 可直接調用 Perplexity 的搜索引擎功能。透過此 MCP，Claude 能在單一回答中搜索並聚合來自 200+ 信息源的內容，同時利用用戶個人的 Perplexity 訂閱權限無需額外購買搜索 API。項目已開源於 GitHub (VSCode-Perplexity-MCP) 並附有 YouTube 演示。"
key_points:
  - "反向工程 Perplexity 應用開發 VSCode MCP 模組 (github.com/Automations-Project/VSCode-Perplexity-MCP)"
  - "Claude 通過 MCP 搜索並在單一回答中綜合 200+ 信息源的內容"
  - "利用現有 Perplexity 訂閱進行搜索，規避額外搜索 API 成本"
tags: [mcp-integration, perplexity, reverse-engineering, search-extension]
topics: [agents.mcp, foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: true
deep_dive_approved: false
---

## I reverse-engineered the Perplexity app and built an MCP that turns your Perplexity/Comet account into a Claude MCP, so Claude can search like crazy and read 200+ sources in one answer with your personal account subscription without API product needed. [Experiment - Educational Purpose]

開發者反向工程 Perplexity 應用，構建了一個 MCP（模型上下文協議）整合模組，讓 Claude 可直接調用 Perplexity 的搜索引擎功能。透過此 MCP，Claude 能在單一回答中搜索並聚合來自 200+ 信息源的內容，同時利用用戶個人的 Perplexity 訂閱權限無需額外購買搜索 API。項目已開源於 GitHub (VSCode-Perplexity-MCP) 並附有 YouTube 演示。

### 重點
- 反向工程 Perplexity 應用開發 VSCode MCP 模組 (github.com/Automations-Project/VSCode-Perplexity-MCP)
- Claude 通過 MCP 搜索並在單一回答中綜合 200+ 信息源的內容
- 利用現有 Perplexity 訂閱進行搜索，規避額外搜索 API 成本

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t1pdqc/i_reverseengineered_the_perplexity_app_and_built/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Here's video showcase: <a href="https://youtu.be/wErgEe9Pgqo"><strong><em>https://youtu.be/wErgEe9Pgqo</em></strong></a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Aggravating_Bad4639"> /u/Aggravating_Bad4639 </a> <br /> <span><a href="https://github.com/Automations-Project/VSCode-Perplexity-MCP">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1pdqc/i_reverseengineered_the_perplexity_app_and_built/">[comments]</a></span>

</details>