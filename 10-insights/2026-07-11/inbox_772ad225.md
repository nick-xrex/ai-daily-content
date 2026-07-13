---
id: inbox_772ad225
date: 2026-07-11
source_ref: "[[00-inbox/.../inbox_772ad225]]"
title: "Release Candidate v1.6.10-rc.17"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.17
source: gitnexus-releases
published_at: 2026-07-11T07:48:17+00:00
fetched_at: 2026-07-13T00:59:00.100047+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.17 是第 17 个自动化发布候选版本，在稳定版推进过程中持续优化平台兼容性。该版本包含 CodeBuddy 和 Qoder 编码代理集成以及完整的 OpenAI Codex 支持。版本共包含约 15 个修复，主要涉及代理阻隔安装恢复和嵌入自愈、FTS 扩展加载错误诊断和自愈、MCP 符号内容和行号显示修复、Windows FTS 依赖缺失诊断、自定义嵌入端点失败报告、服务器 repo 路径解析和克隆目录所有权检查、FastAPI 路由路径常量解析等关键稳定性和集成改进。这些修复针对用户在多平台环境中（特别是 Windows）使用 GitNexus 时可能遇到的各类问题。该版本继续聚焦向 v1.6.10 稳定版迈进的目标。"
key_points:
  - "完整 Codex 支持新增，支持 CodeBuddy 和 Qoder 编码代理集成"
  - "FTS 和嵌入系统改进：扩展加载错误诊断和自愈（#2374/2375）、Windows 依赖检查（#2383）、自定义端点失败报告（#2385/2386）"
  - "repo 路径管理修复：克隆目录所有权检查（#2387）、FastAPI 路由常量解析（#2391/2393）"
tags: [gitnexus, release-candidate, codex, bug-fixes, windows]
topics: []
importance: 3
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.17

GitNexus v1.6.10-rc.17 是第 17 个自动化发布候选版本，在稳定版推进过程中持续优化平台兼容性。该版本包含 CodeBuddy 和 Qoder 编码代理集成以及完整的 OpenAI Codex 支持。版本共包含约 15 个修复，主要涉及代理阻隔安装恢复和嵌入自愈、FTS 扩展加载错误诊断和自愈、MCP 符号内容和行号显示修复、Windows FTS 依赖缺失诊断、自定义嵌入端点失败报告、服务器 repo 路径解析和克隆目录所有权检查、FastAPI 路由路径常量解析等关键稳定性和集成改进。这些修复针对用户在多平台环境中（特别是 Windows）使用 GitNexus 时可能遇到的各类问题。该版本继续聚焦向 v1.6.10 稳定版迈进的目标。

### 重點
- 完整 Codex 支持新增，支持 CodeBuddy 和 Qoder 编码代理集成
- FTS 和嵌入系统改进：扩展加载错误诊断和自愈（#2374/2375）、Windows 依赖检查（#2383）、自定义端点失败报告（#2385/2386）
- repo 路径管理修复：克隆目录所有权检查（#2387）、FastAPI 路由常量解析（#2391/2393）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.17)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.17

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.17 \n Target base: 1.6.10 (rc #17 )\n Source commit (main): accf61c \n Release commit (versioned tree): 883d36f \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(setup): add CodeBuddy and Qoder coding-agent integrations by @magyargergo in #2368 
 feat: full Codex support — hooks, plugin marketplace, and setup ( #2328 , supersedes #1131 ) by @magyargergo in #2369 
 fix: proxy-blocked installs survive onnxruntime-node postinstall and self-heal embeddings ( #2370 ) by @magyargergo in #2372 
 fix: surface real FTS extension LOAD errors and self-heal broken extension files ( #2374 ) by @magyargergo in #2375 
 fix(lbug/mcp): exact symbol content + 0-based line storage with 1-based MCP display ( #2377 , #2379 ) by @magyargergo in #2380 
 fix(fts): diagnose Windows FTS missing-dependency load failures ( #2374 , Phase 1) by @magyargergo in #2383 
 fix: report custom HTTP embedding endpoint failures instead of huggingface download errors ( #2385 ) by @magyargergo in #2386 
 fix(lbug): recognize Windows missing-shadow error so serve repo-switch recovers ( #2382 ) by @magyargergo in #2387 
 fix: resolve imported/composed FastAPI route path constants ( #2391 ) by @magyargergo in #2393 
 fix(ci): shard platform-sensitive matrix + spawn built CLI to fix Windows cross-platform timeout by @magyargergo in #2394 
 fix(hook): emit MCP query hint when server owns DB lock ( #2396 ) by @magyargergo in #2397 
 feat: gate Icebug community engine prototype by @azizur100389 in #2376 
 fix(web): improve repository dropdown search by @evander-wang in #2381 
 fix: surface incremental dirty state diagnostics by @koriyoshi2041 in #2410 
 fix: make large incremental writebacks commit reliably ( #2409 ) by @magyargergo in #2425 
 fix(cli): actionable diagnostics for non-4K page-size buffer manager failures by @vlisitskii in #2424 
 fix(tree-sitter): recover declarations after embedded NUL bytes by @magyargergo in #2430 
 
 New Contributors 
 
 @vlisitskii made their first contribution in #2424 
 
 Full Changelog : v1.6.9...v1.6.10-rc.17

</details>