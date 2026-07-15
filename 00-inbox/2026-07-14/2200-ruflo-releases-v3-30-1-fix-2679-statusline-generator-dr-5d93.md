---
id: inbox_289004ee
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.30.1"
author: "ruvnet"
published_at: 2026-07-14T20:14:05+00:00
fetched_at: 2026-07-14T22:00:25.091656+00:00
content_hash: "5d936356399c5b924725545662e6b036dbffda79e3a82f4c71d38d3d73bbce8c"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.30.1 — fix #2679 statusline generator drift

What 
 PATCH release closing #2679 — the statusline generator drift discovered during the v3.30.0 release flow. 
 Fix 
 `generateStatuslineScript()` in `v3/@claude-flow/cli/src/init/statusline-generator.ts` no longer inlines a 1000-line template string. It now READS `.claude/helpers/statusline.cjs` as its single source of truth and substitutes two known values (`maxAgents`, `bakedVersion`). Every future edit to the helper propagates to `ruflo init` output automatically — no manual sync required. 
 Impact 
 
 Fresh installs / re-inits : get the current v3.29.0-era helper (whole-row-clickable OSC 8, `(domain)` suffix, ellipsis on truncation, bright-white bold command styling, 300s cache TTL, `windowsHide` on every subprocess spawn) instead of the pre- #2195 non-delegation shape that the generator had frozen at. 
 Existing installs : unchanged. The deployed helper is already correct; this fix only affects new `ruflo init` writes. 
 
 CI 
 Three static-regression guards updated for the read-and-substitute pattern: 
 
 `.github/workflows/v3-ci.yml` — statusline generator delegation smoke 
 `scripts/audit-fix-invariants.mjs` — #2196 delegation invariant + NEW #2679 sync invariant 
 `scripts/smoke-statusline-generator-delegation.mjs` — Layer 1 static contract 
 
 Each now greps the HELPER for the delegation content (where it now lives) with a paired assertion that the generator still reads it. Drift on either side of the sync is caught. 
 Related 
 
 PR #2680 — the fix 
 Issue #2679 — closed 
 v3.30.0 release (`74bc81f8e` / `fea1d9e95`) — where this drift was first surfaced 
 
 Install 
 ```bash 
npx ruflo@latest init 
 or 
 npm install -g @claude-flow/cli@3.30.1 
```