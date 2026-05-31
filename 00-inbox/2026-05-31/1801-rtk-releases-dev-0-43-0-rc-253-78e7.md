---
id: inbox_45d41293
source: rtk-releases
source_type: rss
url: "https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.253"
author: "rtk-release-bot[bot]"
published_at: 2026-05-31T15:24:37+00:00
fetched_at: 2026-05-31T18:01:19.122069+00:00
content_hash: "78e744a3ce3208cead34322c3c3f3da91f8c693f5e0b8fdb11c93f18c9d45ae3"
lang: en
caption_quality: None
raw: true
topics: []
---

# dev-0.43.0-rc.253

fix(init): use fs::canonicalize for symlink resolution 

 Simplify resolve_atomic_target() per review feedback — fs::canonicalize
 handles chained symlinks, relative paths, and all edge cases. 

 Co-authored-by: Roopesh &lt;roopesh1724989@gmail.com&gt;