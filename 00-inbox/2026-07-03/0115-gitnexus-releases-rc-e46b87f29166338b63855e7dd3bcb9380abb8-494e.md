---
id: inbox_f56913ed
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fe46b87f29166338b63855e7dd3bcb9380abb838f"
author: "magyargergo"
published_at: 2026-07-03T19:55:27+00:00
fetched_at: 2026-07-04T01:15:47.909746+00:00
content_hash: "494e78be45924dadc5cf5bb08b0391ea1d11294640c52547d0318f2647e0c303"
lang: en
caption_quality: None
raw: true
topics: []
---

# rc/e46b87f29166338b63855e7dd3bcb9380abb838f: feat: flat workspace index follows the checked-out branch (#2364)

feat: flat workspace index follows the checked-out branch ( #2354 ) 
 
 A plain gitnexus analyze now always targets the flat workspace slot, 
updating it incrementally across branch switches instead of auto-routing 
non-owner branches into branches/&lt;slug&gt;/ sub-indexes (disk bloat) or 
nagging with the primary-inversion "run gitnexus clean" warning. No new 
CLI flag or config key: the smart behavior is the default. 
 
 Placement: only explicit --branch consults resolveBranchPlacement; 
plain runs resolve to the flat slot, meta.branch becomes an 
informational "last analyzed branch" label restamped each run. 
 Fast path: a same-commit clean-tree branch flip restamps the label and 
registry entry (adoptFlatBranchLabel, no-op for unregistered repos). 
 Shadow cleanup: when the flat slot adopts a label that has a pinned 
sub-index, the now-unreachable branches/&lt;slug&gt;/ dir and its registry 
summary are removed together. 
 MCP: applyBranchScope always falls back to the on-disk flat meta before 
throwing "not indexed", so long-lived servers resolve a freshly 
restamped workspace branch. 
 status: no more "current branch not indexed" dead end — falls through 
to the workspace index with an informational line and the usual 
commit-based staleness verdict. 
 Deleted primaryInversionWarning; explicit --branch pinning, the 
checkout-mismatch guard, detached-HEAD/CI behavior, and clean --branch are unchanged. 
 
 Supersedes the flag-based approaches in #2358 / #2359 . 
Closes #2354 . 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(storage): check registry before deleting shadowed sub-index ( #2364 review F2) 
 
 adoptFlatBranchLabel ran the branches// rm before its own 
unregistered-repo no-op check, so a repo in the #2264 half-finalized 
state (up to date but unregistered) lost its pinned sub-index on a 
same-commit branch flip while the run still failed. The registry 
lookup now precedes the deletion, making the no-self-heal rule 
( #2264 / #1169 ) cover disk as well as registry state. 
 The 'never self-heals' unit test now materializes a sub-index dir and 
asserts it survives; the run-analyze #2354 fast-path test registers 
its repo under an isolated GITNEXUS_HOME (deletion is only legitimate 
for registered repos) with a new unregistered variant pinning 
dir survival. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(storage): keep branch summary when sub-index rm fails ( #2364 review F4) 
 
 The shadow-cleanup fs.rm swallowed every error while the registry 
summary was dropped unconditionally. On Windows an lbug held open by a 
live MCP server fails the rm with EBUSY/EPERM, and once the summary is 
gone 'clean --branch' can never target the leftover dir (it resolves 
solely via the recorded summary) — stranding the exact un-cleanable 
disk bloat adoptFlatBranchLabel exists to prevent. 
 The summary is now dropped only when the directory is verifiably gone 
(post-rm existence check); on failure the summary is retained, a 
warning names the path and errno, and the informational branch label 
still restamps. Later adopts retry the rm. 
 New repo-manager-rm-failure.test.ts uses the delegating fs/promises 
mock idiom (vi.spyOn cannot intercept ESM namespace exports). 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(core): restamp fast path adopt-first and tolerate read-only storage ( #2364 review F3) 
 
 The fast-path label sync stamped meta before adoptFlatBranchLabel, so 
a crash or adopt failure between the two flipped the retry guard 
(existingMeta.branch !== branchLabel) and locked in the partial state: 
every subsequent same-commit run skipped the cleanup and branch-scoped 
queries kept routing to the stale pinned sub-index. The block also sat 
outside any try/catch, so a same-commit branch flip on a read-only 
.gitnexus mount (the documented Docker :ro workflow, #1549 ) failed a 
byte-for-byte-current analyze over a purely informational label sync. 
 Adopt now runs first and saveMeta last — any partial failure leaves 
the guard true and the next run self-heals — and the whole sync is 
best-effort: read-only errors warn citing #1549 , anything else warns 
and retries next run. Safe because the block only fires on a 
same-commit clean tree, where the flat DB content is byte-valid for 
both labels. isReadOnlyFilesystemError is now exported. 
 New run-analyze-adopt-failure.test.ts covers retry-after-partial- 
failure, adopt-before-stamp ordering, and EROFS/EACCES/EPERM (gaps 4 
and 7); a detached-HEAD fast-path pin lands in run-analyze.test.ts 
(gap 6). 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(mcp): make flat meta authoritative in applyBranchScope ( #2364 review F1) 
 
 applyBranchScope trusted two pieces of cached state before its flat- 
meta disk fallback, and the handle cache only refreshes on a resolve 
miss — never on a hit. Post- #2354 that stale window is the routine 
case: (i) the handle.branch early-return served the flat handle under 
the OLD label after a workspace flip, silently returning the new 
branch's content as the old branch (the pool staleness reinit hot- 
swaps content without updating handle.branch); (ii) a stale cached 
branches[] summary routed to a branches// dir that 
adoptFlatBranchLabel had already deleted (raw 'LadybugDB not found' or 
POSIX ghost reads with staleness detection blinded). 
 The on-disk flat meta is now read before any cached-state trust. A 
branches[] summary is served only when its sub-index lbug actually 
exists (the lbug is what the pool opens — serviceability truth); the 
cached label is trusted only when no readable flat meta contradicts it 
( #2106 R4 legacy shapes preserved). One refreshRepos() fires on 
detected staleness so subsequent calls see fresh handles. Safe against 
mid-analyze reads: dirty stamps spread the existing meta, preserving 
the old label until the end-of-run atomic write. 
 Fixtures now materialize the pinned sub-index lbug; new regressions 
cover the stale-old-label error, adopted-summary fall-through to flat, 
and the dangling-summary partial-failure window (test gaps 1-2). 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(core): make end-of-run branch-label sync best-effort ( #2364 review F5) 
 
 The end-of-run adoptFlatBranchLabel sat inside the pipeline try whose 
catch rethrows, so a registry write failure (ENOSPC, ~/.gitnexus 
perms) after a successful multi-minute analyze failed the whole run — 
even though the index was complete and registered, the neighbouring 
parse-cache save is deliberately wrapped for exactly this reason, and 
adopt retries unconditionally on the next plain analyze. It now warns 
and continues, mirroring the parse-cache wrapper. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(mcp): correct branch-not-indexed guidance for workspace index ( #2364 review F6) 
 
 The error told users to 'Run: gitnexus analyze --branch ', but 
post- #2354 that command hard-errors unless X is checked out — and this 
message is now the common goodbye for a formerly-indexed branch whose 
sub-index the workspace slot adopted. The guidance now explains that 
the workspace index follows the checked-out branch and leads with the 
checkout; the '(primary only)' fallback becomes '(workspace only)'. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 docs: align primary/workspace vocabulary with the #2354 inversion ( #2364 review F7) 
 
 The review flagged pre-inversion 'primary/non-primary' wording that 
now misleads readers about the placement model: the isPrimaryBranch 
JSDoc (field name kept — public API surface), the two branches? JSDoc 
comments in local-backend, the base_ref gate comment in cli/analyze, 
and four branch-scope test names. Comment/JSDoc/test-name edits only; 
'Registry-primary' and 'primary key' senses untouched. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(cli): clarify workspace index status wording ( #2364 review F8) 
 
 'gitnexus analyze follows this branch' was ambiguous about WHICH 
branch analyze follows — the recorded one on the line or the current 
checkout. Both locales now say a re-run follows the current branch. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(storage): re-read registry after the shadow rm in adoptFlatBranchLabel 
 
 The F2 reorder moved the registry read to the top of the function, so 
the whole-file writeRegistry at the bottom persisted a snapshot taken 
BEFORE the recursive rm of an entire sub-index — widening the unlocked 
read-modify-write window from microseconds to the duration of a multi- 
hundred-MB delete. A concurrent registerRepo/removeBranchIndex writer 
in that window was silently clobbered (the #2106 R9 lost-update class; 
registerRepo re-reads before writing for exactly this reason). 
 The top read is now a cheap membership gate only (the F2 no-op 
guarantee); the mutate re-reads its own fresh snapshot after the rm. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix: treat only provably-absent errno as gone in the new existence probes 
 
 Both probes added by this series inverted the codebase's provably- 
absent polarity (listRegisteredRepos validate prunes only on 
ENOENT/ENOTDIR): adoptFlatBranchLabel's dirGone check read ANY 
fs.access failure — including a transient EACCES/EIO on a surviving 
dir — as 'verifiably gone' and dropped the summary, recreating exactly 
the stranded-bloat bug F4 fixed; applyBranchScope's sub-index check 
read the same transient errors on a healthy pinned lbug as 'adopted/ 
deleted', producing a false 'not indexed' error. A resolved force:true 
rm now proves absence without a probe; on failure the probe treats 
only ENOENT/ENOTDIR as gone, and a non-missing lbug serves the handle 
so the pool open surfaces the real error. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(mcp): harden applyBranchScope stale-state coherence 
 
 Four residual gaps in the new arm structure, found by post-fix review: 
 
 The stale-label error listed the just-contradicted cached label as 
indexed ('not indexed: main. Indexed branches: main'). The message 
now derives the flat label from the authoritative meta and excludes 
the requested branch from the hint list. 
 A branch pinned AFTER the server cached its handle never triggered a 
refresh (resolve hits skip the miss-refresh), erroring until restart. 
Every miss now fires exactly one best-effort refreshRepos() before 
the error, so the next call resolves; a refresh-once guard keeps 
doubly-stale resolutions to a single registry re-scan. 
 A registry entry claiming the branch both as flat label and pinned 
summary (the rm-failed adopt-degraded state) could serve the stale- 
vintage pin under a label the flat slot owns; the summary arm now 
requires handle.branch !== branch and the degraded state errors 
honestly. 
 The flat-meta match path returned the cached handle's pre-restamp 
branch/commit/stats; the meta that decided routing now also supplies 
the metadata. 
 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(core): keep the real error visible in restamp warnings; correct the end-of-run retry claim 
 
 The fast-path catch replaced the actual error with 'storage is 
read-only ( #1549 )' for any EACCES/EPERM — mislabeling ownership 
problems and transient Windows locks and discarding the only 
diagnostic signal. The warning now carries the real message with the 
 #1549 hint appended. 
 The end-of-run best-effort comment claimed adopt 'retries 
unconditionally on the next plain analyze'; same-commit runs take the 
fast path whose guard compares the already-stamped meta label, so the 
retry actually lands on the next content-changing run. The comment now 
states the true retry semantics and why the interim state is safe 
(flat meta stamped first; applyBranchScope trusts it). 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 test: unique tmpdir for the branch-scope fixture; drop redundant dynamic impo

[... truncated for safety ...]