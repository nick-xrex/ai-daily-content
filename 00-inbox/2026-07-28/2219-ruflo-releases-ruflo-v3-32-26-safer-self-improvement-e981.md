---
id: inbox_ffc26275
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.26"
author: "ruvnet"
published_at: 2026-07-28T20:29:19+00:00
fetched_at: 2026-07-28T22:19:48.595758+00:00
content_hash: "e981587f160e0775b4c1fc5d354f32c55850fc3e890cadf0b564bd231d2bdce4"
lang: en
caption_quality: None
raw: true
topics: []
---

# Ruflo v3.32.26 — Safer Self-Improvement

Ruflo v3.32.26 — Safer Self-Improvement 
 Ruflo can now test improvements to its retrieval behavior without changing the configuration you are currently using. 
 This release introduces a controlled flywheel: 
 evaluate → review → promote
 
 Ruflo evaluates candidate settings, records the results in a verifiable receipt, and waits for you to approve an accepted candidate. Nothing is promoted automatically. 
 Why this matters 
 Self-improvement should not mean handing control to an optimizer. 
 With v3.32.26, you can: 
 
 test retrieval-policy improvements against held-out tasks; 
 compare quality, latency, token use, failures, and cost limits; 
 inspect the evidence before making a change; 
 activate an accepted candidate with an explicit command; 
 audit what changed through receipts and promotion history. 
 
 Darwin can explore and propose candidates, but Ruflo remains responsible for deciding whether a candidate is safe to promote. 
 Install or upgrade 
 npm install --global ruflo@3.32.26
ruflo --version 
 You can also try this release without a global installation: 
 npx ruflo@3.32.26 metaharness flywheel status --project-root . 
 Try the flywheel 
 Check the current state: 
 ruflo metaharness flywheel status --project-root . 
 Run a local evaluation: 
 ruflo metaharness flywheel run \
 --project-root . \
 --proposer local \
 --sample 40 \
 --private-key /path/to/flywheel-private.pem \
 --public-key /path/to/flywheel-public.pem 
 Review the results: 
 ruflo metaharness flywheel receipts --project-root . 
ruflo metaharness flywheel history --project-root . 
 Promote an accepted result: 
 ruflo metaharness flywheel promote &lt; receipt-id &gt; \
 --project-root . \
 --public-key /path/to/flywheel-public.pem \
 --confirm 
 The end-user quick start includes signing-key setup and a complete walkthrough. 
 Also new 
 
 First-class metaharness flywheel commands in the CLI and MCP. 
 Darwin candidate evolution through metaharness evolve . 
 Stable benchmark creation and verification through metaharness bench . 
 Signed receipts that detect altered evaluation evidence. 
 Atomic, one-time promotion with consistent crash recovery. 
 Safe local operation when the optional Darwin or Flywheel packages are not installed. 
 
 Safe by default 
 
 Evaluation never changes the active policy. 
 Promotion requires an accepted receipt and explicit --confirm . 
 Stale, changed, untrusted, or already-used receipts are rejected. 
 Candidate resource limits are enforced before candidates are considered. 
 Darwin failures do not silently become Darwin-authorized promotions. 
 Automatic unattended promotion is not enabled in this release. 
 
 v3.32.26 currently applies the new loop to bounded retrieval-policy tuning. Tool-policy evolution, model-policy evolution, and unattended autopilot remain disabled until their separate security and spending controls are ready. 
 Compatibility 
 This is a backward-compatible patch release. Existing Ruflo workflows continue to work, and the new flywheel remains opt-in. 
 Published packages: 
 ruflo@3.32.26
claude-flow@3.32.26
@claude-flow/cli@3.32.26
 
 Validation 
 The release passed the focused flywheel suite, signed-receipt and tamper checks, stale-state and crash-recovery tests, resource-limit tests, and a 100-way concurrent promotion test that produced exactly one successful promotion. 
 Learn more 
 
 End-user quick start 
 ADR-322 architecture and safety model 
 Implementation PR #2817 
 Full changelog