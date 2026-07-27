---
id: inbox_d32d9d7c
date: 2026-07-27
source_ref: "[[00-inbox/2026-07-27/0123-ruflo-releases-v3-32-12-subagentpermissiondelegate-2768-cde1]]"
title: "v3.32.12 — SubagentPermissionDelegate (#2768) + Flash Attention credibility cleanup (#2739 dream)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.12
source: ruflo-releases
published_at: 2026-07-27T00:22:28+00:00
fetched_at: 2026-07-27T01:30:01.703423+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.12 同时发布两项重要更新。首先，新增 SubagentPermissionDelegate 机制，通过 `swarm init --with-permissions <preset>` 标志为不同角色配置能力清单（支持 strict/standard/permissive 三种预设），生成 .swarm/permissions.jsonl 和附加审计日志 .swarm/permission-audit.jsonl，解决 ClawArena \"privilege-granting 是编排第 1 瓶颈\" 的问题。其次，移除了 Flash Attention 的不可靠性能声明（原\"2.49x-7.47x speedup\"），改为保守描述\"integration available; measured speedup pending benchmark\"，反映出对文档可信度的严谨态度。"
key_points:
  - "权限管理系统：strict/standard/permissive 三级预设，支持角色级能力清单和完整审计追踪"
  - "可信度修复：删除未验证的 Flash Attention 性能声明，改为\"待基准测试\"（文档完整性改善）"
  - "架构分层：权限元数据 + 审计层由 Claude Code 的 Task 工具负责运行时执行"
tags: [ruflo, subagent-permissions, swarm-orchestration, documentation-integrity]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.12 — SubagentPermissionDelegate (#2768) + Flash Attention credibility cleanup (#2739 dream)

Ruflo v3.32.12 同时发布两项重要更新。首先，新增 SubagentPermissionDelegate 机制，通过 `swarm init --with-permissions <preset>` 标志为不同角色配置能力清单（支持 strict/standard/permissive 三种预设），生成 .swarm/permissions.jsonl 和附加审计日志 .swarm/permission-audit.jsonl，解决 ClawArena "privilege-granting 是编排第 1 瓶颈" 的问题。其次，移除了 Flash Attention 的不可靠性能声明（原"2.49x-7.47x speedup"），改为保守描述"integration available; measured speedup pending benchmark"，反映出对文档可信度的严谨态度。

### 重點
- 权限管理系统：strict/standard/permissive 三级预设，支持角色级能力清单和完整审计追踪
- 可信度修复：删除未验证的 Flash Attention 性能声明，改为"待基准测试"（文档完整性改善）
- 架构分层：权限元数据 + 审计层由 Claude Code 的 Task 工具负责运行时执行

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.12)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Two dream-cycle items shipped together. 
 Fixed / Added 
 
 
 #2768 SubagentPermissionDelegate — new swarm init --with-permissions &lt;preset&gt; flag ships a per-role capability manifest to .swarm/permissions.jsonl and seeds an append-only audit trail at .swarm/permission-audit.jsonl . Presets: strict , standard , permissive . Metadata + audit layer only — Claude Code's Task tool owns runtime enforcement. E2E verified in a fresh scratch cwd: 3 role rows + 3 granted events written, state.json records the preset, bogus presets fail cleanly at parse time. Closes the ClawArena "privilege-granting is #1 orchestration bottleneck" gap from arXiv 2606.31174. 
 
 
 #2739 Flash Attention credibility cleanup — dropped the "2.49x-7.47x speedup" claim from all 5 CLAUDE.md sites. It was inherited from upstream marketing and never reproduced in-tree. Every dream-cycle for 7+ nights flagged it as a credibility drag. Doc now reads "integration available; measured speedup pending benchmark" and explains WHY the number was dropped. 
 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.12 
 Refs: dream-cycles #2727 #2739 #2752 #2760 #2763 #2768 #2778 #2783 (Flash Attention flagged repeatedly), #2768 (ClawArena).

</details>