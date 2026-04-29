---
id: inbox_f30dc91d
date: 2026-04-29
source_ref: "[[00-inbox/2026-04-29/0658-reddit-claudeai-your-claude-code-project-dashboard-is-no-56ac]]"
title: "Your Claude Code project dashboard is now on the Mac App Store"
url: https://www.reddit.com/r/ClaudeAI/comments/1symv0c/your_claude_code_project_dashboard_is_now_on_the/
source: reddit-claudeai
published_at: 2026-04-29T03:13:42+00:00
fetched_at: 2026-04-29T07:28:48.558994+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Storybloq 項目管理工具現已免費上架 macOS App Store，在版本控制根目錄維護 .story/ 目錄（JSON 與 Markdown，git 可追蹤），透過 CLI 與 MCP 伺服器向 Claude Code 會話暴露項目上下文。Mac 應用整合看板視圖、待辦積壓、會話交接筆記產生的時間軸、自主會話狀態追蹤及嵌入式 Claude Code 終端，使開發者無需切換視窗即可協調任務。完整應用（Swift/SwiftUI Mac 程式 + TypeScript CLI/MCP 伺服器）由 Claude Code 自動生成，期間追蹤約 580 張工單與 260 次會話交接，充分驗證 Claude 代碼生成在大規模完整應用開發的可行性與品質。應用支援 macOS 14+（Apple Silicon 與 Intel），透過 App Store 自動更新。"
key_points:
  - "Storybloq Mac App 上架：免費開源，整合看板、時間軸、嵌入式終端，監控 Claude Code 進度與項目狀態"
  - "規模驗證數據：~580 工單 × ~260 會話交接 = 證實 Claude 代碼可交付完整生產級應用的成熟度與品質"
  - "MCP 與 CLI 整合：.story/ 作為 git 可追蹤的單一來源，CLI 與 MCP 伺服器暴露上下文予 Claude Code，實現無縫人-AI 協作"
tags: [storybloq, claude-code, project-tracker, mcp, kanban, app-store]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Your Claude Code project dashboard is now on the Mac App Store

Storybloq 項目管理工具現已免費上架 macOS App Store，在版本控制根目錄維護 .story/ 目錄（JSON 與 Markdown，git 可追蹤），透過 CLI 與 MCP 伺服器向 Claude Code 會話暴露項目上下文。Mac 應用整合看板視圖、待辦積壓、會話交接筆記產生的時間軸、自主會話狀態追蹤及嵌入式 Claude Code 終端，使開發者無需切換視窗即可協調任務。完整應用（Swift/SwiftUI Mac 程式 + TypeScript CLI/MCP 伺服器）由 Claude Code 自動生成，期間追蹤約 580 張工單與 260 次會話交接，充分驗證 Claude 代碼生成在大規模完整應用開發的可行性與品質。應用支援 macOS 14+（Apple Silicon 與 Intel），透過 App Store 自動更新。

### 重點
- Storybloq Mac App 上架：免費開源，整合看板、時間軸、嵌入式終端，監控 Claude Code 進度與項目狀態
- 規模驗證數據：~580 工單 × ~260 會話交接 = 證實 Claude 代碼可交付完整生產級應用的成熟度與品質
- MCP 與 CLI 整合：.story/ 作為 git 可追蹤的單一來源，CLI 與 MCP 伺服器暴露上下文予 Claude Code，實現無縫人-AI 協作

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1symv0c/your_claude_code_project_dashboard_is_now_on_the/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1symv0c/your_claude_code_project_dashboard_is_now_on_the/"> <img alt="Your Claude Code project dashboard is now on the Mac App Store" src="https://external-preview.redd.it/RX2aa_4Bjf0vE9wm7YU_DGJZ6biIaX5Hap_VKlvn9_8.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=750a3fd1aa58ad1d55d8eda94535bf628464faf9" title="Your Claude Code project dashboard is now on the Mac App Store" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Follow up to my .story/ post last week. The Mac companion is now live on the Mac App Store, free.</p> <p>App Store: <a href="https://apps.apple.com/us/app/storybloq/id6761348691">https://apps.apple.com/us/app/storybloq/id6761348691</a></p> <p>Quick recap if you missed the original.<br /> Storybloq is a project tracker that lives in <code>.story/</code> inside your repo.</p> <p>Tickets, issues, roadmap phases, lessons, session handovers. All JSON and markdown, editable in any text editor, git-trackable. The CLI and MCP server expose it to Claude Code so <code>/story</code> loads everything at session start.</p> <p>The Mac app is the visual side. It watches <code>.story/</code> while Claude works.</p> <p>What you get with the Mac app:</p> <p>- Your full backlog at a glance. What's left, what's in progress, what to work on next.</p> <p>- A live kanban so you see status flip the second Claude updates a ticket.</p> <p>- A project timeline generated from your session handovers.</p> <p>- Notes you can view and edit, for brainstorming.</p> <p>- Autonomous session statuses if you use the autonomous feature.</p> <p>- The Claude Code terminal embedded in the same window, so the agent and the board share a screen.</p> <p>It's sandboxed and signed by Apple, auto-updates through the App Store, and runs on macOS 14+ (Apple Silicon and Intel).</p> <p><strong>Built with Claude:</strong></p> <p>The Mac app (Swift / SwiftUI) and the CLI / MCP server (TypeScript) were both written in Claude Code using this same framework. The workspace's <code>.story/</code> has tracked every ticket and session handover across the build.</p> <p>Around 580 tickets and 260 handovers so far. Claude wrote the code, ran review rounds with Codex through MCP, fixed the findings, and shipped the App Store submission.</p> <p>The framework is its own longest-running test case.</p> <p><strong>Links</strong>:</p> <p>- App Store: <a href="https://apps.apple.com/us/app/storybloq/id6761348691">https://apps.apple.com/us/app/storybloq/id6761348691</a></p> <p>- GitHub (CLI and MCP source): <a href="https://github.com/Storybloq/storybloq">https://github.com/Storybloq/storybloq</a></p> <p>Disclosure: I built it. Free, open source, no account, no paid tier, no referral links.</p> <p>Curious how people running multi-project Claude Code work are laying this out.</p> <p>Embedded terminal next to the board, or terminal in a separate window? The inline layout has been cutting that &quot;wait, what was I doing?&quot; moment when switching between projects, but I'd love to hear what others have settled on.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/LastNameOn"> /u/LastNameOn </a> <br /> <span><a href="https://www.storybloq.com/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1symv0c/your_claude_code_project_dashboard_is_now_on_the/">[comments]</a></span> </td></tr></table>

</details>