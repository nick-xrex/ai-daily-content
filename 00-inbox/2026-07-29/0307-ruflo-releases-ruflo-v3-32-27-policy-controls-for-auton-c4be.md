---
id: inbox_0c589702
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.27"
author: "ruvnet"
published_at: 2026-07-29T02:58:10+00:00
fetched_at: 2026-07-29T03:07:31.485057+00:00
content_hash: "c4beac1810989d36296556199598189d876595c8b1abb532d4cb382c082b3662"
lang: en
caption_quality: None
raw: true
topics: []
---

# Ruflo v3.32.27 — Policy Controls for Autonomous Agents

Ruflo v3.32.27 — Policy Controls for Autonomous Agents 
 Agents can now move quickly without receiving unlimited authority. 
 Ruflo v3.32.27 adds an enforceable policy layer between an agent's intent and a 
consequential action. Teams can define what an agent may do, cap spend and 
concurrency, require authenticated approval for sensitive actions, constrain 
delegated workers, and audit every decision through a tamper-evident receipt 
ledger. 
 Existing installations remain compatible. Start in legacy , rehearse the 
policy in observe , and enable blocking with enforce after reviewing the 
recorded decisions. 
 What you can use it for 
 
 Put daily cost and token ceilings around model or tool calls. 
 Require approval for production deploys, destructive actions, or flywheel 
promotion. 
 Limit tools, MCP servers, namespaces, environments, network access, and 
delegated authority. 
 Run bounded concurrent Codex development with a separate worktree and reduced 
capability envelope for every writing worker. 
 Allow MetaHarness to benchmark candidates concurrently without allowing the 
optimizer to promote itself. 
 Audit policy decisions and detect modified or reordered receipts. 
 Filter AgentDB retrieval by typed provenance without breaking legacy records. 
 
 Install or upgrade 
 The verified GitHub release artifacts are available now. Their embedded helper 
manifest is signed. Install the policy runtime, CLI, and Ruflo wrapper together: 
 npm install --global \
 https://github.com/ruvnet/ruflo/releases/download/v3.32.27/claude-flow-security-3.0.0-alpha.13.tgz \
 https://github.com/ruvnet/ruflo/releases/download/v3.32.27/claude-flow-cli-3.32.27.tgz \
 https://github.com/ruvnet/ruflo/releases/download/v3.32.27/ruflo-3.32.27.tgz
ruflo --version
ruflo policy status 
 The normal npm install --global ruflo@3.32.27 path will become available 
after npm trusted-publisher authorization is completed. No source rebuild is 
required. 
 Safe rollout 
 Inspect or migrate the local policy state: 
 ruflo policy init
ruflo policy status
ruflo policy verify 
 Observe policy decisions without blocking normal actions: 
 ruflo policy init --mode observe 
 Add a daily model budget: 
 ruflo policy budget set ' { 
 "id": "daily-model-budget", 
 "action": "model.call", 
 "maxCostUsd": 10, 
 "maxTokens": 500000, 
 "periodMs": 86400000 
 } ' 
 Evaluate an action: 
 ruflo policy evaluate ' { 
 "identity": { 
 "id": "codex-worker-1", 
 "type": "agent", 
 "roles": ["developer"] 
 }, 
 "action": { 
 "type": "model.call", 
 "resource": "openrouter", 
 "environment": "development", 
 "costUsd": 0.12, 
 "tokens": 8000, 
 "concurrency": 2, 
 "network": true 
 } 
 } ' 
 After reviewing receipts and defining explicit rules: 
 ruflo policy init --mode enforce 
 The end-user quick start walks through rules, budgets, delegated 
capability envelopes, concurrent Codex workflows, MetaHarness promotion, and 
troubleshooting. 
 Policy-governed MetaHarness 
 Candidate evaluation is now bounded by both the flywheel SafetyEnvelope and the 
agentic policy engine: 
 ruflo metaharness flywheel run \
 --project-root . \
 --proposer local \
 --sample 40 \
 --max-concurrency 2 \
 --timeout-ms 120000 \
 --private-key /path/to/flywheel-private.pem \
 --public-key /path/to/flywheel-public.pem 
 Promotion remains a separate, explicit, policy-authorized transaction: 
 ruflo metaharness flywheel promote &lt; receipt-id &gt; \
 --project-root . \
 --public-key /path/to/flywheel-public.pem \
 --approval-id &lt; authenticated-approval-id &gt; \
 --confirm 
 Darwin proposes; Ruflo disposes. The optimizer cannot authorize its own 
promotion. 
 Safe defaults 
 
 Existing projects migrate in backward-compatible legacy mode. 
 observe records denials but does not block ordinary actions. 
 Capability-envelope violations are always blocked; delegated authority cannot 
expand. 
 observe and enforce are default-deny when no rule matches. 
 Budgeted requests must report cost or token usage; missing metering does not 
bypass a ceiling. 
 Local policy administration requires an interactive terminal. 
 Approval issuance requires an authenticated human identity adapter. A local 
TTY is not treated as identity proof. 
 MetaHarness, Darwin, and Flywheel remain optional dependencies. 
 Missing optional packages do not break the local policy engine or existing 
AgentDB workflows. 
 
 AgentDB provenance 
 This release also includes ADR-323 typed provenance across AgentDB retrieval: 
 user_claim , agent_output , system_observation , tool_result , and 
 unknown . Legacy records remain readable and are conservatively classified as 
 unknown ; unsigned caller claims are never silently promoted to trusted 
evidence. 
 Compatibility 
 This is a backward-compatible patch release. Existing Ruflo and AgentDB 
installations continue to work without opting into enforcement. The release 
preserves the v3.32.26 flywheel transaction and receipt formats while adding 
policy authorization around privileged operations. 
 Release artifacts: 
 claude-flow-security-3.0.0-alpha.13.tgz
claude-flow-cli-3.32.27.tgz
claude-flow-3.32.27.tgz
ruflo-3.32.27.tgz
SHA256SUMS
 
 Validation 
 The implementation passed: 
 
 the complete ADR-324 policy-engine and security test suites; 
 atomic budget, approval, delegation, evidence, and receipt-ledger tests; 
 concurrent Codex worktree coordination tests; 
 governed in-process MetaHarness evaluation and promotion tests; 
 the 122-case MetaHarness contract suite; 
 operation without AgentBBS or MetaHarness installed; 
 MCP discoverability, install-safety, type-check, package, CodeQL, and 
cross-platform CI gates; 
 policy-engine performance benchmarks. 
 
 Learn more 
 
 End-user quick start 
 ADR-324 architecture 
 ADR-323 typed provenance 
 ADR-322 governed flywheel 
 Policy-engine PR #2822 
 Typed-provenance PR #2820 
 Full changelog