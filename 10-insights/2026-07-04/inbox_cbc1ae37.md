---
id: inbox_cbc1ae37
date: 2026-07-04
source_ref: "[[00-inbox/.../inbox_cbc1ae37]]"
title: "rc/6252aa745f246b36c30d42489fa92367a337eb55: feat(setup): add CodeBuddy and Qoder coding-agent integrations (#2368)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F6252aa745f246b36c30d42489fa92367a337eb55
source: gitnexus-releases
published_at: 2026-07-04T09:54:50+00:00
fetched_at: 2026-07-05T01:42:20.747901+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus PR #2368 提供 Tencent CodeBuddy 和 Alibaba Qoder 編碼代理的 MCP 集成實現細節。CodeBuddy 遵循配置優先順序鏈將 MCP 條目寫入：首選 ~/.codebuddy/.mcp.json（官方推薦位置），次選 ~/.codebuddy/mcp.json（已棄用，避免覆蓋有內容的舊配置），最後 ~/.codebuddy.json（舊版遺留），skills 寫入 ~/.codebuddy/skills/。Qoder 配置則放在 ~/.qoder.json，skills 在 ~/.qoder/skills/。兩者均集成到 editor-targets 註冊表和 --coding-agent 選項，支援完整的 setup 和 uninstall 流程。實現包含跨平台 CI 測試、損壞配置檢測與報告、多候選檔案卸載掃描、國際化文案更新（中英文）等完整的工程化措施。"
key_points:
  - "CodeBuddy 配置優先順序鏈：~/.codebuddy/.mcp.json（推薦）→ ~/.codebuddy/mcp.json（棄用）→ ~/.codebuddy.json（遺留），skills 至 ~/.codebuddy/skills/；Qoder：~/.qoder.json 配置、~/.qoder/skills/ skills"
  - "完整的配置管理實現：支援 setup/uninstall 往返、損壞配置檢測、多候選檔案卸載掃描、legacyFiles 字段支援"
  - "工程質量保證：跨平台 CI 測試、國際化支援（zh-CN、en）、setup 描述文案更新、Kilo Code + GitNexus MCP 設置指南文檔"
tags: [gitnexus, mcp-integration, codebuddy, qoder, coding-agents]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/6252aa745f246b36c30d42489fa92367a337eb55: feat(setup): add CodeBuddy and Qoder coding-agent integrations (#2368)

GitNexus PR #2368 提供 Tencent CodeBuddy 和 Alibaba Qoder 編碼代理的 MCP 集成實現細節。CodeBuddy 遵循配置優先順序鏈將 MCP 條目寫入：首選 ~/.codebuddy/.mcp.json（官方推薦位置），次選 ~/.codebuddy/mcp.json（已棄用，避免覆蓋有內容的舊配置），最後 ~/.codebuddy.json（舊版遺留），skills 寫入 ~/.codebuddy/skills/。Qoder 配置則放在 ~/.qoder.json，skills 在 ~/.qoder/skills/。兩者均集成到 editor-targets 註冊表和 --coding-agent 選項，支援完整的 setup 和 uninstall 流程。實現包含跨平台 CI 測試、損壞配置檢測與報告、多候選檔案卸載掃描、國際化文案更新（中英文）等完整的工程化措施。

### 重點
- CodeBuddy 配置優先順序鏈：~/.codebuddy/.mcp.json（推薦）→ ~/.codebuddy/mcp.json（棄用）→ ~/.codebuddy.json（遺留），skills 至 ~/.codebuddy/skills/；Qoder：~/.qoder.json 配置、~/.qoder/skills/ skills
- 完整的配置管理實現：支援 setup/uninstall 往返、損壞配置檢測、多候選檔案卸載掃描、legacyFiles 字段支援
- 工程質量保證：跨平台 CI 測試、國際化支援（zh-CN、en）、setup 描述文案更新、Kilo Code + GitNexus MCP 設置指南文檔

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F6252aa745f246b36c30d42489fa92367a337eb55)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# rc/6252aa745f246b36c30d42489fa92367a337eb55: feat(setup): add CodeBuddy and Qoder coding-agent integrations (#2368)

feat(setup): add CodeBuddy and Qoder coding-agent integrations 
 
 Adds Tencent CodeBuddy and Alibaba Qoder to gitnexus setup/uninstall, 
fitted to the editor-targets registry and --coding-agent selection. 
 
 CodeBuddy: MCP entry written into the first existing file of its 
documented priority chain (~/.codebuddy/.mcp.json recommended, 
~/.codebuddy/mcp.json deprecated, ~/.codebuddy.json legacy) so a 
populated deprecated config is never shadowed; skills to 
~/.codebuddy/skills/ ( https://www.codebuddy.ai/docs/cli/mcp ) 
 Qoder: MCP entry in ~/.qoder.json, skills to ~/.qoder/skills/ 
( https://docs.qoder.com/cli/using-cli , /extensions/skills) 
 editor-targets gains optional legacyFiles; uninstall sweeps them 
 roster strings updated (CLI help, i18n en/zh-CN, READMEs); en/zh-CN 
setup descriptions were stale (missing Antigravity) and are refreshed 
 
 Supersedes and credits PR #1030 by @zykai0302 , re-fitted to the 
post- #2168 selective-agent architecture with documented config paths. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 
 test(cli): assert stable zh-CN setup-description fragment 
 
 
 fix(setup): surface non-ENOENT config read/stat failures instead of clobbering 
 
 
 fix(setup): report corrupt legacy MCP files informationally during uninstall 
 
 
 test(setup): cover multi-candidate uninstall sweep combinations 
 
 
 fix(setup): detect CodeBuddy/Qoder installs via existing MCP config files 
 
 
 fix(setup): skip empty and non-file candidates in the MCP config chain 
 
 
 docs: add CodeBuddy and Qoder manual MCP configuration sections 
 
 
 test(ci): run the setup-uninstall round-trip in the cross-platform matrix 
 
 
 fix(setup): never claim "not configured" when uninstall recorded errors 
 
 
 refactor(cli): share the isEnoent predicate via editor-targets 
 
 
 refactor(setup): share chain-file install detection between CodeBuddy and Qoder 
 
 
 
 Co-authored-by: Claude Fable 5 noreply@anthropic.com

</details>