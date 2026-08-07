---
id: inbox_7ac809d1
date: 2026-08-06
source_ref: "[[00-inbox/.../inbox_7ac809d1]]"
title: "v2.1.223"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.223
source: claude-code-releases
published_at: 2026-08-06T00:52:37+00:00
fetched_at: 2026-08-07T01:19:31.890856+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.223 發布，重點關注安全性與穩定性。新增 owner wildcard 支持（「owner/*」）用於 GitHub 組織級市集授權/封鎖；新增告警機制當 workflow agents 的 subagent model 被限制時會降級到 parent model；新增 /teleport 提示便於從雲端會話轉移到本地（claude --teleport <session id>）。多項重要安全修復包括：(1) 修復 Bash 權限繞過漏洞（crafted command 隱藏部分內容）(2) 修復 Unicode/tabs padding 繞過 permission dialog (3) 修復 workflow scripts 動態 import() sandbox 逃逸。配置管理方面修復 agent definition 的 bypassPermissions 忽視組織層停用政策的問題；model override 的陌生 key 不再被誤判為 canonical model ID；managed settings 現在正確合併 env block。性能方面改變 CLAUDE_CODE_DISABLE_1M_CONTEXT 行為以支持所有 1M native window 模型的自動 200K 縮減。UI 改動包括 /review 成為 /code-review 別名，支持深度審查（/code-review ultra）。"
key_points:
  - "Owner wildcard 支持（owner/*）讓組織層級市集控制更靈活；permission dialog 強化透過 Unicode/tab padding 檢測防止隱藏指令"
  - "多項 Bash sandbox 逃逸修復：crafted command obfuscation、workflow dynamic import()、agent bypassPermissions policy gap、fork parent prompt rebuild hang"
  - "CLAUDE_CODE_DISABLE_1M_CONTEXT 改為應用所有 1M native window 模型而非固定清單；model override 陌生 key 不再誤判；managed settings env 按 key 合併而非全面覆蓋"
tags: [claude-code, v2.1.223, security-fixes, permission-system, model-routing]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.223

Claude Code v2.1.223 發布，重點關注安全性與穩定性。新增 owner wildcard 支持（「owner/*」）用於 GitHub 組織級市集授權/封鎖；新增告警機制當 workflow agents 的 subagent model 被限制時會降級到 parent model；新增 /teleport 提示便於從雲端會話轉移到本地（claude --teleport <session id>）。多項重要安全修復包括：(1) 修復 Bash 權限繞過漏洞（crafted command 隱藏部分內容）(2) 修復 Unicode/tabs padding 繞過 permission dialog (3) 修復 workflow scripts 動態 import() sandbox 逃逸。配置管理方面修復 agent definition 的 bypassPermissions 忽視組織層停用政策的問題；model override 的陌生 key 不再被誤判為 canonical model ID；managed settings 現在正確合併 env block。性能方面改變 CLAUDE_CODE_DISABLE_1M_CONTEXT 行為以支持所有 1M native window 模型的自動 200K 縮減。UI 改動包括 /review 成為 /code-review 別名，支持深度審查（/code-review ultra）。

### 重點
- Owner wildcard 支持（owner/*）讓組織層級市集控制更靈活；permission dialog 強化透過 Unicode/tab padding 檢測防止隱藏指令
- 多項 Bash sandbox 逃逸修復：crafted command obfuscation、workflow dynamic import()、agent bypassPermissions policy gap、fork parent prompt rebuild hang
- CLAUDE_CODE_DISABLE_1M_CONTEXT 改為應用所有 1M native window 模型而非固定清單；model override 陌生 key 不再誤判；managed settings env 按 key 合併而非全面覆蓋

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.223)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.223

What's changed 
 
 Added owner wildcard entries ( "owner/*" ) to the strictKnownMarketplaces and blockedMarketplaces managed settings for allowing or blocking all marketplace repos under a GitHub org 
 Added a warning when workflow agents, forked skills, slash commands, or resumed background agents' requested subagent model is restricted and the parent model runs instead 
 Added a /teleport hint in cloud sessions showing how to continue locally with claude --teleport &lt;session id&gt; 
 Fixed a Bash permission bypass where a crafted command could hide parts of itself from permission checks 
 Fixed permission prompts so commands padded with tabs or invisible Unicode can no longer hide part of the command from the approval dialog 
 Fixed workflow scripts being able to use dynamic import() to run code outside the workflow sandbox 
 Fixed a permission gap where an agent definition's bypassPermissions mode ignored the org bypass-permissions disable policy 
 Fixed resuming a session after a mid-session /cd coming back empty 
 Fixed gateway model discovery hiding Claude models registered under provider-prefixed IDs such as vertex_ai/claude-* or bedrock/anthropic.claude-* 
 Fixed modelOverrides keys that aren't Anthropic model IDs being treated as the session's canonical model ID; unknown keys are now ignored as documented 
 Fixed managed settings: server-delivered settings no longer disable the env block of a machine-local managed-settings.json or MDM profile; admin env now merges per key 
 Fixed sandboxed commands failing to start on Linux when sandbox.filesystem.denyWrite covers the working directory 
 Fixed forked background agents getting stuck "already resuming" for the rest of the session when rebuilding the fork's parent prompt failed during resume 
 Fixed a resumed session failing every turn, or leaving the interactive app on an unresponsive error screen, when its history held a malformed diagnostics attachment 
 Fixed a rare hang when parsing unusual git push output 
 Changed CLAUDE_CODE_DISABLE_1M_CONTEXT to hold every Claude model with a native 1M window to 200K via auto-compaction, not just a fixed list; a startup warning now appears when auto-compaction isn't holding the session to 200K 
 Changed auto-compact to keep sessions on unrecognized model IDs within the assumed context window instead of letting them grow past it; set CLAUDE_CODE_DISABLE_UNKNOWN_MODEL_WINDOW_ENFORCEMENT=1 to restore the previous behavior 
 Changed /review to be an alias of /code-review , which reviews the current diff or a PR ( /code-review &lt;level&gt; &lt;pr#&gt; ); use /code-review ultra for a deep cloud review 
 Changed /code-review with no effort level to reuse the level you typed last; type a level like /code-review high to change it

</details>