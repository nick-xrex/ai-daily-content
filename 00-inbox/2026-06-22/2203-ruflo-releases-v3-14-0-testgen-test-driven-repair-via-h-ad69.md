---
id: inbox_b340a666
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.14.0"
author: "ruvnet"
published_at: 2026-06-22T21:16:30+00:00
fetched_at: 2026-06-22T22:03:43.561495+00:00
content_hash: "ad69d8dd0019e66db2a6cc9e941a79005a3dcef4451d7f4eeeb66eee15dbce2c"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.14.0 — testgen Test-Driven Repair via headless `claude -p`

✨ New feature — Test-Driven Repair 
 Closes the loop the existing TDD plugins didn't: we generate tests; now we also fix the code to satisfy them. Inspired by agent-harness-generator ADR-175 ; implemented via headless `claude -p` for tighter integration with our stack. 
 What you can do now 
 ```bash 
 Failing CI test → verified fix PR for pennies 
 npx ruflo@latest hooks testgen tdd-repair 
--repo . 
--test tests/failing.test.ts 
--test-command "npx vitest run tests/failing.test.ts" 
--confirm 
``` 
 Or call `mcp__claude-flow__testgen_tdd_repair` from any agent. 
 How it works 
 
 Pre-flight: run the test command. Refuse if it already passes (catches `--test-command` typos). 
 Spawn `claude -p` with capability-restricted toolset (`--allowedTools Read,Edit,Bash`) and hard-capped budget (`--max-budget-usd`). 
 Focused prompt: read the failing test, fix the source, do NOT modify the test, verify by running it. 
 Re-run the test. The exit code IS the fitness function — no LLM-as-judge. 
 If green: emit success + per-attempt usage (`cost_usd`). If red after `--max-attempts`: emit failure receipts; workspace left as-is for review. 
 
 Safety posture 
 
 `--confirm` REQUIRED (dry-run otherwise) 
 Hard `--max-budget-usd` cap (default $5) 
 `--allowedTools Read,Edit,Bash` (no MCP, no network, no arbitrary writes) 
 Prompt forbids modifying the test or adding dependencies 
 15 min hard timeout 
 
 Smoke proof 
 `docs/benchmarks/tdd-repair/SMOKE-2026-06-22.md` — built fixture with `add(a,b) → a-b` bug; pre-repair 2/2 fail, post-repair 2/2 pass. 
 Cost ladder 
 
 
 
 Tier 
 Model 
 Per-attempt typical 
 
 
 
 
 1 
 Haiku (default) 
 $0.02 – $0.20 
 
 
 2 
 Sonnet 
 $0.30 – $2.00 
 
 
 3 
 Opus 
 $1.50 – $8.00 
 
 
 
 Conformant mode (`--no-test-oracle`) 
 Scoped for a follow-up ADR. Today `--no-test-oracle` returns a clear config error. 
 Distribution 
 
 
 
 Package 
 latest 
 alpha 
 v3alpha 
 
 
 
 
 `@claude-flow/cli` 
 3.14.0 
 3.14.0 
 3.14.0 
 
 
 `claude-flow` 
 3.14.0 
 3.14.0 
 3.14.0 
 
 
 `ruflo` 
 3.14.0 
 3.14.0 
 3.14.0 
 
 
 
 Cross-references 
 
 🔗 Inspired by: agent-harness-generator/packages/darwin-mode ADR-175 
 🔗 Smoke receipts: docs/benchmarks/tdd-repair/SMOKE-2026-06-22.md 
 🔗 Companion: testgen `test-gaps` skill (gap → fix loop scoped for next iteration) 
 
 
 🤖 Generated with RuFlo