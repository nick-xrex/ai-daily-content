---
id: inbox_99a4eb5b
date: 2026-06-26
source_ref: "[[00-inbox/.../inbox_99a4eb5b]]"
title: "v2.1.195"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.195
source: claude-code-releases
published_at: 2026-06-26T21:29:42+00:00
fetched_at: 2026-06-29T00:53:59.560295+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.195 發布，帶來多項穩定性和使用者體驗改進。新增 CLAUDE_CODE_DISABLE_MOUSE_CLICKS 環境變數可在全螢幕模式下禁用滑鼠點擊但保留滾輪。修復了 hook matchers 的 hyphenated identifier（如 code-reviewer、mcp__brave-search）的子字符串匹配問題，改為精確匹配。macOS 語音輸入修復涵蓋長時間運行後的靜音捕捉、無空格語言（日、中、泰）的自動提交失效。背景工作穩定性提升，解決版本更新時遺失和崩潰重啟延遲問題。外部插件管理與遠程會話啟動體驗均有改善。"
key_points:
  - "新增 CLAUDE_CODE_DISABLE_MOUSE_CLICKS 環境變數控制全螢幕滑鼠輸入"
  - "Hook matcher hyphenated identifier 改為精確匹配，支援 mcp__brave-search__.* 通配符"
  - "修復語音輸入對日文、中文、泰文無空格語言的自動提交失效"
tags: [claude-code, bug-fix, voice-input, plugin-management, background-jobs]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.195

Claude Code v2.1.195 發布，帶來多項穩定性和使用者體驗改進。新增 CLAUDE_CODE_DISABLE_MOUSE_CLICKS 環境變數可在全螢幕模式下禁用滑鼠點擊但保留滾輪。修復了 hook matchers 的 hyphenated identifier（如 code-reviewer、mcp__brave-search）的子字符串匹配問題，改為精確匹配。macOS 語音輸入修復涵蓋長時間運行後的靜音捕捉、無空格語言（日、中、泰）的自動提交失效。背景工作穩定性提升，解決版本更新時遺失和崩潰重啟延遲問題。外部插件管理與遠程會話啟動體驗均有改善。

### 重點
- 新增 CLAUDE_CODE_DISABLE_MOUSE_CLICKS 環境變數控制全螢幕滑鼠輸入
- Hook matcher hyphenated identifier 改為精確匹配，支援 mcp__brave-search__.* 通配符
- 修復語音輸入對日文、中文、泰文無空格語言的自動提交失效

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.195)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.195

What's changed 
 
 Added CLAUDE_CODE_DISABLE_MOUSE_CLICKS to disable mouse click/drag/hover in fullscreen mode while keeping wheel scroll 
 Fixed hook matchers with hyphenated identifiers (e.g. code-reviewer , mcp__brave-search ) accidentally substring-matching — they now exact-match. Use mcp__brave-search__.* to match all tools from a hyphenated MCP server. 
 Fixed voice dictation on macOS capturing silence in long-running sessions after the default input device changes 
 Fixed voice dictation auto-submit never firing for languages written without spaces (Japanese, Chinese, Thai) 
 Fixed external plugins enabled only by project .claude/settings.json not requiring explicit install consent on every loader path 
 Fixed /plugin Enable/Disable not working when a plugin's plugin.json name differs from its marketplace entry name 
 Fixed background jobs disappearing from claude agents or losing data when written by a newer Claude Code version 
 Fixed reopening a crashed background task showing a blank screen for up to 5 seconds instead of its restart 
 Fixed background agent daemons running unreachable when the control socket fails to start, blocking restarts 
 Improved voice mode on Linux: now distinguishes "no microphone" from "SoX not installed" when SoX is present but no audio capture device exists 
 Improved claude agents completed list to fill available vertical space; on short terminals the header compacts so live sessions stay visible 
 Improved Remote session startup with a provisioning checklist while the container starts

</details>