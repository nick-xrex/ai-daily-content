---
id: inbox_1c543fbb
source: codex-releases
source_type: rss
url: "https://github.com/openai/codex/releases/tag/rust-v0.125.0"
author: "github-actions[bot]"
published_at: 2026-04-24T18:01:13+00:00
fetched_at: 2026-04-25T15:05:01.324335+00:00
content_hash: "2b0344df038065e43bfd114b16e5648b1f65b0da8a2931def244e9443c6528ee"
lang: en
caption_quality: None
raw: true
topics: []
---

# 0.125.0

<h2>New Features</h2>
<ul>
<li>App-server integrations now support Unix socket transport, pagination-friendly resume/fork, sticky environments, and remote thread config/store plumbing. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18255">#18255</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18892">#18892</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18897">#18897</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18908">#18908</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19008">#19008</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19014">#19014</a>)</li>
<li>App-server plugin management can install remote plugins and upgrade configured marketplaces. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18917">#18917</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19074">#19074</a>)</li>
<li>Permission profiles now round-trip across TUI sessions, user turns, MCP sandbox state, shell escalation, and app-server APIs. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18284">#18284</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18285">#18285</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18286">#18286</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18287">#18287</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19231">#19231</a>)</li>
<li>Model providers now own model discovery, with AWS/Bedrock account state exposed to app clients. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18950">#18950</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19048">#19048</a>)</li>
<li><code>codex exec --json</code> now reports reasoning-token usage for programmatic consumers. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19308">#19308</a>)</li>
<li>Rollout tracing now records tool, code-mode, session, and multi-agent relationships, with a debug reducer command for inspection. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18878">#18878</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18879">#18879</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18880">#18880</a>)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li>Interrupting <code>/review</code> and exiting the TUI no longer leaves the interface wedged on delegate startup or unsubscribe. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18921">#18921</a>)</li>
<li>Exec-server no longer drops buffered output after process exit and now waits correctly for stream closure. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18946">#18946</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19130">#19130</a>)</li>
<li>App-server now respects explicitly untrusted project config instead of auto-persisting trust. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18626">#18626</a>)</li>
<li>WebSocket app-server clients are less likely to disconnect during bursts of turn and tool-output notifications. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19246">#19246</a>)</li>
<li>Windows sandbox startup handles multiple CLI versions and installed app directories better, and background <code>Start-Process</code> calls avoid visible PowerShell windows. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19044">#19044</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19180">#19180</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19214">#19214</a>)</li>
<li>Config/schema handling now rejects conflicting MultiAgentV2 thread limits, resolves relative agent-role config paths, hides unsupported MCP bearer-token fields, and rejects invalid <code>js_repl</code> image MIME types. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19129">#19129</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19261">#19261</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19294">#19294</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19292">#19292</a>)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li>App-server docs and generated schemas were refreshed for the new transport, thread, marketplace, sticky environment, and permission-profile APIs. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18255">#18255</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18897">#18897</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19014">#19014</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19074">#19074</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19231">#19231</a>)</li>
<li>Rollout-trace documentation now covers the debug trace reduction workflow. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18880">#18880</a>)</li>
</ul>
<h2>Chores</h2>
<ul>
<li>Refreshed <code>models.json</code> and related core, app-server, SDK, and TUI fixtures for the latest model catalog and reasoning defaults. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19323">#19323</a>)</li>
<li>Windows Bazel CI now uses a stable PATH and shared query startup path for better cache reuse. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19161">#19161</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19232">#19232</a>)</li>
<li>Plugin marketplace add/remove/startup-sync internals moved out of <code>codex-core</code>, and curated plugin cache versions now use short SHAs. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19099">#19099</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19095">#19095</a>)</li>
<li>Reverted a macOS signing entitlement change after it caused alpha startup failures. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19167">#19167</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19350">#19350</a>)</li>
<li>Stabilized flaky approval-popup and plugin MCP tool-discovery tests. (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19178">#19178</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19191">#19191</a>)</li>
</ul>
<h2>Changelog</h2>
<p>Full Changelog: <a class="commit-link" href="https://github.com/openai/codex/compare/rust-v0.124.0...rust-v0.125.0"><tt>rust-v0.124.0...rust-v0.125.0</tt></a></p>
<ul>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19129">#19129</a> Reject agents.max_threads with multi_agent_v2 <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19130">#19130</a> exec-server: wait for close after observed exit <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19149">#19149</a> Update safety check wording <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18284">#18284</a> tui: sync session permission profiles <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18710">#18710</a> [codex] Fix plugin marketplace help usage <a class="user-mention notranslate" href="https://github.com/xli-oai">@xli-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19127">#19127</a> feat: drop spawned-agent context instructions <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18892">#18892</a> Add remote thread config loader protos <a class="user-mention notranslate" href="https://github.com/rasmusrygaard">@rasmusrygaard</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19014">#19014</a> Add excludeTurns parameter to thread/resume and thread/fork <a class="user-mention notranslate" href="https://github.com/ddr-oai">@ddr-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18882">#18882</a> [codex] Route live thread writes through ThreadStore <a class="user-mention notranslate" href="https://github.com/wiltzius-openai">@wiltzius-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19008">#19008</a> [codex] Implement remote thread store methods <a class="user-mention notranslate" href="https://github.com/wiltzius-openai">@wiltzius-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18626">#18626</a> Respect explicit untrusted project config <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18255">#18255</a> app-server: add Unix socket transport <a class="user-mention notranslate" href="https://github.com/euroelessar">@euroelessar</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19167">#19167</a> ci: add macOS keychain entitlements <a class="user-mention notranslate" href="https://github.com/euroelessar">@euroelessar</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19099">#19099</a> Move marketplace add/remove and startup sync out of core. <a class="user-mention notranslate" href="https://github.com/xl-openai">@xl-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19168">#19168</a> Use Auto-review wording for fallback rationale <a class="user-mention notranslate" href="https://github.com/maja-openai">@maja-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18908">#18908</a> Add remote thread config endpoint <a class="user-mention notranslate" href="https://github.com/rasmusrygaard">@rasmusrygaard</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18285">#18285</a> tui: carry permission profiles on user turns <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18286">#18286</a> mcp: include permission profiles in sandbox state <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18878">#18878</a> [rollout_trace] Trace tool and code-mode boundaries <a class="user-mention notranslate" href="https://github.com/cassirer-openai">@cassirer-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18287">#18287</a> shell-escalation: carry resolved permission profiles <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18946">#18946</a> fix(exec-server): retain output until streams close <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19074">#19074</a> Add app-server marketplace upgrade RPC <a class="user-mention notranslate" href="https://github.com/xli-oai">@xli-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19180">#19180</a> use a version-specific suffix for command runner binary in .sandbox-bin <a class="user-mention notranslate" href="https://github.com/iceweasel-oai">@iceweasel-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19178">#19178</a> Stabilize approvals popup disabled-row test <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18921">#18921</a> Fix /review interrupt and TUI exit wedges <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19191">#19191</a> Stabilize plugin MCP tools test <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19194">#19194</a> Mark hooks schema fixtures as generated <a class="user-mention notranslate" href="https://github.com/abhinav-oai">@abhinav-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18288">#18288</a> tests: isolate approval fixtures from host rules <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19044">#19044</a> guide Windows to use -WindowStyle Hidden for Start-Process calls <a class="user-mention notranslate" href="https://github.com/iceweasel-oai">@iceweasel-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19214">#19214</a> do not attempt ACLs on installed codex dir <a class="user-mention notranslate" href="https://github.com/iceweasel-oai">@iceweasel-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19161">#19161</a> ci: derive cache-stable Windows Bazel PATH <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18811">#18811</a> refactor: route Codex auth through AuthProvider <a class="user-mention notranslate" href="https://github.com/efrazer-oai">@efrazer-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19246">#19246</a> Increase app-server WebSocket outbound buffer <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19048">#19048</a> feat: expose AWS account state from account/read <a class="user-mention notranslate" href="https://github.com/celia-oai">@celia-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18880">#18880</a> [rollout_trace] Add debug trace reduction command <a class="user-mention notranslate" href="https://github.com/cassirer-openai">@cassirer-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18897">#18897</a> Add sticky environment API and thread state <a class="user-mention notranslate" href="https://github.com/starr-openai">@starr-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18879">#18879</a> [rollout_trace] Trace sessions and multi-agent edges <a class="user-mention notranslate" href="https://github.com/cassirer-openai">@cassirer-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19095">#19095</a> feat: Use short SHA versions for curated plugin cache entries <a class="user-mention notranslate" href="https://github.com/xl-openai">@xl-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18950">#18950</a> feat: let model providers own model discovery <a class="user-mention notranslate" href="https://github.com/celia-oai">@celia-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19206">#19206</a> app-server: persist device key bindings in sqlite <a class="user-mention notranslate" href="https://github.com/euroelessar">@euroelessar</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18917">#18917</a> [codex] Support remote plugin install writes <a class="user-mention notranslate" href="https://github.com/xli-oai">@xli-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19231">#19231</a> permissions: make profiles represent enforcement <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19261">#19261</a> Resolve relative agent role config paths from layers <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19232">#19232</a> ci: reuse Bazel CI startup for target-discovery queries <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19292">#19292</a> Reject unsupported js_repl image MIME types <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19247">#19247</a> chore: apply truncation policy to unified_exec <a class="user-mention notranslate" href="https://github.com/sayan-oai">@sayan-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19294">#19294</a> Hide unsupported MCP bearer_token from config schema <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19308">#19308</a> Surface reasoning tokens in exec JSON usage <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19323">#19323</a> Update models.json and related fixtures <a class="user-mention notranslate" href="https://github.com/sayan-oai">@sayan-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/19350">#19350</a> fix alpha build <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
</ul>