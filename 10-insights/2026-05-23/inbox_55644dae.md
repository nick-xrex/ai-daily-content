---
id: inbox_55644dae
date: 2026-05-23
source_ref: "[[00-inbox/.../inbox_55644dae]]"
title: "Release Candidate v1.6.6-rc.45"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.6-rc.45
source: gitnexus-releases
published_at: 2026-05-23T06:28:54+00:00
fetched_at: 2026-05-24T04:26:46.777527+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.6-rc.45 發布候選版本，功能與 rc.46 相同，包含 Kotlin 型別系統 5 項修復、JavaScript scope-based resolution 遷移、C++ SFINAE 和 type-traits 擴展。性能改進：owner-keyed member resolution lookup、zero-copy ingestion worker pool。支持 Git worktree、多語言 wiki、Windows FTS/Cypher 相容性修復。此版本為舊版 RC，內容基本重複，已被後續版本取代。"
key_points:
  - "Kotlin 型別系統 5 項修復、JavaScript scope-based resolution、C++ 類型約束擴展"
  - "owner-keyed lookup、zero-copy worker pool、FTS 相容性加固"
  - "Git worktree、多語言支持、Windows Cypher 讀寫分離優化"
tags: [gitnexus, rc-release]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.6-rc.45

GitNexus v1.6.6-rc.45 發布候選版本，功能與 rc.46 相同，包含 Kotlin 型別系統 5 項修復、JavaScript scope-based resolution 遷移、C++ SFINAE 和 type-traits 擴展。性能改進：owner-keyed member resolution lookup、zero-copy ingestion worker pool。支持 Git worktree、多語言 wiki、Windows FTS/Cypher 相容性修復。此版本為舊版 RC，內容基本重複，已被後續版本取代。

### 重點
- Kotlin 型別系統 5 項修復、JavaScript scope-based resolution、C++ 類型約束擴展
- owner-keyed lookup、zero-copy worker pool、FTS 相容性加固
- Git worktree、多語言支持、Windows Cypher 讀寫分離優化

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.6-rc.45)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.6-rc.45

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.6-rc.45 \n Target base: 1.6.6 (rc #45 )\n Source commit (main): 84ac88a \n Release commit (versioned tree): 39739e3 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 feat(ingestion): log deferred resolution progress when verbose ( #1741 ) by @magyargergo in #1773 
 docs(lang-kotlin): refresh scope-resolver JSDoc after #1758 - #1763 landed by @magyargergo in #1781 
 feat(cpp): Resolve overloaded operator calls by @azizur100389 in #1754 
 fix(lbug): add WAL checkpoint-threshold control by @Copilot in #1772 
 feat(i18n): make web and CLI language-aware by @ChamHerry in #1748 
 
 New Contributors 
 
 @NilotpalK made their first contribution in #1650 
 @TonyReg made their first contribution in #1657 
 @LocallyInsaneDB made their first contribution in #1692 
 @ChamHerry made their first contribution in #1747 
 @luyua9 made their first contribution in #1718 
 @oddFEELING made their first contribution in #1765 
 
 Full Changelog : v1.6.5...v1.6.6-rc.45

</details>