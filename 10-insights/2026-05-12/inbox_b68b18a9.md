---
id: inbox_b68b18a9
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/0014-claude-mem-releases-v13-2-0-4a92]]"
title: "v13.2.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.2.0
source: claude-mem-releases
published_at: 2026-05-12T01:44:07+00:00
fetched_at: 2026-05-26T00:21:35.239321+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.2.0 新增 wowerpoint skill 生成 kawaii NotebookLM 投影片牌組。單一來源文件→牌組，包裝 notebooklm CLI 搭配 kawaii-prompt + --format detailed 預設，採用 spawn-subagent 模式讓 ~10 分鐘生成不阻斷主對話。預設提示範本：「使用 kawaii 角色訴說 <subject> 的故事。保持溫暖清晰」，允許使用者自訂提示傳遞。單一來源/牌組強制以工作流形狀施行：確認或撰寫來源文件後加入 NotebookLM。設置需要 notebooklm-py（uv tool install --with playwright）、playwright install chromium、jq。Subagent 完成通知觸發時 PDF 已磁碟；主對話不被渲染阻斷。"
key_points:
  - "wowerpoint skill 包裝 notebooklm CLI，kawaii-prompt + --format detailed 預設"
  - "Spawn-subagent 模式：~10 分鐘生成不阻斷主對話，完成通知觸發時 PDF 已磁碟"
  - "單一來源/牌組強制；需要 notebooklm-py + playwright chromium + jq"
tags: [wowerpoint, notebooklm, slide-deck, subagent-pattern, claude-mem]
topics: [agents.mcp]
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.2.0

claude-mem v13.2.0 新增 wowerpoint skill 生成 kawaii NotebookLM 投影片牌組。單一來源文件→牌組，包裝 notebooklm CLI 搭配 kawaii-prompt + --format detailed 預設，採用 spawn-subagent 模式讓 ~10 分鐘生成不阻斷主對話。預設提示範本：「使用 kawaii 角色訴說 <subject> 的故事。保持溫暖清晰」，允許使用者自訂提示傳遞。單一來源/牌組強制以工作流形狀施行：確認或撰寫來源文件後加入 NotebookLM。設置需要 notebooklm-py（uv tool install --with playwright）、playwright install chromium、jq。Subagent 完成通知觸發時 PDF 已磁碟；主對話不被渲染阻斷。

### 重點
- wowerpoint skill 包裝 notebooklm CLI，kawaii-prompt + --format detailed 預設
- Spawn-subagent 模式：~10 分鐘生成不阻斷主對話，完成通知觸發時 PDF 已磁碟
- 單一來源/牌組強制；需要 notebooklm-py + playwright chromium + jq

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.2.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's new 
 wowerpoint skill — kawaii NotebookLM slide-deck generator 
 Turn one source document into a kawaii NotebookLM slide-deck PDF. Wraps the notebooklm CLI with the kawaii-prompt + --format detailed defaults and a spawn-subagent pattern so generation (~10 min) never blocks the main conversation. 
 
 Single-source-per-deck is enforced by the workflow shape: confirm or write the source doc before adding it to NotebookLM. Don't paper over a weak source by stacking more sources — write a comprehensive doc first. 
 Slide-deck only. Videos and podcasts from the same engine are noticeably worse and out of scope; the skill refers users to the notebooklm CLI directly for those formats. 
 Default prompt template: Use kawaii characters to tell the story of &lt;subject&gt;. Keep it warm and clear. Pass any user-supplied prompt through verbatim. 
 Setup requires notebooklm-py (via uv tool install --with playwright ), playwright install chromium , and jq . 
 Spawn-and-end-turn pattern: the subagent's completion notification fires when the PDF is on disk; the main conversation never blocks on the ~10 min render. 
 
 See PR #2430 for the full design notes and review history. 
 Skills inventory 
 This release brings the plugin to 12 skills : babysit, do, how-it-works, knowledge-agent, learn-codebase, make-plan, mem-search, pathfinder, smart-explore, timeline-report, version-bump, wowerpoint.

</details>