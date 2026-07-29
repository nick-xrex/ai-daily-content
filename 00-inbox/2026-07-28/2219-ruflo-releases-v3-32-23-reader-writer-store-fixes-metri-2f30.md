---
id: inbox_145bf3da
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.23"
author: "ruvnet"
published_at: 2026-07-28T03:21:57+00:00
fetched_at: 2026-07-28T22:19:48.615094+00:00
content_hash: "2f308c86a9b72e2c146d917854200086f817021cb43887dfab9a5b9cd08825ef"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.23 — reader/writer store fixes: metrics, backup, swarm status (#2797 #2798 #2799)

Three "clean exit, no real work reflected" bugs reported by @vidaunited on v3.32.22 — all reader/writer store-shape mismatches. Each fixed and validated E2E on the published package. 
 Fixed 
 #2797 — hooks metrics Pattern Learning always 0. The pattern reader filtered on key.includes('pattern') || metadata.type==='pattern' || key.startsWith('learned-') , but no writer produces that shape. The post-task dual-write ( #2786 fix-2) persists learned patterns as routing-decision:* entries in the patterns namespace. Fix: broaden the pattern filter to count namespace==='patterns' and metadata.type==='routing-decision' . Shipped validation: patterns.total 0 → 1 after one hooks post-task --store-results . 
 #2798 — Nightly memory backup silent no-op under CLAUDE_FLOW_ENCRYPT_AT_REST . Same class as #2786 : backupMemoryDb() opened the RFE1-encrypted .swarm/memory.db with better-sqlite3's online-backup API → "file is not a database" → recorded as skipped while the worker reported 100% success. Users with encryption had zero backups behind a green status. Fix: fall back to a plain byte copy (valid — sql.js rewrites the encrypted file wholesale per flush). Shipped validation: RFE1 source → 176 KB snapshot written. 
 #2799 — swarm status always Total 0 agents. swarm status read .swarm/agents/*.json (never written); agent spawn records the count in .claude-flow/metrics/swarm-activity.json . Fix: reconcile against the activity file agent spawn actually writes when the agents dir is empty. Shipped validation: spawn 4 → swarm status Total 0 → 4 (matches agent list ). 
 Verification 
 
 Regression tests: 3/3 pass ( hooks-metrics-swarm-backup-2797-2798-2799.test.ts , real execFileSync repros) 
 Post-publish: all three fixes re-validated on npx ruflo@3.32.23 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.23 
 Closes: #2797 #2798 #2799 .