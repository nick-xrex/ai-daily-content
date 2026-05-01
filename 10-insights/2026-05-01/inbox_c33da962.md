---
id: inbox_c33da962
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/1257-reddit-claudeai-example-of-using-the-godotiq-mcp-with-co-74e9]]"
title: "Example of using the GodotIQ MCP with Coding Agent to create video games"
url: https://www.reddit.com/r/ClaudeAI/comments/1t0q8bf/example_of_using_the_godotiq_mcp_with_coding/
source: reddit-claudeai
published_at: 2026-05-01T11:04:05+00:00
fetched_at: 2026-05-01T13:38:54.394349+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者推出 GodotIQ MCP server，為 Godot 遊戲開發提供真正的場景空間智能。傳統 AI 代理在 Godot 中工作盲目（無法看見節點位置、信號、調用關係），GodotIQ 解決此痛點，提供 2D/3D 場景理解、代碼關係圖、編輯器整合。作者讓代理自主運行一小時，成功生成完整雙搖桿生存者遊戲（含波次、BOSS、升級卡、音頻、著色器）。免費層 22 工具，Pro 層 $19 一次性購買；支持 Claude Code、Cursor、Codex、Windsurf 等 MCP 客戶端。`pip install godotiq`。"
key_points:
  - "GodotIQ 提供空間智能（scene understanding）與信號/調用關係圖，解決傳統 AI 代理在 Godot 中的「盲眼」問題"
  - "免費層 22 工具足夠探索，Pro 層 $19 提供完整空間智能和進階代碼分析，適合複雜專案開發"
  - "實測：代理一小時內自主完成帶 AI、波次、BOSS、卡牌系統的遊戲原型，展示 MCP 與自主代理在遊戲開發中的實際能力"
tags: [godot, mcp, game-dev, agents, spatial-intelligence]
topics: [agents.mcp]
importance: 4
novelty: 5
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Example of using the GodotIQ MCP with Coding Agent to create video games

開發者推出 GodotIQ MCP server，為 Godot 遊戲開發提供真正的場景空間智能。傳統 AI 代理在 Godot 中工作盲目（無法看見節點位置、信號、調用關係），GodotIQ 解決此痛點，提供 2D/3D 場景理解、代碼關係圖、編輯器整合。作者讓代理自主運行一小時，成功生成完整雙搖桿生存者遊戲（含波次、BOSS、升級卡、音頻、著色器）。免費層 22 工具，Pro 層 $19 一次性購買；支持 Claude Code、Cursor、Codex、Windsurf 等 MCP 客戶端。`pip install godotiq`。

### 重點
- GodotIQ 提供空間智能（scene understanding）與信號/調用關係圖，解決傳統 AI 代理在 Godot 中的「盲眼」問題
- 免費層 22 工具足夠探索，Pro 層 $19 提供完整空間智能和進階代碼分析，適合複雜專案開發
- 實測：代理一小時內自主完成帶 AI、波次、BOSS、卡牌系統的遊戲原型，展示 MCP 與自主代理在遊戲開發中的實際能力

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t0q8bf/example_of_using_the_godotiq_mcp_with_coding/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t0q8bf/example_of_using_the_godotiq_mcp_with_coding/"> <img alt="Example of using the GodotIQ MCP with Coding Agent to create video games" src="https://external-preview.redd.it/NGE0andvNXFiaXlnMeNNlzkiUFzwvVoQNmCoLHZkwR6UmF8pTPlW5NrzCShL.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=561633c77104703fe075a2235fee845d83a1f863" title="Example of using the GodotIQ MCP with Coding Agent to create video games" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I’ve developed an MCP server for Godot. Most coding agents in Godot today work blindly: they read files but don’t know where the nodes are in space, don’t understand the signals, and don’t see what calls what. Godotiq solves this, giving the agent a true understanding of the 2D/3D scene, the code, and the editor.</p> <p>To test it, I gave it some free assets I found online and a prompt, and let it run for about an hour. It produced a mini twin-stick survivors-style game with waves, bosses, power-up cards, audio, and shaders. The agent did it all on its own, including visual debugging when something wasn’t working. You can try it in your browser at <a href="http://godotiq.com">godotiq.com</a> (desktop only) .</p> <p>Godotiq has a free tier with 22 tools, enough to explore the workflow and see if it’s right for you. It works with any MCP client (Claude Code, Cursor, Codex, Windsurf). There’s also a Pro tier for a one-time fee of $19 with full spatial intelligence and advanced code analysis, designed for those developing projects of a certain complexity, it’s the tier I used for Neuroforge.</p> <p><code>pip install godotiq</code></p> <p>More info at <a href="http://godotiq.com">godotiq.com</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/jf_nash"> /u/jf_nash </a> <br /> <span><a href="https://v.redd.it/n0dfcf5qbiyg1">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t0q8bf/example_of_using_the_godotiq_mcp_with_coding/">[comments]</a></span> </td></tr></table>

</details>