---
id: inbox_7750b85b
date: 2026-06-25
source_ref: "[[00-inbox/2026-06-25/2203-hackernews-show-hn-openknowledge-open-source-ai-fir-072d]]"
title: "Show HN: OpenKnowledge – open source AI-first alternative to Obsidian/Notion"
url: https://github.com/inkeep/open-knowledge
source: hackernews
published_at: 2026-06-25T16:04:46+00:00
fetched_at: 2026-06-27T22:11:31.654133+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Inkeep 開源發布 OpenKnowledge，一套整合 Claude、Codex 的 WYSIWYG markdown editor，定位為 Obsidian 與 Notion 的開源替代品。產品提供 MacOS app、Web UI 與 CLI 三種形式，採用 Tiptap/ProseMirror、CodeMirror、YJS (CRDT) 技術棧。核心工程挑戰包括實現 ProseMirror 與 markdown 的無損雙向轉換，以及透過 dual-observer CRDT 維持編輯器與原始檔案狀態同步。架構基於 git/GitHub 驅動協作與版本控制，支援 AI agents 在 markdown 中的可視化操作與即時團隊協作。完全開源自託管，優先保護資料隱私，適合 AI-first 工作流程。"
key_points:
  - "OpenKnowledge 整合 Claude/Codex，提供 WYSIWYG UI 相比 Obsidian 更友善的編輯體驗"
  - "核心技術：ProseMirror ↔ markdown 無損雙向轉換 + dual-observer CRDT 維持狀態同步"
  - "Git/GitHub 驅動協作與版本控制，支援 agents 可視化與隱私優先的自託管架構"
tags: [ai-editor, open-source, crdt, claude-integration, markdown-editor]
topics: [foundation_models.claude, agents.mcp]
importance: 3
novelty: 3
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: OpenKnowledge – open source AI-first alternative to Obsidian/Notion

Inkeep 開源發布 OpenKnowledge，一套整合 Claude、Codex 的 WYSIWYG markdown editor，定位為 Obsidian 與 Notion 的開源替代品。產品提供 MacOS app、Web UI 與 CLI 三種形式，採用 Tiptap/ProseMirror、CodeMirror、YJS (CRDT) 技術棧。核心工程挑戰包括實現 ProseMirror 與 markdown 的無損雙向轉換，以及透過 dual-observer CRDT 維持編輯器與原始檔案狀態同步。架構基於 git/GitHub 驅動協作與版本控制，支援 AI agents 在 markdown 中的可視化操作與即時團隊協作。完全開源自託管，優先保護資料隱私，適合 AI-first 工作流程。

### 重點
- OpenKnowledge 整合 Claude/Codex，提供 WYSIWYG UI 相比 Obsidian 更友善的編輯體驗
- 核心技術：ProseMirror ↔ markdown 無損雙向轉換 + dual-observer CRDT 維持狀態同步
- Git/GitHub 驅動協作與版本控制，支援 agents 可視化與隱私優先的自託管架構

**原文：** [hackernews](https://github.com/inkeep/open-knowledge)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hi HN, Nick here. We’re launching OpenKnowledge ( https:&#x2F;&#x2F;openknowledge.ai&#x2F; ), a “what you see is what you get” markdown editor that has direct integrations with Claude, Codex, and other agents. Available as MacOS app or Web UI+CLI. Fully free&#x2F;local and OSS. We built this because we wanted a Notion-like experience for writing and sharing markdown files across our team. Obsidian is the best alternative we tried, but found it doesn’t have a true WYSWIG UI and it didn’t integrate well with Claude&#x2F;Codex outside of community plugins. So we built OpenKnowledge. It takes shape as: 1. A MacOS app with a file navigator, the WYSIWYG editor, and link explorer. 2. Integrations with the Claude, Codex, and Cursor desktop apps. The agents can open an OpenKnowledge editor within their embedded web browsers for a side-by-side experience. 3. Built-in mcps, skills, and RAG for LLM-wiki and “AI Second Brain” scenarios + spec writing 4. An embedded terminal and CLI for TUI-first users OSS stack includes: Tiptap&#x2F;prosemirror, CodeMirror, yjs (CRDT), Electron (MacOS app), Orama, remark&#x2F;rehype&#x2F;micromark&#x2F;mdast, @pierre&#x2F;trees On the architecture side, the interesting eng. challenges included: 1. A pipeline to convert ProseMirror to markdown in a bidirectional lossless way. ProseMirror uses ASTs, which are not designed to have byte-fidelity. 2. A dual-observer CRDT to keep the ProseMirror and markdown state in-sync. The CRDT + git also power a collaborative experience that shows what Agents are doing in the markdown, have undo&#x2F;redo, and version history. The “Share” and cloud-sync functionality are geared for team collaboration. They feel “no-code” but leverage git&#x2F;GitHub under the hood, which also means data stays fully private. In that spirit, we made OpenKnowledge open source for anybody who’s curious or who’d like to contribute. We’re actively thinking about plugins&#x2F;extensibility and what’s next. If you have suggestions or feedback, would love to hear it.

</details>