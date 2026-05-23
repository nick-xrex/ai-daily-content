---
id: inbox_6b2b9adc
date: 2026-05-22
source_ref: "[[00-inbox/2026-05-22/1800-gitnexus-releases-release-candidate-v1-6-6-rc-39-c8f5]]"
title: "Release Candidate v1.6.6-rc.39"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.6-rc.39
source: gitnexus-releases
published_at: 2026-05-22T10:10:51+00:00
fetched_at: 2026-05-22T18:06:42.959036+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.6-rc.39 發布，自動化預發行版本，npm install gitnexus@rc。本版本融合多語言分析改進：JavaScript 完成 scope-based resolution 遷移（RFC #909 Ring 3），Kotlin 新增 scope resolver 並強化 smart-cast 型別精化、overload 選擇、MRO 虛擬分派、iterable 跨檔案傳播、method-chain receiver 類型、constructor 型別覆蓋（#1727, #1758-1779），C++ 添加 SFINAE 過濾和 type_traits constraint 擴展。功能面新增 Git worktrees 支持、多語言 wiki（--lang 旗標）、GitLab 倉庫支援。分析堆提升至 16GB（UE5 級倉庫指引），WAL 損壞檢測與復原，Windows EPERM/FTS/Express 5 兼容修復。影響對象為 GitNexus 用戶，特別是 C++、JavaScript、Kotlin 項目。"
key_points:
  - "JavaScript scope-based resolution 遷移（RFC #909 Ring 3, issue #928）完成，改善符號解析"
  - "Kotlin scope resolver + smart-cast、overload 目標選擇、MRO 分派、iterable 傳播、method-chain receiver、constructor override（#1727, #1758-1779）"
  - "C++ SFINAE 過濾 + type_traits registry；分析堆 16GB；Git worktrees、GitLab、多語言 wiki（#1654, #1565, #1613）"
tags: [gitnexus, code-analysis, scope-resolution, kotlin, javascript]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.6-rc.39

GitNexus v1.6.6-rc.39 發布，自動化預發行版本，npm install gitnexus@rc。本版本融合多語言分析改進：JavaScript 完成 scope-based resolution 遷移（RFC #909 Ring 3），Kotlin 新增 scope resolver 並強化 smart-cast 型別精化、overload 選擇、MRO 虛擬分派、iterable 跨檔案傳播、method-chain receiver 類型、constructor 型別覆蓋（#1727, #1758-1779），C++ 添加 SFINAE 過濾和 type_traits constraint 擴展。功能面新增 Git worktrees 支持、多語言 wiki（--lang 旗標）、GitLab 倉庫支援。分析堆提升至 16GB（UE5 級倉庫指引），WAL 損壞檢測與復原，Windows EPERM/FTS/Express 5 兼容修復。影響對象為 GitNexus 用戶，特別是 C++、JavaScript、Kotlin 項目。

### 重點
- JavaScript scope-based resolution 遷移（RFC #909 Ring 3, issue #928）完成，改善符號解析
- Kotlin scope resolver + smart-cast、overload 目標選擇、MRO 分派、iterable 傳播、method-chain receiver、constructor override（#1727, #1758-1779）
- C++ SFINAE 過濾 + type_traits registry；分析堆 16GB；Git worktrees、GitLab、多語言 wiki（#1654, #1565, #1613）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.6-rc.39)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.6-rc.39 \n Target base: 1.6.6 (rc #39 )\n Source commit (main): f72d9a9 \n Release commit (versioned tree): 361342b \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(cpp): sfinae filter by @zander-raycraft in #1623 
 feat(ingestion): Add C++ parameter type class sidecar by @azizur100389 in #1642 
 fix(lbug): issue #1647 , detect WAL corruption in schema init and surface recovery by @NilotpalK in #1650 
 fix(wiki): Remove the hidden 60s default timeout, validate gitnexus wiki timeout/retry flags, and surface timeout errors by @Copilot in #1651 
 fix(ingestion): Raise analyze auto-heap to 16GB and tighten cross-platform OOM guidance for UE5-scale repositories by @Copilot in #1652 
 feat(wiki): added --lang flags to gitnexus wiki for multilanguage wiki generation support by @sanguine59 in #1613 
 feat(detect-changes): support git worktrees by @NilotpalK in #1654 
 fix: Use Ladybug native read-only enforcement and prepared statement execution for Cypher query paths by @Copilot in #1655 
 perf(scope-resolution): use owner-keyed lookup for Step 2 member resolution by @TonyReg in #1657 
 feat(eval-server): added --host for user configured host IP instead of system hardcoded IP (127.0.0.1) by @sanguine59 in #1667 
 fix(test): retry Windows temp cleanup in cli-e2e teardown by @magyargergo in #1688 
 fix(api): open lbug read-only for /api/graph, /api/search, /api/grep by @magyargergo in #1686 
 feat(cpp): Expand type_traits constraint registry by @azizur100389 in #1648 
 feat(javascript): migrate JavaScript to scope-based resolution (RFC #909 Ring 3, issue #928 ) by @ReidenXerx in #1640 
 fix(mcp): setup fallback on Windows when global gitnexus resolves to a non-spawnable shim by @Copilot in #1694 
 fix(lbug): probe-then-load FTS extension on Windows ( #1690 ) by @LocallyInsaneDB in #1692 
 fix(detect-changes): guard resolveWorktreeCwd against overriding a separately-indexed worktree by @NilotpalK in #1691 
 fix(ingestion): Prioritize same-module Java type resolution for duplicate FQNs across modules by @Copilot in #1712 
 feat(cpp): Add pointer nullptr ellipsis conversion ranks by @azizur100389 in #1708 
 feat: Add analyze --repair-fts , enforce FTS verification, and harden repair safeguards by @Copilot in #1720 
 fix(ingestion): surface skipped large-file paths by default ( #1659 ) by @jelsco in #1661 
 fix(eval-server): localhost now doesn't normalize into IPv4 instead lets OS decide which to bind by @sanguine59 in #1722 
 fix(group): Union HTTP graph and source contracts by @azizur100389 in #1709 
 fix(workers): resilient + zero-copy ingestion worker pool — prevent analyze hangs on TS-root-scale loads by @Copilot in #1693 
 feat(ingestion): add Kotlin scope resolver by @ShiningXu in #1727 
 fix(server): restore gitnexus serve startup under Express 5 by @magyargergo in #1749 
 feat(web): add GitLab repository support by @hugogu in #1565 
 fix(lbug): keep serve stable when sidecars are missing by @ChamHerry in #1747 
 fix(analyze): prevent cache-hit native workers from aborting by @ChamHerry in #1751 
 fix(install): materialize vendored grammars to fix Windows EPERM ( #1728 ) by @magyargergo in #1729 
 feat(ingestion): Link object literal methods to exported bindings by @luyua9 in #1718 
 fix(group): detect httpx AsyncClient alias imports by @luyua9 in #1687 
 fix(mcp): disambiguate duplicate-name repo resolution for worktrees by @magyargergo in #1753 
 ci(web): use npm ci for deterministic Vercel installs by @abhigyanpatwari in #1764 
 chore(security): upgrade @vercel/node in gitnexus-web and remediate transitive advisories by @Copilot in #1705 
 fix(cli): apply --no-stats to keep-marker stats line ( #1706 ) by @oddFEELING in #1765 
 fix(lang-kotlin): overload target-id selection by parameter types ( #1761 ) by @magyargergo in #1777 
 fix(lang-kotlin): smart-cast type refinement for when/is and if/is ( #1758 ) by @magyargergo in #1774 
 fix(lang-kotlin): interface default method dispatch via implements-split MRO ( #1763 ) by @magyargergo in #1779 
 fix(lang-kotlin): cross-file iterable return propagation ( #1759 ) by @magyargergo in #1775 
 fix(lang-kotlin): method-chain fixpoint receiver types ( #1760 ) by @magyargergo in #1776 
 fix(lang-kotlin): virtual dispatch via constructor type override ( #1762 ) by @magyargergo in #1778 
 
 New Contributors 
 
 @NilotpalK made their first contribution in #1650 
 @TonyReg made their first contribution in #1657 
 @LocallyInsaneDB made their first contribution in #1692 
 @ChamHerry made their first contribution in #1747 
 @luyua9 made their first contribution in #1718 
 @oddFEELING made their first contribution in #1765 
 
 Full Changelog : v1.6.5...v1.6.6-rc.39

</details>