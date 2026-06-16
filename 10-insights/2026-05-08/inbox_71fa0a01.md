---
id: inbox_71fa0a01
date: 2026-05-08
source_ref: "[[00-inbox/.../inbox_71fa0a01]]"
title: "v13.0.0 — Server Beta + Apache 2.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.0.0
source: claude-mem-releases
published_at: 2026-05-08T08:27:13+00:00
fetched_at: 2026-06-16T00:45:05.928497+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.0.0 大版本发布，引入三大变更。其一：Server Beta 可选运行时——独立服务生命周期、Postgres 持久化存储、BullMQ+Redis 队列引擎（via CLAUDE_MEM_QUEUE_ENGINE=bullmq，快速失败）、/v1 RESTful API（events/sessions/memories/search/context/audit/jobs 端点）、API-key 认证 + Better-Auth 代理、Outbox 模式保证事件-工作流事务一致性、Docker Compose + E2E 测试栈。其二：许可证迁移 AGPL-3.0 → Apache-2.0，新增 NOTICE 文件与 docs/license.md、docs/ip-boundary.md 阐明开源/商业边界，ragtime 子项目同步迁移。其三：Server Beta 作为可选安装项（默认关闭），既有 worker 用户无破坏性变更，保留 SQLite 存储与现有端口；完整迁移指南见 docs/migration-worker-to-server.md。兼容性：Node ≥20、Bun ≥1.0；Server Beta 需 Postgres+Redis。"
key_points:
  - "Server Beta 架构：Postgres 事务存储 + BullMQ/Redis 队列 + /v1 RESTful API（events/sessions/memories/search/context/audit/jobs）+ Outbox 模式保证事件-工作流一致性；可选启用，SQLite worker 继续运作"
  - "AGPL-3.0 → Apache-2.0 relicense：IP 边界明确化（docs/ip-boundary.md），商业能力与开源核心分离；ragtime 子项目同步迁移"
  - "向后兼容设计：既有 worker-era 用户零强制升级；Server Beta opt-in；迁移路径文档化（docs/migration-worker-to-server.md）"
tags: [claude-mem, server-infrastructure, postgres, redis, rest-api, outbox-pattern]
topics: [agents.mcp]
importance: 5
novelty: 5
insight_quality: 4
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## v13.0.0 — Server Beta + Apache 2.0

claude-mem v13.0.0 大版本发布，引入三大变更。其一：Server Beta 可选运行时——独立服务生命周期、Postgres 持久化存储、BullMQ+Redis 队列引擎（via CLAUDE_MEM_QUEUE_ENGINE=bullmq，快速失败）、/v1 RESTful API（events/sessions/memories/search/context/audit/jobs 端点）、API-key 认证 + Better-Auth 代理、Outbox 模式保证事件-工作流事务一致性、Docker Compose + E2E 测试栈。其二：许可证迁移 AGPL-3.0 → Apache-2.0，新增 NOTICE 文件与 docs/license.md、docs/ip-boundary.md 阐明开源/商业边界，ragtime 子项目同步迁移。其三：Server Beta 作为可选安装项（默认关闭），既有 worker 用户无破坏性变更，保留 SQLite 存储与现有端口；完整迁移指南见 docs/migration-worker-to-server.md。兼容性：Node ≥20、Bun ≥1.0；Server Beta 需 Postgres+Redis。

### 重點
- Server Beta 架构：Postgres 事务存储 + BullMQ/Redis 队列 + /v1 RESTful API（events/sessions/memories/search/context/audit/jobs）+ Outbox 模式保证事件-工作流一致性；可选启用，SQLite worker 继续运作
- AGPL-3.0 → Apache-2.0 relicense：IP 边界明确化（docs/ip-boundary.md），商业能力与开源核心分离；ragtime 子项目同步迁移
- 向后兼容设计：既有 worker-era 用户零强制升级；Server Beta opt-in；迁移路径文档化（docs/migration-worker-to-server.md）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.0.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.0.0 — Server Beta + Apache 2.0

Highlights 
 This is the claude-mem 13 major release, landing the Server Beta runtime and the project's relicense. 
 Server Beta runtime (opt-in) 
 
 Independent server-beta service with its own lifecycle ( claude-mem server start/status/stop ) 
 Postgres-backed observation storage 
 BullMQ + Redis observation queue engine (gated behind CLAUDE_MEM_QUEUE_ENGINE=bullmq , fail-fast) 
 New /v1 REST API surface (events, sessions, memories, search, context, audit, jobs) 
 API-key auth + Better-Auth proxy 
 Outbox pattern for transactional event-to-job pipelines 
 Generation-job primitives ( ServerJobQueue , ActiveServerBetaQueueManager , deterministic colon-free SHA-256 job IDs) 
 Docker Compose + E2E harness for the new stack 
 
 Licensing 
 
 Repository relicensed from AGPL-3.0 to Apache-2.0 
 NOTICE file added 
 docs/license.md and docs/ip-boundary.md clarify the OSS / commercial boundary 
 ragtime/ subproject also relicensed to Apache-2.0 
 
 Installer 
 
 Server Beta is exposed as an installer option (default off — open-source core is unaffected) 
 
 Migration notes 
 
 Existing users on the worker-era plugin keep working — no breaking changes for the default install 
 Server Beta is opt-in. Worker continues to run on its existing port and SQLite store. 
 See docs/migration-worker-to-server.md for forward-looking migration guidance 
 
 Compatibility 
 
 Node ≥ 20, Bun ≥ 1.0 
 Server Beta requires Postgres + Redis (only when enabled) 
 
 Full diff: v12.7.5...v13.0.0

</details>