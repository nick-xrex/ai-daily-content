---
id: inbox_f78ba65e
source: codex-releases
source_type: rss
url: "https://github.com/openai/codex/releases/tag/rust-v0.123.0"
author: "github-actions[bot]"
published_at: 2026-04-23T01:26:41+00:00
fetched_at: 2026-04-24T02:46:14.152311+00:00
content_hash: "e1e6599f92ba3ced00a7fc99528bb05d006356a46f80ee333ed717823ee234d8"
lang: en
caption_quality: None
raw: true
topics: []
---

# 0.123.0

<h2>New Features</h2>
<ul>
<li>Added a built-in <code>amazon-bedrock</code> model provider with configurable AWS profile support (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18744">#18744</a>).</li>
<li>Added <code>/mcp verbose</code> for full MCP server diagnostics, resources, and resource templates while keeping plain <code>/mcp</code> fast (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18610">#18610</a>).</li>
<li>Made plugin MCP loading accept both <code>mcpServers</code> and top-level server maps in <code>.mcp.json</code> (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18780">#18780</a>).</li>
<li>Improved realtime handoffs so background agents receive transcript deltas and can explicitly stay silent when appropriate (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18597">#18597</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18761">#18761</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18635">#18635</a>).</li>
<li>Added host-specific <code>remote_sandbox_config</code> requirements for remote environments (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18763">#18763</a>).</li>
<li>Refreshed bundled model metadata, including the current <code>gpt-5.4</code> default (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18586">#18586</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18388">#18388</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18719">#18719</a>).</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li>Fixed <code>/copy</code> after rollback so it copies the latest visible assistant response, not a pre-rollback response (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18739">#18739</a>).</li>
<li>Queued normal follow-up text submitted while a manual shell command is running, preventing stuck <code>Working</code> states (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18820">#18820</a>).</li>
<li>Fixed Unicode/dead-key input in VS Code WSL terminals by disabling the enhanced keyboard mode there (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18741">#18741</a>).</li>
<li>Prevented stale proxy environment variables from being restored from shell snapshots (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/17271">#17271</a>).</li>
<li>Made <code>codex exec</code> inherit root-level shared flags such as sandbox and model options (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18630">#18630</a>).</li>
<li>Removed leaked review prompts from TUI transcripts (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18659">#18659</a>).</li>
</ul>
<h2>Documentation</h2>
<ul>
<li>Added and tightened the Code Review skill instructions used by Codex-driven reviews (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18746">#18746</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18818">#18818</a>).</li>
<li>Documented intentional await-across-lock cases and enabled Clippy linting for them (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18423">#18423</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18698">#18698</a>).</li>
<li>Updated app-server protocol docs for threadless MCP resource reads and namespaced dynamic tools (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18292">#18292</a>, <a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18413">#18413</a>).</li>
</ul>
<h2>Chores</h2>
<ul>
<li>Fixed high-severity dependency alerts by pinning patched JS and Rust dependencies (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18167">#18167</a>).</li>
<li>Reduced Rust dev build debug-info overhead while preserving useful backtraces (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18844">#18844</a>).</li>
<li>Refreshed generated Python app-server SDK types from the current schema (<a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18862">#18862</a>).</li>
</ul>
<h2>Changelog</h2>
<p>Full Changelog: <a class="commit-link" href="https://github.com/openai/codex/compare/rust-v0.122.0...rust-v0.123.0"><tt>rust-v0.122.0...rust-v0.123.0</tt></a></p>
<ul>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18662">#18662</a> feat: add metric to track the number of turns with memory usage <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18659">#18659</a> chore: drop review prompt from TUI UX <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18661">#18661</a> feat: log client use min log level <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18094">#18094</a> [codex] Use background agent task auth for backend calls <a class="user-mention notranslate" href="https://github.com/adrian-openai">@adrian-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18441">#18441</a> Avoid false shell snapshot cleanup warnings <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18260">#18260</a> [codex] Use background task auth for additional backend calls <a class="user-mention notranslate" href="https://github.com/adrian-openai">@adrian-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18657">#18657</a> fix: auth.json leak in tests <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18610">#18610</a> Add verbose diagnostics for /mcp <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18633">#18633</a> Use app server thread names in TUI picker <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18591">#18591</a> Surface parent thread status in side conversations <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18361">#18361</a> codex: move thread/name/set and thread/memoryModeSet into ThreadStore <a class="user-mention notranslate" href="https://github.com/wiltzius-openai">@wiltzius-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18274">#18274</a> protocol: canonicalize file system permissions <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18403">#18403</a> refactor: use semaphores for async serialization gates <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18586">#18586</a> Update models.json <a class="user-mention notranslate" href="https://github.com/aibrahim-oai">@aibrahim-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18289">#18289</a> Wire the PatchUpdated events through app_server <a class="user-mention notranslate" href="https://github.com/akshaynathan">@akshaynathan</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18631">#18631</a> Remove simple TUI legacy_core reexports <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18697">#18697</a> [codex] Fix agent identity auth test fixture <a class="user-mention notranslate" href="https://github.com/adrian-openai">@adrian-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18388">#18388</a> Update models.json @github-actions</li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18167">#18167</a> [codex] Fix high severity dependency alerts <a class="user-mention notranslate" href="https://github.com/caseysilver-oai">@caseysilver-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/17692">#17692</a> [codex-analytics] guardian review analytics schema polishing <a class="user-mention notranslate" href="https://github.com/rhan-oai">@rhan-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18722">#18722</a> chore(guardian) disable mcps and plugins <a class="user-mention notranslate" href="https://github.com/dylan-hurd-oai">@dylan-hurd-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18597">#18597</a> Update realtime handoff transcript handling <a class="user-mention notranslate" href="https://github.com/guinness-oai">@guinness-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18627">#18627</a> Surface TUI skills refresh failures <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18719">#18719</a> Fix stale model test fixtures <a class="user-mention notranslate" href="https://github.com/aibrahim-oai">@aibrahim-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18714">#18714</a> Add experimental remote thread store config <a class="user-mention notranslate" href="https://github.com/wiltzius-openai">@wiltzius-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18739">#18739</a> fix(tui): keep /copy aligned with rollback <a class="user-mention notranslate" href="https://github.com/fcoury-oai">@fcoury-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18701">#18701</a> [codex] prefer inherited spawn agent model <a class="user-mention notranslate" href="https://github.com/tibo-openai">@tibo-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18632">#18632</a> Use app server metadata for fork parent titles <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18112">#18112</a> feat: cascade thread archive <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18716">#18716</a> Read conversation summaries through thread store <a class="user-mention notranslate" href="https://github.com/wiltzius-openai">@wiltzius-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18635">#18635</a> Add realtime silence tool <a class="user-mention notranslate" href="https://github.com/guinness-oai">@guinness-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18254">#18254</a> uds: add async Unix socket crate <a class="user-mention notranslate" href="https://github.com/euroelessar">@euroelessar</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18746">#18746</a> Add Code Review skill <a class="user-mention notranslate" href="https://github.com/pakrym-oai">@pakrym-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18208">#18208</a> Add session config loader interface <a class="user-mention notranslate" href="https://github.com/rasmusrygaard">@rasmusrygaard</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18753">#18753</a> Refactor TUI app module into submodules <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18630">#18630</a> Fix exec inheritance of root shared flags <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18027">#18027</a> [6/6] Fail exec client operations after disconnect <a class="user-mention notranslate" href="https://github.com/aibrahim-oai">@aibrahim-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/17271">#17271</a> fix: fix stale proxy env restoration after shell snapshots <a class="user-mention notranslate" href="https://github.com/viyatb-oai">@viyatb-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18602">#18602</a> Warn when trusting Git subdirectories <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18761">#18761</a> [codex] Send realtime transcript deltas on handoff <a class="user-mention notranslate" href="https://github.com/guinness-oai">@guinness-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18435">#18435</a> /statusline &amp; /title - Shared preview values <a class="user-mention notranslate" href="https://github.com/canvrno-oai">@canvrno-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18744">#18744</a> feat: add a built-in Amazon Bedrock model provider <a class="user-mention notranslate" href="https://github.com/celia-oai">@celia-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18581">#18581</a> [1/4] Add executor HTTP request protocol <a class="user-mention notranslate" href="https://github.com/aibrahim-oai">@aibrahim-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18418">#18418</a> refactor: narrow async lock scopes <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18780">#18780</a> feat: Support more plugin MCP file shapes. <a class="user-mention notranslate" href="https://github.com/xl-openai">@xl-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18713">#18713</a> protocol: preserve glob scan depth in permission profiles <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18795">#18795</a> fix(guardian) Dont hard error on feature disable <a class="user-mention notranslate" href="https://github.com/dylan-hurd-oai">@dylan-hurd-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18292">#18292</a> Make MCP resource read threadless <a class="user-mention notranslate" href="https://github.com/mzeng-openai">@mzeng-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18786">#18786</a> Fallback display names for TUI skill mentions <a class="user-mention notranslate" href="https://github.com/canvrno-oai">@canvrno-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18807">#18807</a> chore(app-server) linguist-generated <a class="user-mention notranslate" href="https://github.com/dylan-hurd-oai">@dylan-hurd-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18393">#18393</a> feat(auto-review) Handle request_permissions calls <a class="user-mention notranslate" href="https://github.com/dylan-hurd-oai">@dylan-hurd-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18763">#18763</a> Add remote_sandbox_config to our config requirements <a class="user-mention notranslate" href="https://github.com/abhinav-oai">@abhinav-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18794">#18794</a> Organize context fragments  <a class="user-mention notranslate" href="https://github.com/pakrym-oai">@pakrym-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18423">#18423</a> chore: document intentional await-holding cases <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18698">#18698</a> chore: enable await-holding clippy lints <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18413">#18413</a> [tool search] support namespaced deferred dynamic tools <a class="user-mention notranslate" href="https://github.com/pash-openai">@pash-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18818">#18818</a> [codex] Tighten code review skill wording <a class="user-mention notranslate" href="https://github.com/pakrym-oai">@pakrym-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18271">#18271</a> show bash mode in the TUI <a class="user-mention notranslate" href="https://github.com/abhinav-oai">@abhinav-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18741">#18741</a> fix(tui): disable enhanced keys for VS Code WSL <a class="user-mention notranslate" href="https://github.com/fcoury-oai">@fcoury-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18850">#18850</a> Move external agent config out of core <a class="user-mention notranslate" href="https://github.com/pakrym-oai">@pakrym-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18844">#18844</a> build: reduce Rust dev debuginfo <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18848">#18848</a> feat: baseline lib <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18846">#18846</a> core: make test-log a dev dependency <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18428">#18428</a> app-server: define device key v2 protocol <a class="user-mention notranslate" href="https://github.com/euroelessar">@euroelessar</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18093">#18093</a> Propagate thread id in MCP tool metadata <a class="user-mention notranslate" href="https://github.com/rennie-openai">@rennie-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/17836">#17836</a> [codex] Add tmux-aware OSC 9 notifications <a class="user-mention notranslate" href="https://github.com/caseychow-oai">@caseychow-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18820">#18820</a> Queue follow-up input during user shell commands <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18858">#18858</a> Stabilize debug clear memories integration test <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18799">#18799</a> Move TUI app tests to modules they cover <a class="user-mention notranslate" href="https://github.com/etraut-openai">@etraut-openai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18442">#18442</a> Refactor app-server config loading into ConfigManager <a class="user-mention notranslate" href="https://github.com/pakrym-oai">@pakrym-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18813">#18813</a> Split DeveloperInstructions into individual fragments. <a class="user-mention notranslate" href="https://github.com/pakrym-oai">@pakrym-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18275">#18275</a> sandboxing: intersect permission profiles semantically <a class="user-mention notranslate" href="https://github.com/bolinfest">@bolinfest</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18862">#18862</a> Refresh generated Python app-server SDK types <a class="user-mention notranslate" href="https://github.com/sdcoffey">@sdcoffey</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/15578">#15578</a> Add Windows sandbox unified exec runtime support <a class="user-mention notranslate" href="https://github.com/iceweasel-oai">@iceweasel-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18429">#18429</a> app-server: add codex-device-key crate <a class="user-mention notranslate" href="https://github.com/euroelessar">@euroelessar</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18872">#18872</a> app-server: fix Bazel clippy in tracing tests <a class="user-mention notranslate" href="https://github.com/euroelessar">@euroelessar</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18885">#18885</a> skip busted tests while I fix them <a class="user-mention notranslate" href="https://github.com/iceweasel-oai">@iceweasel-oai</a></li>
<li><a class="issue-link js-issue-link" href="https://github.com/openai/codex/pull/18873">#18873</a> chore: default multi-agent v2 fork to all <a class="user-mention notranslate" href="https://github.com/jif-oai">@jif-oai</a></li>
</ul>