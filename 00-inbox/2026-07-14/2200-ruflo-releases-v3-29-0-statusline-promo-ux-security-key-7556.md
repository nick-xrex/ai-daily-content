---
id: inbox_e0f18e86
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.29.0"
author: "ruvnet"
published_at: 2026-07-14T16:58:19+00:00
fetched_at: 2026-07-14T22:00:25.097307+00:00
content_hash: "755650c2f9440d4a2ee653972f51ff67177615c4142b82d38f99924ba748f497"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.29.0 — Statusline promo UX + security key rotation

Highlights 
 Two new user-facing CLI subcommands to control the statusline promo row: 
 
 ruflo funnel accept — skip the 24h disclosure grace so promo rotation starts immediately on the next render (instead of waiting a full day after first-render). 
 ruflo funnel open — open the currently-shown promo URL in your default browser. Terminal-independent, so it works on hosts that don't route clicks to the terminal's link handler (VS Code integrated terminal, some Windows configs, etc.). 
 
 Statusline row 3 (promo) improvements: 
 
 Whole row wrapped in one OSC 8 hyperlink — click anywhere on the row opens the URL. 
 Visible (domain) suffix so the destination is readable and copyable even where OSC 8 doesn't render. 
 Bright-white bold styling on the "manage: " tail so it visually reads as "shell command to type". 
 Ellipsis on truncation instead of silent mid-word chop. 
 
 Windows console-flash mitigations (partial — the primary cause is upstream at anthropics/claude-code#70200 ; we mitigate what our own subprocess calls contribute): 
 
 windowsHide: true on 3 subprocess spawn sites: statusline CLI delegation, statusline safeExec helper, hook-handler detached background refresh. 
 Statusline cache TTL bumped 60s → 300s, so the outer wrapper spawn (Claude Code's, not ours) fires ~5× less often. Promo/insight rotation still runs on its own tighter 20s clock. 
 New ruflo tracking issue: #2669 (mirrors upstream #70200, #14828, #66540). 
 
 Security 
 Helpers-signing key rotated ( RUFLO_HELPERS_PUBKEY v2). The previous private key was accidentally captured in a Claude Code session transcript today. Mitigation done at rotation time: 
 
 New Ed25519 keypair generated. 
 Old GCP Secret Manager version destroyed (not just disabled). 
 New pubkey baked into src/init/helper-signing.ts and scripts/verify-helpers.mjs . 
 Helpers manifest re-signed with the new key before publish. 
 
 Upgrade urgency: Users on ruflo ≤ 3.28.0 still trust the OLD (now-leaked) pubkey. An attacker with the leaked key could forge a helpers manifest that verifies on those old installs. Upgrade to v3.29.0 as soon as possible — new installs pick up the new pubkey and validate only manifests signed with the new key. 
 Compatibility 
 
 Semver MINOR (3.28.0 → 3.29.0) — additive CLI subcommands, no breaking changes. 
 Key rotation is atomic per-version — no dual-pubkey transition needed. Each CLI version's baked pubkey validates the manifest shipped with that same version. 
 
 PRs merged 
 
 #2671 — feat(funnel,statusline): accept + open subcommands, whole-row-clickable promo, Windows flash mitigations 
 #2673 — security: rotate helpers-signing key (RUFLO_HELPERS_PUBKEY v2) 
 
 Tracking issues 
 
 #2669 — Windows cmd/console flash (upstream anthropics/claude-code#70200 ) 
 
 Install 
 npx ruflo@latest init
 # or 
npm install -g @claude-flow/cli@3.29.0