---
id: inbox_aa7e51d9
source: rtk-releases
source_type: rss
url: "https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.1-rc.297"
author: "rtk-release-bot[bot]"
published_at: 2026-06-30T11:17:05+00:00
fetched_at: 2026-07-01T23:31:26.445922+00:00
content_hash: "d46ca05cbafec6cb8fb711edb887c323f3462b34eab23cbd6a524bbd220bf0d5"
lang: en
caption_quality: None
raw: true
topics: []
---

# dev-0.43.1-rc.297

fix(openclaw): handle exit code 3 from rtk rewrite 

 Interpret all RTK rewrite exit codes and respond appropriately:
 - Exit 0 (Allow): auto-apply rewrite
 - Exit 1 (Passthrough): no RTK equivalent, pass through unchanged
 - Exit 2 (Deny): block the call entirely
 - Exit 3 (Ask): rewrite available, require user approval via
 requireApproval with allow-once/deny decisions 

 Uses execFileSync (not execSync) to avoid shell injection. Returns
 a [string | null, RewriteVerdict?] tuple from tryRewrite so the
 before_tool_call hook can react to each verdict type. 

 "allow-always" omitted from allowedDecisions because OpenClaw does
 not auto-persist approval for plugin hooks — see:
 https://docs.openclaw.ai/plugins/plugin-permission-requests#troubleshooting 

 Closes #2202