---
id: inbox_9b2d5d5b
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F1408bfbffe69422e7db3f004d1cbc556b1634c41"
author: "magyargergo"
published_at: 2026-07-08T17:34:05+00:00
fetched_at: 2026-07-09T22:07:22.246252+00:00
content_hash: "222fcc863e974d30167b8bf1c029b7351e162a7809ffb0606d77657a065fefbd"
lang: en
caption_quality: None
raw: true
topics: []
---

# rc/1408bfbffe69422e7db3f004d1cbc556b1634c41: fix(hook): emit MCP query hint when server owns DB lock (#2396) (#2397)

fix(hook): emit MCP query hint when server owns DB lock ( #2396 ) 
 
 When the GitNexus MCP server holds the lbug write lock, the PreToolUse hook's CLI augment cannot run (LadybugDB is single-writer) and previously skipped silently — disabling graph augmentation in the most common deployment (server online). Since the same session already has the MCP query tool live, the owner branch now emits an additionalContext hint pointing the agent at mcp__gitnexus__query for that pattern, via the same sanctioned stdout channel the augment-success path uses (Codex-safe, #2369 ). 
 Rejected the alternative of having the hook query the server: it runs over stdio (no port/pipe from the separate hook process) and cross-process read-only access can't coexist with the write lock — both are large architecture changes. Applied to all three gated hook copies (claude .cjs, claude-plugin .js, antigravity .cjs); the cursor hook has no owner gate and is untouched. The stderr augment skipped: MCP server owns DB diagnostic stays GITNEXUS_DEBUG-gated ( #1913 ). Owner-path tests flipped from stdout-empty to hint-present. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 fix(hook): reword MCP-query hint to be conditionally truthful ( #2396 ) 
 
 The #2396 owner branch emits the hint on every DB-owner path — a confirmed 
 gitnexus mcp owner, a gitnexus serve owner, and the fail-closed/timeout 
paths (the probe collapses timeout and owned to one boolean). The old text 
claimed "Knowledge graph is live via the MCP server" and named 
mcp__gitnexus__query unconditionally, which is untrue on a fail-closed probe 
where no server is confirmed and misdirecting for a serve-only owner 
(review C2/C4). 
 Reword the hint (byte-identical across all three hook copies) to state that 
local augment is unavailable and to condition the MCP call on the tools 
actually being live ("if the GitNexus MCP tools are live in this session"). 
This is truthful on every owner path; the needles the assertions rely on 
(mcp__gitnexus__query, query, search_query, the pattern) are preserved. 
 Fix the 10 stale owner/fail-closed unit tests that still asserted empty 
stdout (review C1, the macOS platform-sensitive 2/3 blocker): flip them to 
assert the hint via parseHookOutput, keep their stderr/GITNEXUS_DEBUG 
expectations, and rename the two 'SILENTLY' titles. The GITNEXUS_DEBUG='' 
owner-hint case is restored (the PR's new loop only covered '0'/'false'). 
Probe and its white-box tests untouched. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 fix(hook): de-orphan the JSDoc in the claude hook copy ( #2396 ) 
 
 The #2396 change inserted buildMcpQueryHint between the pre-existing 
"PreToolUse handler" JSDoc and handlePreToolUse, orphaning that doc onto the 
helper and leaving handlePreToolUse undocumented (review C5). Move the helper 
(with its own doc) above the handler doc so the "PreToolUse handler" comment 
again precedes handlePreToolUse, matching the clean plugin copy. Pure move; no 
behavior change. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 fix(hook): throttle the MCP-owner hint to once per repo per window ( #2396 ) 
 
 Previously the hint emitted on every qualifying search while a GitNexus process 
owned the DB, so an owner-locked session (the common deploy) was nudged toward 
the MCP query tool on every Grep/Glob/Bash — context bloat and ~2x query 
amplification (review C3). 
 Add shouldEmitMcpHint(gitNexusDir) to all three hook copies: a per-repo 
.gitnexus/.mcp-hint-shown mtime marker emits the hint at most once per window. 
Window via GITNEXUS_MCP_HINT_THROTTLE_MS (default 10min; 0/invalid disables). 
Best-effort — any fs error falls back to emitting, so the hint is never lost to 
a marker failure. The stderr skip diagnostic still fires regardless (only the 
hint is throttled). 
 Tests: hookEnv disables the throttle by default (gitNexusDir is shared across 
the suite, so a marker would otherwise throttle sibling owner tests); a dedicated 
macOS-lane test sets a real window and asserts emit-then-throttle with the marker 
gating it. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 docs(hook): README reflects the MCP-owner query hint, not a silent skip ( #2396 ) 
 
 The 'Hook augmentation/notifications are silently skipped' section still 
described the MCP-server-owns-DB path as a silent augmentation skip (review 
docs finding). That path now hands the agent a conditional MCP-query hint via 
additionalContext (throttled per repo). Reword the section to describe the hint 
and its GITNEXUS_MCP_HINT_THROTTLE_MS throttle, and keep the GITNEXUS_DEBUG 
stderr-diagnostic guidance. No CHANGELOG edit (owned at release time). 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 test(hook): guard hint-copy drift + pattern JSON-escaping ( #2396 ) 
 
 Two gaps the review flagged (R7): 
 
 Drift guard: buildMcpQueryHint and shouldEmitMcpHint are triplicated across 
the three hook copies with no shared module. A source-level byte-identity 
check (runs on every platform, unlike the macOS-only owner tests) fails if any 
copy diverges — the institutional pattern the repo already uses for mirrored 
hook metadata. 
 Escaping: an adversarial Grep pattern (embedded quote + newline) must not 
break the additionalContext JSON envelope. A macOS-lane owner test drives the 
real hook with such a pattern and asserts parseHookOutput still yields valid 
JSON containing the literal characters (JSON.stringify escapes them). 
 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 Co-authored-by: Claude Opus 4.8 (1M context) noreply@anthropic.com