---
id: inbox_8293c595
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.16.0"
author: "ruvnet"
published_at: 2026-06-29T23:14:32+00:00
fetched_at: 2026-07-01T23:31:23.999793+00:00
content_hash: "fa7055c17c9902fb0ce77a089e0905e68af4c4a92a6fde40d707ee28816c9cce"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.16.0 — ADR-164 AgentBBS Business Autopilot (4 MCP tools, 7 pods, atomic budget tracker)

What's new in 3.16.0 — ADR-164 AgentBBS Business Autopilot 
 This MINOR release lands Phases 1-4 of ADR-164 — a federated business-management autopilot layer built over ruflo-federation + agentbbs . 
 What you get 
 7 new MCP tools (345 → 352) 
 Federation BBS (4 tools) — register/publish/watch/human-join over agentbbs@~0.1.0 as a federation-peer kind, with optional-dep + graceful-degraded fallbacks. 
 Business pods (2 tools) — business_pod_validate + business_pod_route_backend for the new domain-pod scaffolding. 
 http_fetch (1 tool) — security-default-rejects (private IPs, auth headers) with URL allowlist + timeout + response-size cap. 
 7 business pod templates 
 Pre-built JSON templates for sales / marketing / finance / ops / support / hr / exec, each with per-pod PII policy (SOC2 / GDPR), budget caps, schedules, and routing affinity. 
 Atomic SQLite budget tracker (ADR-164.1) 
 Closes the "Expired Commit Leak" found in peer review: even if an LLM call exceeds the reservation window, the spend is recorded against the room's monthly cap with a COMMIT_AFTER_EXPIRY warning. Behind CLAUDE_FLOW_BBS_ATOMIC_BUDGET=1 for opt-in rollout (per ADR-164.1 §12). 
 ruflo federation trust elevate CLI 
 Founder-bootstrap escape hatch (ADR-164 §3.5.4) — bypasses the 500-interaction trust threshold for new federation peers, with mandatory --reason + --audit flags. 
 Architecture (BBS-as-special-tier-peer) 
 A BBS room is a federation node. send to its node-id = broadcast to the room. ruflo nodes subscribe by role; humans join via the agentbbs web UI. The bridge is 4 new MCP tools — no new transports, no new value objects, no new entities. 
 Upstream coordination 
 ruvnet/agentbbs#3 merged — adds the ruflo-integration regression-guard CI workflow that runs on every PR + nightly cron. 
 Verified 
 
 108 vitest cases new this release (44 + 40 + 21 + 3 regression rounds) 
 352/352 MCP tools pass ADR-112 discoverability audit (Use-when guidance, ≥80 chars, no duplicates) 
 3 smoke contracts (business-pods, agentbbs, agenticow) all green 
 agentbbs regression-guard passing upstream 
 
 Phase 5+ deferrals (next release) 
 
 pod-tick --live mode (Managed Agent + claude-p wiring) 
 Sweeper-timer integration (daemon worker) 
 agentbbs create_board upstream MCP tool ( agentbbs#3 comment ) 
 Streaming federation_bbs_watch 
 Federation-trust ACL gate (founder-only crypto check) 
 
 Install / upgrade 
 npx ruflo@latest # 3.16.0 
npx @claude-flow/cli@latest # 3.16.0 
npx claude-flow@latest # 3.16.0 
 npm dist-tags 
 @claude-flow/cli latest=3.16.0 alpha=3.16.0 v3alpha=3.16.0
claude-flow latest=3.16.0 alpha=3.16.0 v3alpha=3.16.0
ruflo latest=3.16.0 alpha=3.16.0 v3alpha=3.16.0
 
 Related 
 
 PR #2503 — feat: ADR-164 Phases 1-4 
 PR #2504 — chore(release): 3.15.0 → 3.16.0 
 ADR docs/adr/ADR-164-agentbbs-business-autopilot.md (1412 lines) 
 ADR docs/adr/ADR-164.1-budget-tracker-atomicity.md (775 lines) 
 Upstream PR agentbbs#3