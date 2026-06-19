---
id: inbox_4782c145
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.12.4"
author: "ruvnet"
published_at: 2026-06-18T14:40:47+00:00
fetched_at: 2026-06-18T22:00:29.573284+00:00
content_hash: "da7748d936a5caf34b50d83bb455e7bc0162cb40d43a62a4ba7bd11b51d9f9f6"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.12.4 — CWE-78 security patch (agentic-flow ≥ 2.0.14)

🔒 Security release — CWE-78 fix 
 This release picks up agentic-flow@2.0.14 , which closes an OS command injection vulnerability in its MCP server tools. 
 What the upstream advisory found 
 agentic-flow ≤ 2.0.13's MCP server tools ( standalone-stdio , http-sse , http-streaming-updated , stdio-full , claude-flow-sdk , poc-stdio , plus the fastmcp/tools/{agent,swarm,hooks} sinks) interpolated attacker-influenceable MCP tool parameters directly into shell command strings passed to execSync() . A malicious value like: 
 x"; touch /tmp/INJECTED; id &gt; /tmp/rce.txt; echo "
 
 would break out of the surrounding double-quoted argument and execute arbitrary OS commands with the privileges of the user running the MCP server. In MCP deployments where untrusted content (web pages, files, third-party tool output) is processed by the AI agent, this was reachable without direct attacker access to the host. 
 What changed in this release 
 
 Root package.json : agentic-flow ^2.0.13 → ^2.0.14 
 ruflo/ wrapper overrides : adds "agentic-flow": "&gt;=2.0.14" defense-in-depth pin (per the #2112 lesson — wrapper does not inherit root overrides ) 
 All three packages bumped from 3.12.3 → 3.12.4 
 
 
 
 
 Package 
 latest 
 alpha 
 v3alpha 
 
 
 
 
 @claude-flow/cli 
 3.12.4 
 3.12.4 
 3.12.4 
 
 
 claude-flow 
 3.12.4 
 3.12.4 
 3.12.4 
 
 
 ruflo 
 3.12.4 
 3.12.4 
 3.12.4 
 
 
 
 How to upgrade 
 npx ruflo@latest # picks up 3.12.4 automatically 
npx claude-flow@latest # picks up 3.12.4 automatically 
npx @claude-flow/cli@latest # picks up 3.12.4 automatically 
 If you have a local install, refresh: 
 npm install ruflo@latest
 # or 
npm install agentic-flow@^2.0.14 
 Verifying the fix 
 Anywhere agentic-flow is installed in your tree: 
 $ grep -c " execSync( " node_modules/agentic-flow/dist/mcp/standalone-stdio.js
0
$ grep -c " execFileSync( " node_modules/agentic-flow/dist/mcp/standalone-stdio.js
14 
 The pre-fix code had 14 execSync(stringInterp) sinks; the fixed code has zero, replaced 1:1 with execFileSync('npx', argv, { shell: false }) where every argv element is passed straight to execve(2) and the shell is never invoked. 
 Cross-references 
 
 🔗 Upstream advisory + fix: ruvnet/agentic-flow#169 
 🔗 Upstream PR: ruvnet/agentic-flow#170 (merged at 0c2ec96 ) 
 🔗 Downstream tracking issue: #2414 
 🔗 Downstream PR: #2415 (merged at da901d0 ) 
 🔗 Published agentic-flow@2.0.14 : https://www.npmjs.com/package/agentic-flow/v/2.0.14 
 
 Credit 
 CWE-78 advisory originally reported via the hackchang_pipeline red-team report package ( npm_agentic-flow_report_package_20260618_163017.zip ). Thanks to hackchang for the report — the sink inventory + minimized PoC payload made it straightforward to write the static-scan regression test that fails CI if any new execSync() call is ever reintroduced into the MCP server tree. 
 
 🤖 Generated with RuFlo