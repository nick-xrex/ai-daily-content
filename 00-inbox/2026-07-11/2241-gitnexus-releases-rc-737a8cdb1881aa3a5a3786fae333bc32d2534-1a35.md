---
id: inbox_1855046e
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F737a8cdb1881aa3a5a3786fae333bc32d25343c3"
author: "koriyoshi2041"
published_at: 2026-07-11T10:43:47+00:00
fetched_at: 2026-07-11T22:41:12.781952+00:00
content_hash: "1a35091e3c3d2277e03a5c7531da01d4a5f00d443c7c67e36532a8b020590fe7"
lang: en
caption_quality: None
raw: true
topics: []
---

# rc/737a8cdb1881aa3a5a3786fae333bc32d25343c3: fix(web): use repo path identity in switcher (#2420)

fix(web): use repo path identity in switcher 
 
 
 keep repo URL project names stable 
 
 
 fix server repo path resolution 
 
 
 fix repo path miss resolution 
 
 
 fix(server): guard clone-dir deletion with path ownership check 
 
 
 Deleting a registry entry derived its clone dir from the entry NAME with 
no ownership check, so deleting a local repo that shares a display name 
with a server-cloned sibling wiped the sibling's checkout. Gate the 
removal on cloneDirBelongsToEntry (canonicalized path equality), the 
same entry.path-driven rule the handler's step 2b already mandates. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(server): fail closed on relative repo params and rate-limit GET /api/repo 
 
 Relative separator-containing ?repo= values (org/name, ./repo) were 
canonicalized against the server CWD — an attacker-influenced 
realpathSync probe on an un-rate-limited GET — before failing anyway. 
Reject them immediately without touching the filesystem, drop the 
redundant path.sep clause, document the resolver's two-tier contract, 
and wire createRouteLimiter on GET /api/repo like its DELETE sibling. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 test(server): lock repo resolver branches and register for Windows CI 
 
 Lock in the resolver's remaining branches: first-wins for ambiguous 
bare names, Windows-shaped input as a fail-closed path claim, the 
repos[0] default, and the case-insensitive name fallback. Register the 
suite in cross-platform-tests.ts so windows-latest actually runs the 
path-shape logic it exists to protect. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 refactor(web): single repoIdentity helper with repoPath normalized end-to-end 
 
 The identity fallback chain was copy-pasted in Header and RepoLanding 
while backend-client already owns BackendRepo and the repoPath 
normalization. Export one repoIdentity helper, normalize fetchRepos 
like fetchRepoInfo, and emit repoPath from GET /api/repos so the 
scheme no longer silently relies on /api/repo.repoPath equalling 
/api/repos.path. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(web): persist and restore repo path identity in the URL 
 
 The URL persisted only ?project=, so refreshing after 
switching to a duplicate-name repo silently restored the first 
same-named sibling. Persist ?repo= alongside the 
readable ?project= at both write sites, prefer it on restore (legacy 
project-only URLs still work), keep failed path restores fail-visible 
(no name fallback), and strip stale identity params when deleting the 
active or last repo. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(web): analyze completion connects by path identity 
 
 RepoAnalyzer's completion callback passed the display name, so 
analyzing a repo whose basename collides with an existing one 
reconnected the first same-named sibling. The SSE terminal payload now 
carries the job's repoPath (both emit sites), the analyzer passes that 
identity to onComplete while the done screen keeps showing the display 
name, and old servers without repoPath degrade to today's behavior. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(web): scope code-reference file reads to the active repo identity 
 
 The code viewer passed the display name as the repo scope, so with 
duplicate-name repos it rendered the wrong repo's file contents under 
the right filename. Pass the active path identity (currentRepo) with 
the display name as fallback, and collapse the two dead repo fields 
that were already shadowed by the readFile spread. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(web): show display names instead of absolute paths in labels 
 
 The path-identity switch leaked raw filesystem paths into three 
user-facing surfaces: the re-analyze progress label, the repo-switch 
overlay, and the agent prompt's project name via loadGraphAnyway. 
Resolve display names at render time (registry lookup, then basename 
fallback) while state keeps holding the identity; loadGraphAnyway 
passes the name explicitly because initializeAgent's empty-deps 
closure would otherwise fall through to the literal 'project'. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(web): stop initializeAgent from clobbering repo identity with display names 
 
 initializeAgent fell back to writing overrideProjectName (a display 
name) into the repo identity, so any future name-only caller — the 
pre-PR idiom — would silently kill the Active badge and re-admit the 
duplicate-name ambiguity through the agent path. Only opts.repo may 
write the identity now. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 chore(web): drop dead initializers flagged by CodeQL 
 
 pNameStr's and repoIdentity's initial values were never read: both are 
assigned on the success path before any use and the catch returns 
early. Bare declarations resolve CodeQL alerts 825/826. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 style(web): fix tailwind class order per root prettier plugin 
 
 The worktree pre-commit hook resolved prettier-plugin-tailwindcss 
through symlinked node_modules and sorted scrollbar-thin differently 
than CI's clean-room install. Re-formatted with the root lockfile 
environment; no behavior change. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 test(web): e2e coverage for every #2419 duplicate-name ambiguity 
 
 Provision two live repos with the same basename under different parents 
via POST /api/analyze, then drive a real browser through each item of 
the issue's "Actual behavior" list: 
 
 duplicate rows render and the ACTIVE one is identifiable before and 
after switching (active-state must not compare repo.name) 
 switching between duplicates swaps the loaded graph, verified by 
per-repo marker files (onSwitchRepo must not receive repo.name) 
 re-analyze targets the clicked duplicate's exact path (POST body), 
tracks progress on that row only, and the completion reconnect 
requests that same path — never the same-named sibling 
 delete requests target exactly the chosen duplicate's path; the 
sibling stays registered and loaded 
 backend ?repo= resolution is path-first: landing selection loads the 
exact repo, ?repo= survives F5, and a stale path fails closed to the 
repo picker instead of retargeting the sibling 
 
 Adds four data-testids to Header (switcher trigger/row/reanalyze/ 
delete, rows expose data-active) so the spec has stable selectors, and 
broadens the post-analyze reconnect retry in App to any BackendError: 
the server may still be reinitializing when the SSE complete event 
fires, and that surfaces as transient 5xx/binder errors, not only 404. 
 The re-analyze and delete tests deliberately assert identity at the 
request level and tolerate two pre-existing server races that are 
unrelated to the #2419 identity contract (freshly-analyzed DB briefly 
unreadable after SSE complete; registry validate-prune clobbering a 
concurrent unregister) — see the in-test comments. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 
 chore(autofix): apply prettier + eslint fixes via /autofix command 
 
 
 test(web): isolate repo-path-identity e2e onto a spec-owned backend 
 
 
 The spec is the only e2e file doing write operations (analyze, 
re-analyze, delete). Running its force re-analysis against the shared 
CI backend while parallel workers held connections took the whole 
server down (run 29145679019: the jobId poll died with ECONNRESET and 
every later test in every file failed to connect). 
 Spawn a dedicated gitnexus serve on port 4799 with an isolated 
GITNEXUS_HOME in beforeAll instead: writes can no longer perturb the 
other suites, a crash is contained to this spec (its output is captured 
and printed, which CI otherwise loses), and the registry is hermetic by 
construction — the previous leftover-purge and shared-registry cleanup 
are gone. Every page is pointed at the spec backend through 
useBackend's supported localStorage override, which covers both the 
probe-driven landing flow and the ?server= auto-connect. Verified 
self-sufficient (6/6 with no shared server running) and non-interfering 
(full suite 39/39 with the shared server up). 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 
 stabilize repo path identity e2e 
 
 
 fix(server): don't report analyze complete before the index is settled 
 
 
 The analyze worker reports complete over IPC before its on-disk 
finalization (LadybugDB checkpoint, native handle release, metadata 
write) is visible at the storage path — observed up to ~6.5s behind the 
IPC message. The launcher's "reinitialize backend BEFORE marking 
complete" ordering was meant to make the repo queryable by the time the 
client sees the SSE complete event, but it never verified that: clients 
reconnecting on that event read a database still being written. Locally 
that surfaces as "Binder exception: Table CodeRelation does not exist" 
or a silently empty graph, and the open can quarantine the in-flight 
WAL; on slow CI runners the native layer racing the rewrite has killed 
the whole server (signal exit, no output — run 29146867959). 
 Gate the complete transition on the index actually settling: LadybugDB 
file and metadata both rewritten by THIS job (mtime &gt;= job start — bare 
existence is not enough, a re-analysis leaves the previous index in 
place while it works) and no transient WAL/shadow/checkpoint sidecars 
remaining. Bounded (60s) and proceed-on-timeout, so a job whose 
analysis legitimately rewrites nothing cannot wedge. Also evict the 
server's cached DB handle before reinitializing — same invalidation 
DELETE /api/repo performs — so post-completion reads cannot be served 
from a pre-rewrite handle. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 test(web): assert re-analyze completion identity at the request level 
 
 The strict form (Ready + marker on the re-analyzed duplicate) still 
trips a deeper pre-existing storage race that makes a freshly 
re-analyzed database transiently unreadable to the reconnect even with 
the settle gate in place — unrelated to the #2419 identity contract 
this test covers. Keep the identity assertions (the reconnect targets 
the exact duplicate's path and never the same-named sibling) and leave 
a pointer to tighten once the storage race is fixed. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(server): resolve the settle-gate path from the registry, not the request 
 
 CodeQL flagged the settle gate's stat/exists probes as js/path-injection: 
the probed path derived from the user-provided analyze path . Resolve 
it from the repo's registry entry instead — the user value is now only a 
comparison key, and the probes run against the server-owned storagePath 
record, which is also the authoritative path readers resolve through. 
Re-resolved each poll round because the worker registers the repo as 
part of the same finalization the gate is waiting out. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 Co-authored-by: Gergő Magyar gergomagyar@icloud.com 
Co-authored-by: Claude Fable 5 noreply@anthropic.com 
Co-authored-by: github-actions[bot] &lt;41898282+github-actions[bot]@users.noreply.github.com&gt;