---
id: inbox_28efdcea
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-hermes-agent-releases-clean-before-remerge-pluginify-provider-7707]]"
title: "clean-before-remerge: Pluginify provider/platform/terminal backends"
url: https://github.com/NousResearch/hermes-agent/releases/tag/clean-before-remerge
source: hermes-agent-releases
published_at: 2026-05-29T13:28:00+00:00
fetched_at: 2026-05-30T02:23:14.078954+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent 架构重构提案：将 provider 适配器（Anthropic、Bedrock、Azure）、platform 适配器（Telegram、Slack、Discord、Feishu、DingTalk、Matrix）和 terminal 后端（Modal、Daytona）从核心库移出至 plugins/ 工作区成员。核心模块通过 plugin registry（get_provider_namespace、get_provider_service 等）的懒加载引用替代直接导入，减少核心依赖耦合。此次迁移涉及98个文件重定位，所有导入已验证无死代码；测试套件已重新适配 registry 挂钩机制。该重构实现了适配器的完全解耦，使扩展新 provider/platform 无需修改核心代码。"
key_points:
  - "98 个文件重定位至 plugins/，核心通过 plugin registry（get_provider_service 等）懒加载引用适配器，而非直接导入，降低核心的 shipping 体积和依赖耦合"
  - "Anthropic 凭证发现和 OAuth-masquerade 守卫迁入插件的 credential_pool_hook，browser-open 操作通过 _can_open_graphical_browser 保护"
  - "17 个被移动模块的导入进行烟雾测试，验证零死导入；pyproject extras 和 nix 变体按平台聚合工作区成员"
tags: [hermes-agent, refactor, plugin-architecture, dependency-injection, provider-adapters]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## clean-before-remerge: Pluginify provider/platform/terminal backends

Hermes Agent 架构重构提案：将 provider 适配器（Anthropic、Bedrock、Azure）、platform 适配器（Telegram、Slack、Discord、Feishu、DingTalk、Matrix）和 terminal 后端（Modal、Daytona）从核心库移出至 plugins/ 工作区成员。核心模块通过 plugin registry（get_provider_namespace、get_provider_service 等）的懒加载引用替代直接导入，减少核心依赖耦合。此次迁移涉及98个文件重定位，所有导入已验证无死代码；测试套件已重新适配 registry 挂钩机制。该重构实现了适配器的完全解耦，使扩展新 provider/platform 无需修改核心代码。

### 重點
- 98 个文件重定位至 plugins/，核心通过 plugin registry（get_provider_service 等）懒加载引用适配器，而非直接导入，降低核心的 shipping 体积和依赖耦合
- Anthropic 凭证发现和 OAuth-masquerade 守卫迁入插件的 credential_pool_hook，browser-open 操作通过 _can_open_graphical_browser 保护
- 17 个被移动模块的导入进行烟雾测试，验证零死导入；pyproject extras 和 nix 变体按平台聚合工作区成员

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/clean-before-remerge)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Move provider adapters (anthropic, bedrock, azure), platform adapters 
(telegram, slack, discord, feishu, dingtalk, matrix), and terminal backends 
(modal, daytona) out of core into plugins/ workspace members. Core references 
them via the plugin registries (get_provider_namespace / get_provider_service / 
get_tool_provider / get_credential_pool_hook) instead of direct imports. 
 
 Provider/platform/terminal adapters relocated under plugins/; pyproject 
extras reference workspace members; nix variants aggregate per-platform extras. 
 Anthropic credential discovery + OAuth-masquerade guard live in the plugin's 
credential_pool_hook; browser-open guarded by _can_open_graphical_browser. 
 Vercel AI Gateway + Vercel Sandbox removed (upstream deletion); get_bedrock_model_ids 
removed (replaced by bedrock_model_ids_or_none + discover_bedrock_models). 
 Terminal backends resolve ModalEnvironment / DaytonaEnvironment lazily from 
the plugin registry. 
 uv.lock regenerated against the pluginified workspace. 
 
 Plugin test suites updated for the relocation: imports point at 
hermes_agent_.adapter, caplog logger-name filters and monkeypatch targets 
use the new module paths, and credential/rollback tests patch 
registries.get_provider_service rather than the removed agent.*_adapter modules. 
 Verified: zero dead imports of relocated modules in core (import smoke test + 
rename-map grep); nix develop succeeds; targeted plugin suites green 
(bedrock, anthropic-auxiliary, matrix, dingtalk, feishu, credential_pool, 
switch_model_rollback). Remaining full-suite failures are pre-existing on the 
pre-merge tree (telegram setUpModule code ) or environmental (voice/media/ 
PTY/network-dependent), not introduced here.

</details>