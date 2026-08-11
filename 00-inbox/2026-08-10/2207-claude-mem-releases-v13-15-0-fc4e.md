---
id: inbox_dd987416
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.15.0"
author: "thedotmack"
published_at: 2026-08-10T20:35:46+00:00
fetched_at: 2026-08-10T22:07:38.555073+00:00
content_hash: "fc4ebb2278f7413f023d6faa4c7582d6a9934b84364db45f36e4e4d01adffa9c"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.15.0

7-day Pro trial in the installer 
 The npx installer can now start a free week of CMEM Pro end to end: 
 
 Trial funnel in npx claude-mem install — pitch → email entry → magic-link → Stripe checkout, with the installer polling the pairing API and finishing setup automatically once the trial starts ( #3524 ) 
 Device-code approval — the terminal shows a short code (XXXX-XXXX) that you confirm in the browser before credentials are delivered, closing a pairing-secret disclosure vector ( #3524 ) 
 Live model pricing — the installer now fetches model pricing from the API instead of shipping hardcoded numbers ( #3515 ) 
 
 Requires the cmem.ai backend released today (trial routes + cli_pairings device-authorization grant).