---
id: inbox_77a63b43
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.17"
author: "ruvnet"
published_at: 2026-07-27T02:45:24+00:00
fetched_at: 2026-07-27T22:45:54.297688+00:00
content_hash: "6b7ee41e1d7f03d04619fc348def44b15fd48475fd10b83a15c28e65b6fe36fd"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.17 — PlanFlip + MemPoison gates (#2752 dream-cycle)

Two more dream-cycle security gates, reusing ChannelGuard's detector. 
 Added 
 PlanFlip gate — ruflo security scan-plan 
Scans agent-emitted plans (inline -p or --plan-file &lt;path&gt; ) for injected steps that would shift the plan's authority. Gate FIRES on high-severity findings (default) or ANY finding ( --strict ). Exit 2 signals fire so callers can gate distribution. 
 MemPoison gate — ruflo memory store --scan-content 
Runs the scanner on the value BEFORE persistence and refuses the write with exit 2 on any finding. Also activates globally via RUFLO_MEMORY_SCAN_ON_WRITE=1 for safety-critical flows. Refusal is authoritative — does not fall through to the sql.js path. 
 Both gates reuse ChannelGuard's scanChannelMessage from the shared security/injection-catalog + channel-guard modules — adding a phrase to the catalog now strengthens all four surfaces at once (composition-scan, channel-scan, scan-plan, memory-store). 
 Verification 
 
 Regression tests: 6/6 for #2752 (detector + 3 CLI wire E2E via real execFileSync ) 
 Total security tests ( #2752 + #2783 ): 21/21 
 E2E on shipped CLI: memory store with injected value → exit 2, plan file with injected step → exit 2 with FIRE verdict 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.17 
 Refs: dream-cycle #2752 (2026-07-21).