---
id: inbox_8644a1e1
date: 2026-07-11
source_ref: "[[00-inbox/.../inbox_8644a1e1]]"
title: "Release Candidate v1.6.10-rc.19"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.19
source: gitnexus-releases
published_at: 2026-07-11T17:26:35+00:00
fetched_at: 2026-07-13T00:59:00.065678+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.19 是 v1.6.10 稳定版发布前的第 19 个自动化发布候选版本。该版本新增 CodeBuddy 和 Qoder 编码代理集成，同步实现了完整的 OpenAI Codex 支持，包括 hooks、plugin marketplace 和 setup 功能。版本包含约 19 个重要修复，涉及代理阻隔安装恢复和嵌入自愈（#2370/2372）、FTS 扩展加载错误诊断和自愈（#2374/2375）、MCP 符号内容精确性修复（0-based line storage + 1-based MCP display，#2377-2380）、Windows FTS 依赖诊断（#2383）、自定义嵌入端点失败报告（#2385/2386）、repo 路径解析和克隆目录所有权检查（#2387）、FastAPI 路由解析（#2391/2393）、跨平台 CI 超时处理（#2394）。关键修复还包括增量写回可靠性改进（#2409/2425）、Tree-Sitter 嵌入 NUL 字节恢复（#2430）以及 Napi::Error SIGABRT 修复（#2432/2436），针对分析过程中的稳定性和崩溃问题。该版本主要面向 Windows 和多平台稳定性改进，代码库新增贡献者 @vlisitskii。"
key_points:
  - "完整 Codex 支持新增（hooks、plugin marketplace、setup），同步新增 CodeBuddy 和 Qoder 编码代理集成"
  - "Windows 平台稳定性修复：FTS 依赖缺失诊断（#2383）、repo 路径解析和克隆目录所有权检查（#2387）、跨平台 CI 超时处理（#2394）"
  - "MCP 和嵌入系统改进：符号内容精确性（0-based → 1-based 转换，#2377-2380）、增量写回可靠性（#2409）、Napi::Error SIGABRT 修复（#2432/2436）"
tags: [gitnexus, release-candidate, codex-integration, windows-stability, mcp-fixes]
topics: []
importance: 4
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.19

GitNexus v1.6.10-rc.19 是 v1.6.10 稳定版发布前的第 19 个自动化发布候选版本。该版本新增 CodeBuddy 和 Qoder 编码代理集成，同步实现了完整的 OpenAI Codex 支持，包括 hooks、plugin marketplace 和 setup 功能。版本包含约 19 个重要修复，涉及代理阻隔安装恢复和嵌入自愈（#2370/2372）、FTS 扩展加载错误诊断和自愈（#2374/2375）、MCP 符号内容精确性修复（0-based line storage + 1-based MCP display，#2377-2380）、Windows FTS 依赖诊断（#2383）、自定义嵌入端点失败报告（#2385/2386）、repo 路径解析和克隆目录所有权检查（#2387）、FastAPI 路由解析（#2391/2393）、跨平台 CI 超时处理（#2394）。关键修复还包括增量写回可靠性改进（#2409/2425）、Tree-Sitter 嵌入 NUL 字节恢复（#2430）以及 Napi::Error SIGABRT 修复（#2432/2436），针对分析过程中的稳定性和崩溃问题。该版本主要面向 Windows 和多平台稳定性改进，代码库新增贡献者 @vlisitskii。

### 重點
- 完整 Codex 支持新增（hooks、plugin marketplace、setup），同步新增 CodeBuddy 和 Qoder 编码代理集成
- Windows 平台稳定性修复：FTS 依赖缺失诊断（#2383）、repo 路径解析和克隆目录所有权检查（#2387）、跨平台 CI 超时处理（#2394）
- MCP 和嵌入系统改进：符号内容精确性（0-based → 1-based 转换，#2377-2380）、增量写回可靠性（#2409）、Napi::Error SIGABRT 修复（#2432/2436）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.19)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.19

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.19 \n Target base: 1.6.10 (rc #19 )\n Source commit (main): c644509 \n Release commit (versioned tree): d43c479 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix(web): use repo path identity in switcher by @koriyoshi2041 in #2420 
 fix: stop Napi::Error SIGABRT on analyze — index C++ type lookups, terminate workers only at JS-safe points ( #2432 ) by @magyargergo in #2436 
 
 New Contributors 
 
 @vlisitskii made their first contribution in #2424 
 
 Full Changelog : v1.6.9...v1.6.10-rc.19

</details>