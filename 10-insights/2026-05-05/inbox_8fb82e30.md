---
id: inbox_8fb82e30
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/0819-reddit-claudeai-i-wish-claude-projects-would-have-the-sa-316f]]"
title: "I wish Claude Projects would have the same read/write ability as Claude Code"
url: https://www.reddit.com/r/ClaudeAI/comments/1t40z2r/i_wish_claude_projects_would_have_the_same/
source: reddit-claudeai
published_at: 2026-05-05T01:20:19+00:00
fetched_at: 2026-05-05T08:45:09.968377+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶反映 Claude Projects（聊天版本）的功能限制。他維護一套個人知識庫系統（todo、目標、日誌、日曆/Gmail 整合），利用 Claude Code 的檔案讀寫能力開發。Claude Projects 的語音功能雖然方便外出使用，但無法直接編輯檔案，導致每週需手動同步（Claude Chat → Claude Code → Projects）。用戶希望 Projects 能有與 Code 相同的讀寫能力，或考慮透過 MCP server 自建解決方案。"
key_points:
  - "痛點：Claude Projects 無檔案寫入能力，僅支援讀取"
  - "當前流程：Claude Chat 產出 → 複製至 Claude Code 編輯 → 手動同步回 Projects"
  - "潛在方案：MCP server 中介層、或 Anthropic 開放 Projects 的檔案寫入權限"
tags: [claude-projects, feature-request, knowledge-management, mcp]
topics: [agents.mcp]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## I wish Claude Projects would have the same read/write ability as Claude Code

用戶反映 Claude Projects（聊天版本）的功能限制。他維護一套個人知識庫系統（todo、目標、日誌、日曆/Gmail 整合），利用 Claude Code 的檔案讀寫能力開發。Claude Projects 的語音功能雖然方便外出使用，但無法直接編輯檔案，導致每週需手動同步（Claude Chat → Claude Code → Projects）。用戶希望 Projects 能有與 Code 相同的讀寫能力，或考慮透過 MCP server 自建解決方案。

### 重點
- 痛點：Claude Projects 無檔案寫入能力，僅支援讀取
- 當前流程：Claude Chat 產出 → 複製至 Claude Code 編輯 → 手動同步回 Projects
- 潛在方案：MCP server 中介層、或 Anthropic 開放 Projects 的檔案寫入權限

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t40z2r/i_wish_claude_projects_would_have_the_same/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>I have a &quot;second brain&quot; filesystem as markdown files that I have been maintaining for months that started out in Claude Code as the interface + file read/write layer... This system just stores a collection of personal todo items, long/short term goals, journal entries and integrates into my calendar and gmail.</p> <p>When Claude Chat released their voice feature, I created a Claude Project with a snapshot of the files within my second brain. I was pleasantly surprised with how well this feature worked. It made accessing my second brain on the go so much easier and I was using my second brain much more.</p> <p>The biggest point of friction with this system however is updating the files. These files go stale so quickly. I will have a productive claude chat session and I would need to ask for a convo summary on convo wrap up, then paste that summary into Claude Code so it can edit my files. THEN I'd paste over those files into my claude project.</p> <p>Really annoying but still works. I just need to sit down every week or so and update my files. Not the end of the world but I feel like this could be fixed SO easily if Anthropic would allow claude chat to edit project files the same way Claude Code does.</p> <p>Not sure if anyone has a similar setup and / or has come up with a clever workaround to this. I was thinking about creating an MCP server that would host my files somewhere and give claude chat read/write access. Feels like overkill though.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Comprehensive-Ad1819"> /u/Comprehensive-Ad1819 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t40z2r/i_wish_claude_projects_would_have_the_same/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t40z2r/i_wish_claude_projects_would_have_the_same/">[comments]</a></span>

</details>