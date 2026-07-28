---
id: inbox_a9f9cac5
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.16"
author: "ruvnet"
published_at: 2026-07-27T02:36:33+00:00
fetched_at: 2026-07-27T22:45:54.314821+00:00
content_hash: "156047e043f5279ede3df1364f0baaeb778d057c434b0b8f07ffbc5a2102867f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.16 — ChannelGuard companion (#2783 dream-cycle pair complete)

Completes the dream-cycle #2783 ADR-320 recommendation: Composition Inspector (v3.32.15) + ChannelGuard (this release). 
 Added 
 ruflo security channel-scan — deterministic (no LLM) inter-agent message scanner. arXiv 2607.19430: individually-safe LLM agents propagate injection payloads through inter-agent message channels; per-message safety checks pass at each hop. ChannelGuard closes the gap by scanning content at the routing boundary. 
 Four attack signatures: 
 
 Injection-phrase — shared 16-phrase catalog with composition-scan (new src/security/injection-catalog.ts ; a phrase added there strengthens both surfaces). 
 Role-shift — system: / assistant: / user: markers appearing INSIDE the message body (start-of-message preambles allowed). 
 Encoded-payload — long base64/hex runs that could hide obfuscated instructions. 
 Zero-width/bidi unicode — U+200B, U+200C, U+200D, U+FEFF, U+202A-E, U+2066-9 — zero legitimate use in agent messages. 
 
 Usage: 
 ruflo security channel-scan -m "...message text..."
ruflo security channel-scan --message-file ./inbox/msg-1234.txt
 
 Exit codes: 0 safe, 2 flagged — shell-integration friendly ( channel-scan &amp;&amp; forward skips flagged messages). 
 Verification 
 
 Regression tests: 9/9 for ChannelGuard, 6/6 for Composition Inspector, 15/15 total . 
 E2E on malicious message → 5 findings across 3 signature categories. 
 E2E on benign handoff → SAFE, 0 findings. 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.16 
 Refs: dream-cycle #2783 .