---
id: inbox_b6ab8e8d
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.11.0"
author: "ruvnet"
published_at: 2026-06-16T16:13:38+00:00
fetched_at: 2026-06-16T22:00:27.550668+00:00
content_hash: "850014c448247603cff76277f67996084e0c5419dca74a687247201146a273a9"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.11.0 — router ADR-148/149 + cost-tracker observability + fleet audits

Merged PR #2398 (squash). 
 Highlights 
 
 Router (v3/@claude-flow/cli) : ADR-148 FastGRNN router artifact lifecycle, ADR-149 per-model cost-optimal routing, Map&lt;task_hash&gt; dedup fixes across decisions/cost-savings/cost-projection. 
 Cost-tracker plugin : forward observability stack — projection / counterfactual / burn / anomaly (MAD) / health (composite gate) / diff (PR regression) / session (per-message drill-down). Stop-hook auto-track. Snapshot git-context. 
 Cache-write visibility : closed at four layers (per-message, time-series, summary, diff) — cache_creation_input_tokens was the silent cost driver. 
 Fleet-wide CI : meta-smoke runner across 32 plugins (402+ structural invariants), exit-bypass antipattern lint, SKILL.md frontmatter audit (117 files), plugin.json manifest audit (34 files), per-plugin timeout/ --fail-fast . 
 
 Install 
 npx ruflo@latest # latest stable 
npx @claude-flow/cli@latest 
 Legacy alpha and v3alpha dist-tags also updated to 3.11.0.