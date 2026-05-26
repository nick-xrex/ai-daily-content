---
id: inbox_24f07bbb
source: ecc-releases
source_type: rss
url: "https://github.com/affaan-m/ECC/releases/tag/v2.0.0-rc.1"
author: "github-actions[bot]"
published_at: 2026-05-25T19:36:47+00:00
fetched_at: 2026-05-26T00:14:48.602433+00:00
content_hash: "cd3b54882ae0ce5d28688ae876fc302e5dc55e291aaae9be05f59bccf5ded22a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.0.0-rc.1

ECC 2.0.0-rc.1 
 ECC 2.0.0-rc.1 is the first release-candidate surface for ECC as a cross-harness operating system for agentic work. 
 Claude Code remains a first-class target. Codex, OpenCode, Cursor, Gemini, Zed, and terminal-only workflows are now treated as execution surfaces that can share the same skills, rules, hooks, MCP conventions, release gates, and operator workflows. 
 What is new 
 
 243 public skills packaged across coding, research, security, media, enterprise ops, and agent workflows. 
 A rollout-derived optimization pack for agents that need measured speedups instead of one-shot prompting. 
 A public teaser Itô prediction-market skill pack for read-only research, basket comparison, oracle-style market intelligence, and risk review. Itô API access stays gated and separate from ECC Tools billing. 
 AgentShield and supply-chain follow-up surfaces after the Mini Shai-Hulud/TanStack campaign work. 
 Cross-harness package surfaces for Claude Code, Codex, OpenCode, Cursor, Gemini, Zed, and terminal workflows. 
 Release-readiness gates for preview packs, public-action approvals, release URL ledgers, operator readiness, discussion state, Linear roadmap coverage, and supply-chain checks. 
 
 New optimization skills 
 
 parallel-execution-optimizer : splits work into safe parallel lanes, separate worktrees, concurrent reads, and mergeable outputs. 
 benchmark-optimization-loop : turns vague speed goals into measured variants, baselines, promotion gates, and rollback notes. 
 data-throughput-accelerator : pushes large scans and corpus work into indexed, checkpointed, manifest-driven pipelines. 
 latency-critical-systems : profiles p50, p95, queue time, cache hit rate, cold starts, and freshness before changing runtime paths. 
 recursive-decision-ledger : converts repetitive rollout prompting into reusable decision ledgers with prior winners and explicit promotion criteria. 
 
 Why this matters 
 ECC is no longer just a Claude Code config pack. The release candidate packages the reusable layer underneath agent work: skills, hooks, rules, MCP conventions, command surfaces, test gates, and operator discipline that can move across harnesses. 
 The goal is simple: stop rewriting the same prompts, stop relying on fragile local habits, and turn working agent behavior into portable infrastructure. 
 Download 
 
 Release tarball: https://github.com/affaan-m/ECC/releases/download/v2.0.0-rc.1/ecc-universal-2.0.0-rc.1.tgz 
 Full changelog: v1.10.0...v2.0.0-rc.1 
 
 Additional registry and directory surfaces will follow the remaining publication gates. For this RC, the GitHub prerelease and tarball are the public packaged artifact. 
 Verification 
 This release candidate passed the local validation gate used for the final packaging work: 
 
 npm test : 2568 passing 
 npm run lint : passing 
 node scripts/ci/validate-skills.js : 243 skills 
 node scripts/ci/validate-install-manifests.js : 31 modules, 75 components, 6 profiles 
 node scripts/ci/validate-no-personal-paths.js : passing 
 npm run preview-pack:smoke -- --format json : passing 
 npm pack --dry-run : includes the new optimization and Itô skill packs 
 
 RC boundary 
 This is a release candidate, not the final GA claim. Secrets, private operator state, OAuth tokens, personal datasets, and unsanitized local automations are not part of the public package.