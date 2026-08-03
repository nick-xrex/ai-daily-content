---
id: inbox_7af95836
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.13.0"
author: "thedotmack"
published_at: 2026-08-02T17:15:08+00:00
fetched_at: 2026-08-02T22:12:26.048973+00:00
content_hash: "f6b46362460d0f08ea69eb08624ade36c0e454a3d9907ed626cc568c25d6c281"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.13.0

Sensitive observation type 
 Adds a ninth observation type to the code mode: sensitive — information that isn't quite private, but that you wouldn't want leaking into further content development in the wrong context. Internal URLs, unreleased plans, personal details, business metrics, client or partner names. 
 These fire a Telegram notification by default, the same way security_alert does. 
 Configuring 
 Notifications are controlled by CLAUDE_MEM_TELEGRAM_TRIGGER_TYPES in ~/.claude-mem/settings.json . The default is now security_alert,sensitive . Set the key to any comma-separated list of types, or to an empty string to turn notifications off entirely. 
 Existing installs are migrated automatically: if your trigger list is still the old default of exactly security_alert , it is rewritten to include sensitive . A customized list is left untouched. Without this migration the new type would never have notified on any existing install, because a fresh settings.json is seeded with every default and persisted values win on load. 
 If you had deliberately set your trigger list to exactly security_alert and want it to stay that way, set it to something explicitly different after upgrading — the migration cannot distinguish that case from the seeded default. 
 Also in this release 
 
 Observer prompt fix. The type_guidance prompt still described "6 options" and never listed security_alert or security_note from #2084 . That string is the only type prose the observer model sees — the per-type description fields are never injected into any prompt — so those types have been under-emitted since April. It now enumerates all nine. 
 Corpus filters, the OpenClaw detailed feed, and the weekly-digests legend all recognize the new type. 
 BMP-safe fallback for the new emoji, so injected context can't contribute a surrogate pair (the #2787 failure class). 
 Built plugin artifacts are regenerated, picking up the chroma concurrent-write fix from #3462 that had not yet been built into the shipped bundles. 
 
 Full changelog : v13.12.4...v13.13.0