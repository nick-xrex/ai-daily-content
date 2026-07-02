---
id: inbox_afd20f09
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.16.3"
author: "ruvnet"
published_at: 2026-07-01T14:34:02+00:00
fetched_at: 2026-07-01T23:31:23.987014+00:00
content_hash: "ba930af95c844201ef11713d2aadcecd3c7d106f7e8a5c22149519fe38a447a3"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.16.3 — Security release (GHSA-c4hm-4h84-2cf3, ADR-166 MCP bridge RCE)

🔒 Security release 
 Advisory: GHSA-c4hm-4h84-2cf3 — CVSS 9.8 critical 
 ADR: ADR-166: MCP Bridge Unauthenticated RCE — Coordinated Disclosure Remediation 
 What was vulnerable 
 The MCP bridge shipping in ruflo/docker-compose.yml exposed POST /mcp with no authentication. The docker-compose defaults bound the bridge and MongoDB to all interfaces. Combined, an unauthenticated network attacker could invoke tools/call → terminal_execute inside the bridge container, obtain a shell, read every provider API key from the container env, spawn attacker-controlled swarms on the victim's keys, and persist a poisoned pattern into the AgentDB learning store that steers future AI outputs. 
 What's fixed in 3.16.3 
 
 MCP bridge binds 127.0.0.1 by default. Public bind requires MCP_AUTH_TOKEN or the process exits ≠0 at boot with a FATAL message. 
 Bearer auth middleware with timingSafeEqual constant-time compare. 
 Server-side executeTool gate for terminal_execute (opt-in via MCP_ENABLE_TERMINAL=true ) — enforced identically on /mcp , /mcp/:group , and autopilot. This was the missing link that made the disclosed RCE chain reach shell. 
 docker-compose.yml : read_only bridge rootfs, MongoDB --auth on by default, MONGO_INITDB_ROOT_PASSWORD required to boot. 
 CORS allowlist wiring via MCP_CORS_ORIGIN . 
 Static + runtime regression locks (12/12 static, 12/12 runtime green) + CI workflow. 
 
 ⚠️ Operators of any exposed instance MUST 
 
 Firewall :3001 and :27017 immediately if you were running the previous default docker-compose on a public IP. 
 Rotate OPENAI , GOOGLE , OPENROUTER , ANTHROPIC keys. 
 Audit the AgentDB pattern store for injected agentdb_pattern-store entries and purge them. A patched redeploy alone does NOT undo the AI-supply-chain poisoning vector. 
 Audit MongoDB for tampering. 
 
 Breaking change (correct one, for security) 
 docker-compose.yml now refuses to start without MONGO_INITDB_ROOT_PASSWORD . Generate one: 
 echo " MONGO_INITDB_ROOT_PASSWORD= $( openssl rand -base64 32 ) " &gt;&gt; .env 
 For the optional public-bind deployment pattern, additionally: 
 echo " MCP_BIND_HOST=0.0.0.0 " &gt;&gt; .env
 echo " MCP_AUTH_TOKEN= $( openssl rand -base64 32 ) " &gt;&gt; .env
docker compose -f docker-compose.yml -f docker-compose.public.yml up -d 
 Credit 
 Coordinated disclosure by an external security researcher (name to be published with the CVE) and Dragan Spiridonov (ADR-166 co-author). The end-to-end 8-step PoC drove the choice to bind loopback by default rather than paper over with token-only auth — thank you. 
 Verification 
 
 @claude-flow/cli@3.16.3 — npm view @claude-flow/cli@latest version → 3.16.3 
 claude-flow@3.16.3 — npm view claude-flow@latest version → 3.16.3 
 ruflo@3.16.3 — npm view ruflo@latest version → 3.16.3 
 All three dist-tags ( latest , alpha , v3alpha ) point at 3.16.3 
 
 🤖 Generated with RuFlo