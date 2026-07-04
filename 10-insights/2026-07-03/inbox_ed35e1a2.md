---
id: inbox_ed35e1a2
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-repowise-releases-v0-26-0-8b30]]"
title: "v0.26.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.26.0
source: repowise-releases
published_at: 2026-07-03T11:46:01+00:00
fetched_at: 2026-07-04T01:23:13.266468+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise 發布 v0.26.0，主要新增 VS Code 擴展與架構可視化功能。新版本包含編輯器原生信號（診斷、風險評分、重構提示）、持續縮放的架構圖構建器、決策嵌入的批次優化，以及機器可讀界面和死代碼偵測。VS Code 擴展已支援伺服器生命週期管理、MCP 註冊、側邊欄儀表板、主題切換，並修復了高度依賴項安全漏洞。此版本為 Repowise 與 IDE 深度整合的重要里程碑。"
key_points:
  - "VS Code extension 含伺服器生命週期管理、MCP 支援、編輯器原生診斷與風險評分"
  - "新增 zoom-map builder 實現連續縮放的架構圖視圖，支援實時風險評分"
  - "批次決策嵌入優化、修復高度/關鍵 CVE（npm + Python）"
tags: [repowise, vscode-extension, mcp, architecture-viz, dev-tools]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.26.0

Repowise 發布 v0.26.0，主要新增 VS Code 擴展與架構可視化功能。新版本包含編輯器原生信號（診斷、風險評分、重構提示）、持續縮放的架構圖構建器、決策嵌入的批次優化，以及機器可讀界面和死代碼偵測。VS Code 擴展已支援伺服器生命週期管理、MCP 註冊、側邊欄儀表板、主題切換，並修復了高度依賴項安全漏洞。此版本為 Repowise 與 IDE 深度整合的重要里程碑。

### 重點
- VS Code extension 含伺服器生命週期管理、MCP 支援、編輯器原生診斷與風險評分
- 新增 zoom-map builder 實現連續縮放的架構圖視圖，支援實時風險評分
- 批次決策嵌入優化、修復高度/關鍵 CVE（npm + Python）

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.26.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's Changed 
 
 MCP get_answer/get_context tuning + in-code rationale retrieval by @RaghavChamadiya in #621 
 MCP get_answer: frame-grounding gate + in-code rationale anchoring by @RaghavChamadiya in #622 
 feat(server): zoom-map builder for a continuous-zoom architecture view by @RaghavChamadiya in #626 
 perf(core): batch decision embeddings in persistence and reindex by @swati510 in #641 
 feat: machine-readable interfaces, live range risk scoring, dead-code line spans, shared API client by @RaghavChamadiya in #642 
 feat: VS Code extension with server lifecycle, onboarding, and MCP registration by @RaghavChamadiya in #643 
 feat(vscode): editor-native signals - diagnostics, trees, branch risk, refactoring lens, docs by @RaghavChamadiya in #644 
 feat(vscode): visualization panels from the shared UI library by @RaghavChamadiya in #649 
 feat(vscode): sidebar home dashboard with freshness and theme switcher by @RaghavChamadiya in #650 
 fix(update): keep the index freshness stamp current on no-op syncs by @RaghavChamadiya in #652 
 feat(vscode): trim webview bundle, graph panels, a11y, and release tooling by @RaghavChamadiya in #653 
 feat(vscode): settings panel for editor signals and server config by @RaghavChamadiya in #654 
 feat(embeddings): make Ollama embed timeout configurable via env by @austintraver in #656 
 chore(vscode): release extension 0.1.1 by @RaghavChamadiya in #659 
 fix(deps): clear high/critical dependency CVEs (npm + Python) by @RaghavChamadiya in #645 
 feat(vscode): editor-native UX pass with panel navigation and quieter defaults by @RaghavChamadiya in #660 
 fix: hide config languages from language usage by @cnYui in #623 
 release: v0.26.0 — VS Code extension, zoom architecture view, web build fix by @RaghavChamadiya in #661 
 fix(web): declare @repowise-dev/api-client dependency (unblocks v0.26.0 publish) by @RaghavChamadiya in #662 
 
 New Contributors 
 
 @austintraver made their first contribution in #656 
 @cnYui made their first contribution in #623 
 
 Full Changelog : v0.25.0...v0.26.0

</details>