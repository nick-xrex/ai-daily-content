---
id: inbox_5d6565dd
date: 2026-05-21
source_ref: "[[00-inbox/2026-05-21/0014-claude-mem-releases-v13-3-0-738d]]"
title: "v13.3.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.3.0
source: claude-mem-releases
published_at: 2026-05-21T10:26:08+00:00
fetched_at: 2026-05-26T00:21:35.238298+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.3.0 發佈 3 個新 skill 擴展代理能力。design-is (#2483) 針對 Dieter Rams 的 10 項「Good design is...」原則審計設計，產出 0-3 分/原則與 NEW/REFINE/REDESIGN 判決。weekly-digests (#2399) 產生全專案 claude-mem 時軸的序列化 chapter-per-ISO-week 摘要，透過順序 subagent pipeline 保持 30+ 章節敘事一致。oh-my-issues (#2409) 根因議題聚類，編成了將 ~100 個未解決議題合併為 6 plan-master 的方法；支援聚類、分類、綑綁 3 種模式。同時修復 MCP 重複根 .mcp.json 與 Codex 轉錄重放。"
key_points:
  - "design-is：Dieter Rams 10 原則審計，0-3 分/原則、NEW/REFINE/REDESIGN 判決、file:line 證據"
  - "weekly-digests：ISO-week 序列化摘要，順序 subagent pipeline 保持 30+ 章敘事一致"
  - "oh-my-issues：根因聚類，3 模式（cluster pass、triage、bundle），將 ~100 未解決→ 6 plan-master"
tags: [design-audit, skill-release, issue-clustering, claude-mem, workflow]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.3.0

claude-mem v13.3.0 發佈 3 個新 skill 擴展代理能力。design-is (#2483) 針對 Dieter Rams 的 10 項「Good design is...」原則審計設計，產出 0-3 分/原則與 NEW/REFINE/REDESIGN 判決。weekly-digests (#2399) 產生全專案 claude-mem 時軸的序列化 chapter-per-ISO-week 摘要，透過順序 subagent pipeline 保持 30+ 章節敘事一致。oh-my-issues (#2409) 根因議題聚類，編成了將 ~100 個未解決議題合併為 6 plan-master 的方法；支援聚類、分類、綑綁 3 種模式。同時修復 MCP 重複根 .mcp.json 與 Codex 轉錄重放。

### 重點
- design-is：Dieter Rams 10 原則審計，0-3 分/原則、NEW/REFINE/REDESIGN 判決、file:line 證據
- weekly-digests：ISO-week 序列化摘要，順序 subagent pipeline 保持 30+ 章敘事一致
- oh-my-issues：根因聚類，3 模式（cluster pass、triage、bundle），將 ~100 未解決→ 6 plan-master

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.3.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's New 
 New skills 
 
 design-is ( #2483 ) — audits a design against Dieter Rams' ten "Good design is..." principles. Produces per-principle 0–3 scores with file:line evidence and a NEW / REFINE / REDESIGN verdict, then hands off a ready-to-run /make-plan prompt. 
 weekly-digests ( #2399 ) — produces a chapter-per-ISO-week serial digest of a project's full claude-mem timeline. Sequential subagent pipeline keeps the narrative coherent across 30+ chapters. 
 oh-my-issues ( #2409 ) — root-cause issue clustering. Codifies the consolidation method that turned ~100 open issues into 6 plan-masters during the v13.0.1 cycle. Three modes: cluster pass, triage, bundle. 
 
 Fixes 
 
 fix(mcp): drop duplicate root .mcp.json ( #2411 ) — Claude Code's /doctor was warning "MCP server mcp-search skipped — same command/URL as already-configured mcp-search" for every plugin user. The root copy was vestigial; the plugin's namespaced registration now wins. 
 fix: stop Codex transcript replay after hooks migration ( #2365 ) — disables the default ~/.codex/sessions/**/*.jsonl watch (native Codex hooks are now authoritative). Repairs ~/.codex/config.toml to set [features] hooks = true and [plugins."claude-mem@claude-mem-local"] enabled = true directly. Fixes transcript replay where files discovered after startup ignored startAtEnd and re-injected history. 
 
 Opt back into legacy Codex transcript ingestion with CLAUDE_MEM_CODEX_TRANSCRIPT_INGESTION=true if you depend on the JSONL watcher.

</details>