---
id: inbox_236f354d
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-reddit-claudeai-my-pre-coding-routine-with-claude-code-5-b5e5]]"
title: "My pre-coding routine with Claude Code, 5 MCP servers before I write a single line"
url: https://www.reddit.com/r/ClaudeAI/comments/1ta3a9x/my_precoding_routine_with_claude_code_5_mcp/
source: reddit-claudeai
published_at: 2026-05-11T13:26:49+00:00
fetched_at: 2026-05-11T18:19:20.717971+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "开发者公开分享在 Claude Code 中编码前的完整预编码流程，历时 60-90 秒，包含 5 个 MCP 服务器：内存 MCP 维系跨会话的上下文与决策历史、代码图 MCP 构建 repo 调用图并替代盲目 grep、Tavily 搜索当前最佳实践、Context7 加载库的实时文档、hooks 强制读后再编辑。作者核心洞察是重新定义了 Claude 的角色——模型不是知识源而是编制层，MCP 服务、hooks、外部索引才是系统的真正知识骨架。该工作流通过信息分层与读写防护解决了 Claude 幻觉与过时 API 问题，每周记录与图谱更新使整个系统逐周自我锐化。"
key_points:
  - "5 层 MCP 预编码堆栈：内存（跨会话决策）+ 代码图（调用关系）+ Tavily（最新实践）+ Context7（库文档）+ hooks（安全防护）"
  - "模型重新定义为编制器而非知识源；MCP 和 hooks 是系统骨架，记录与索引每周更新使决策精度线性提升"
  - "读-前-编-辑 hook 强制正确上下文加载，虽增加前置 token 成本但避免盲目编辑的数倍重构代价"
tags: [mcp-servers, workflow-optimization, codebase-memory, context7, hooks]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## My pre-coding routine with Claude Code, 5 MCP servers before I write a single line

开发者公开分享在 Claude Code 中编码前的完整预编码流程，历时 60-90 秒，包含 5 个 MCP 服务器：内存 MCP 维系跨会话的上下文与决策历史、代码图 MCP 构建 repo 调用图并替代盲目 grep、Tavily 搜索当前最佳实践、Context7 加载库的实时文档、hooks 强制读后再编辑。作者核心洞察是重新定义了 Claude 的角色——模型不是知识源而是编制层，MCP 服务、hooks、外部索引才是系统的真正知识骨架。该工作流通过信息分层与读写防护解决了 Claude 幻觉与过时 API 问题，每周记录与图谱更新使整个系统逐周自我锐化。

### 重點
- 5 层 MCP 预编码堆栈：内存（跨会话决策）+ 代码图（调用关系）+ Tavily（最新实践）+ Context7（库文档）+ hooks（安全防护）
- 模型重新定义为编制器而非知识源；MCP 和 hooks 是系统骨架，记录与索引每周更新使决策精度线性提升
- 读-前-编-辑 hook 强制正确上下文加载，虽增加前置 token 成本但避免盲目编辑的数倍重构代价

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1ta3a9x/my_precoding_routine_with_claude_code_5_mcp/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Been running this routine for months now. Started because I was losing too much time to Claude just guessing. Halluzinated class names, outdated SDK methods, advice that didn't match the codebase I was actually in. So I built a routine I run before I let it write anything. Takes maybe 60-90 seconds. Saved me hundreds of hours by now. Start the session and load memory. A memory MCP carries context across sessions. Last sprint, open decisions, recent learnings, why we picked X over Y three months ago. Without this, every session starts cold and Claude rebuilds my reasoning from scratch, usually wrong. Index the codebase as a graph. A codebase-memory server builds a knowledge graph of the repo. Functions, callers, dependencies, cycles. When Claude needs to know what calls processOrder, it queries the graph instead of grepping blind. One tool call replaces dozens of file reads. Search with Tavily for current practice. Before any non-trivial decision I let it search what people are actually doing right now. Training data is old. Best practices from a year ago aren't always still best practices. Clean answer with sources, not a wall of SEO spam. Load Context7 for library docs. Context7 fetches current docs for whatever library I'm about to touch. Anthropic SDK, Next.js, Prisma, whatever. The training cutoff means the model cheerfully invents API methods that got renamed two versions ago. Loading the actual current docs ended that whole category of bug months ago. Now write code. At this point Claude has memory, codebase structure, current ecosystem context, and accurate library docs. The output is dramatically different. Less &quot;let me try this and see&quot;, more &quot;based on the call graph and the v5 docs, the change goes here&quot;. Hooks are the other piece nobody talks about. The single most important one for me is a read-before-edit guard. It refuses any edit on a file the session hasn't actually read first. Yes, it costs extra tokens up front because the model has to load the file properly instead of guessing what's in it. Those extra tokens are nothing compared to the tokens you burn cleaning up edits that were made blind. Same idea with a safety guard that blocks destructive commands, and a hook that triggers a re-index after edits so the graph stays in sync. And then the loop closes. Whatever worked goes back into memory. Decisions, patterns, traps we hit, fixes that stuck. Next session starts with all of that already loaded. The system gets sharper every week, not because the model changed, but because the context around it keeps compounding. The bigger pattern I figured out over the past few months is that I stopped treating the model as the source of knowledge. The model is the orchestrator. The MCP servers and the hooks are the system. Memory remembers, the graph knows the code, search knows the present, Context7 knows the docs, hooks keep the model honest. The model just connects them. Curious what other people stack before they start a session. Anyone doing this with different servers or hooks? &#32; submitted by &#32; /u/studiomeyer_io [link] &#32; [comments]

</details>