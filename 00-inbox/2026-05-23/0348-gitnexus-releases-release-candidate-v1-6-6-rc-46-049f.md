---
id: inbox_37ff7a8f
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.6-rc.46"
author: "github-actions[bot]"
published_at: 2026-05-23T07:11:24+00:00
fetched_at: 2026-05-24T03:48:29.973565+00:00
content_hash: "049f1969d83e8e74a76a743ad98d020c6eb16dbfc6d09557072472aeffb33143"
lang: en
caption_quality: None
raw: true
topics: []
---

# Release Candidate v1.6.6-rc.46

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.6-rc.46 \n Target base: 1.6.6 (rc #46 )\n Source commit (main): 51e6678 \n Release commit (versioned tree): e045d97 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 feat(lang-kotlin): flip Kotlin to MIGRATED_LANGUAGES + close #1756 / #1757 (refs #1746 ) by @magyargergo in #1782 
 
 New Contributors 
 
 @NilotpalK made their first contribution in #1650 
 @TonyReg made their first contribution in #1657 
 @LocallyInsaneDB made their first contribution in #1692 
 @ChamHerry made their first contribution in #1747 
 @luyua9 made their first contribution in #1718 
 @oddFEELING made their first contribution in #1765 
 
 Full Changelog : v1.6.5...v1.6.6-rc.46