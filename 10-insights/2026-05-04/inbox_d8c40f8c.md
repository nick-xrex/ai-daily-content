---
id: inbox_d8c40f8c
date: 2026-05-04
source_ref: "[[00-inbox/2026-05-04/0819-reddit-claudeai-built-a-plugin-so-my-parallel-claude-cod-c340]]"
title: "built a plugin so my parallel Claude Code sessions can message each other instead of me alt-tabbing"
url: https://www.reddit.com/r/ClaudeAI/comments/1t3osat/built_a_plugin_so_my_parallel_claude_code/
source: reddit-claudeai
published_at: 2026-05-04T17:38:22+00:00
fetched_at: 2026-05-05T08:44:14.773165+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者構建了 Relay 插件（MIT 開源，github.com/innestic/claude-relay），讓多個本機 Claude Code 會話能相互通訊，無需使用者手動視窗切換。機制為每個會話運行一個輕量級 MCP 伺服器，由本機 hub daemon 透過 unix socket 路由訊息。入站提問以 channel notification 形式出現，Claude 能自然地在下一個回合回應。Hub 在最後一個會話斷開後約 5 分鐘自動退出，僅支援同一機器、無身份驗證、所有資料保留本地。此工具應對的核心痛點是多會話工作流中重複的手動切換（如前端問後端：「user object 最後是什麼形狀？」），定位為會話間通訊而非編排框架。"
key_points:
  - "Relay 插件利用 Claude Code channels capability，以 MCP + unix socket 實現平行會話通訊，無視窗切換或複製貼上"
  - "機制：輕量 MCP 伺服器 + 本機 hub daemon 路由，訊息落地為 channel notifications，同機器限制、無驗證、本地隔離"
  - "解決多會話痛點：前後端並行開發時直接提問與廣播，減少上下文切換頻率"
tags: [claude-code-plugin, multi-session-workflow, mcp, developer-experience]
topics: [agents.mcp]
importance: 3
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## built a plugin so my parallel Claude Code sessions can message each other instead of me alt-tabbing

開發者構建了 Relay 插件（MIT 開源，github.com/innestic/claude-relay），讓多個本機 Claude Code 會話能相互通訊，無需使用者手動視窗切換。機制為每個會話運行一個輕量級 MCP 伺服器，由本機 hub daemon 透過 unix socket 路由訊息。入站提問以 channel notification 形式出現，Claude 能自然地在下一個回合回應。Hub 在最後一個會話斷開後約 5 分鐘自動退出，僅支援同一機器、無身份驗證、所有資料保留本地。此工具應對的核心痛點是多會話工作流中重複的手動切換（如前端問後端：「user object 最後是什麼形狀？」），定位為會話間通訊而非編排框架。

### 重點
- Relay 插件利用 Claude Code channels capability，以 MCP + unix socket 實現平行會話通訊，無視窗切換或複製貼上
- 機制：輕量 MCP 伺服器 + 本機 hub daemon 路由，訊息落地為 channel notifications，同機器限制、無驗證、本地隔離
- 解決多會話痛點：前後端並行開發時直接提問與廣播，減少上下文切換頻率

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t3osat/built_a_plugin_so_my_parallel_claude_code/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t3osat/built_a_plugin_so_my_parallel_claude_code/"> <img alt="built a plugin so my parallel Claude Code sessions can message each other instead of me alt-tabbing" src="https://preview.redd.it/68xdfr1qn5zg1.gif?width=640&amp;crop=smart&amp;s=94d86da7bf9e40c6bd1410fbd6acd18bf4896ca9" title="built a plugin so my parallel Claude Code sessions can message each other instead of me alt-tabbing" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I usually have two or more Claude Code sessions open at once. One in the backend repo, one in the frontend. Half the time I'd be in the frontend asking &quot;wait, what shape did the user object end up as?&quot;, then alt-tab, ask the backend session, copy the answer, alt-tab back, paste.</p> <p>The other Claude was right there. It already knew. I was the bottleneck.</p> <p>So I wrote a plugin called Relay. In the frontend window I just say:</p> <p>▎ask the backend session what the user object looks like</p> <p>The backend session sees the question between turns, answers it, and the reply pops up in my frontend session as a notification. No window switching. No copy-paste. Works for broadcasts too, like &quot;ask everyone what they're working on&quot;, and the replies trickle in one at a time.</p> <p>The mechanism is simpler than it sounds. Claude Code shipped a channels capability a while back that lets MCP servers push messages into a session between turns. Relay piggybacks on that. Each session runs a tiny MCP server, a single hub daemon on your machine routes between them over a unix socket, and inbound asks land as channel notifications so Claude reacts to them naturally on its next turn. First session you start spawns the hub. It self-exits about 5 min after the last session disconnects. Same machine only, no auth, nothing leaves your box.</p> <p>I know there are other &quot;make Claudes coordinate&quot; projects. Most of them are orchestration frameworks where one boss Claude bosses worker Claudes around. This isn't that. It's just messaging between sessions you already have open, doing whatever you already had them doing. Closer to slack-for-your-claudes than to a swarm runner.</p> <p>Repo with install steps: <a href="https://github.com/innestic/claude-relay">https://github.com/innestic/claude-relay</a> (MIT)</p> <p>It's day-one open source so the rough edges are real. If you run multi-session workflows already, what's the dumb friction you keep hitting? That's what I want to fix next.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/vildanbina"> /u/vildanbina </a> <br /> <span><a href="https://i.redd.it/68xdfr1qn5zg1.gif">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3osat/built_a_plugin_so_my_parallel_claude_code/">[comments]</a></span> </td></tr></table>

</details>