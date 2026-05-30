---
id: inbox_2bd6438d
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0216-hermes-agent-releases-merge-commit-backup-merge-origin-main-in-b546]]"
title: "merge-commit-backup: Merge origin/main into ethie/oh-god (pluginify refactor reconciliation)"
url: https://github.com/NousResearch/hermes-agent/releases/tag/merge-commit-backup
source: hermes-agent-releases
published_at: 2026-05-28T21:57:55+00:00
fetched_at: 2026-05-30T02:23:14.080026+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent 大型合并操作：协调 pluginify 重构分支与主分支 267 个 commit 的并入。主分支编辑了 515 个文件，本分支移动了 98 个文件至 plugins/；关键冲突点在于主分支修改了被迁移文件的旧路径。最终决策：采纳主分支删除 ai-gateway/vercel_sandbox、保留 tools/lazy_deps.py；agent/credential_pool.py 合并主分支的 OAuth-masquerade 安全修复与本分支的 plugin hook 重定向；CLI 工具重新应用了 pluginify 导入改写。17 个已移动模块的导入进行详尽验证，无冲突标记；21 个目标测试通过，无引入新的失败。"
key_points:
  - "文件路径冲突处理：main 删除 ai-gateway/vercel_sandbox PR #33067，本分支保留 plugins/terminals/vercel/；冲突采纳 main 决策，清理所有孤立引用"
  - "agent/credential_pool.py 安全合并：保留本分支的 plugin-hook 重定向，同时将 main 的 api_key_path_explicit OAuth-masquerade 修复移植至 anthropic credential_pool_hook"
  - "导入验证：17 个被迁移模块的零死导入确认，导入烟雾测试通过，目标测试套件（credential_pool、anthropic plugin、run_agent）均绿"
tags: [hermes-agent, merge, refactor, conflict-resolution, git-strategy]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## merge-commit-backup: Merge origin/main into ethie/oh-god (pluginify refactor reconciliation)

Hermes Agent 大型合并操作：协调 pluginify 重构分支与主分支 267 个 commit 的并入。主分支编辑了 515 个文件，本分支移动了 98 个文件至 plugins/；关键冲突点在于主分支修改了被迁移文件的旧路径。最终决策：采纳主分支删除 ai-gateway/vercel_sandbox、保留 tools/lazy_deps.py；agent/credential_pool.py 合并主分支的 OAuth-masquerade 安全修复与本分支的 plugin hook 重定向；CLI 工具重新应用了 pluginify 导入改写。17 个已移动模块的导入进行详尽验证，无冲突标记；21 个目标测试通过，无引入新的失败。

### 重點
- 文件路径冲突处理：main 删除 ai-gateway/vercel_sandbox PR #33067，本分支保留 plugins/terminals/vercel/；冲突采纳 main 决策，清理所有孤立引用
- agent/credential_pool.py 安全合并：保留本分支的 plugin-hook 重定向，同时将 main 的 api_key_path_explicit OAuth-masquerade 修复移植至 anthropic credential_pool_hook
- 导入验证：17 个被迁移模块的零死导入确认，导入烟雾测试通过，目标测试套件（credential_pool、anthropic plugin、run_agent）均绿

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/merge-commit-backup)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Reconciles the "pluginify everything" refactor (moving provider adapters, 
platform adapters, and terminal backends out of core into plugins/) with 
267 commits of main. main had 515 edits across 635 files; our branch moved 
98 files into plugins/. The dangerous class was main editing files at OLD 
paths that we relocated — handled below. 
 STRUCTURAL DECISIONS 
 
 ai-gateway + vercel_sandbox: honored main's PR #33067 deletion. Dropped our 
orphaned plugins/terminals/vercel/ dir and all 3 stale vercel refs that 
survived in pyproject (workspace member, [all] entry, uv source). 
 tools/lazy_deps.py: kept main's version. Our branch deleted it incompletely 
(WIP) while main has 30 live callers + active maintenance. main's intent won. 
 agent/agent_runtime_helpers.py: COMBINED — main's atomic swap+rollback 
snapshot envelope wraps our pluginified registries-based anthropic imports. 
 agent/credential_pool.py: took our plugin-hook indirection AND ported main's 
api_key_path_explicit OAuth-masquerade security fix INTO the anthropic 
credential_pool_hook (it was pluginified from a pre-fix base and would have 
been silently dropped otherwise). 
 hermes_cli/model_switch.py, hermes_cli/models.py: took main's logic 
(cached_provider_model_ids, AI-gateway removal) then re-applied our pluginify 
import rewrites (agent.bedrock_adapter/anthropic_adapter -&gt; registries 
namespace lookups) since those modules moved to plugins. 
 tools/terminal_tool.py: took main's version (vercel_sandbox deletion) then 
restored our lazy registry resolution for modal + daytona environments 
(both moved to plugins; main's direct imports would crash at runtime). 
 nix/checks.nix: kept both — our hermetic-boundary checks + main's 
messaging-variant discord.py guard. 
 pyproject.toml: plugin extras as workspace members (ours) + main's new wecom 
extra; vercel removed throughout. 
 uv.lock: regenerated with uv lock (not hand-merged); 233 packages. 
 
 VERIFICATION 
 
 Zero conflict markers anywhere. 
 Exhaustive 17-moved-module grep: no dead imports of relocated modules in core. 
 Import smoke test: all hot core modules import clean. 
 Targeted tests (21 files incl. credential_pool, anthropic plugin, 
run_agent, project_metadata): pass. 
 3 credential_pool security tests rewired to register the real plugin hook 
(core tests don't trigger plugin discovery): pass. 
 Full suite: remaining failures are pre-existing on premerge-oh-god (telegram 
collection error: setUpModule MagicMock code ) or environmental (matrix 
DNS/e2ee-deps, network) — NOT introduced by this merge. See PR notes.

</details>