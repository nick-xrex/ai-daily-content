---
id: inbox_baf1a37f
source: rtk-releases
source_type: rss
url: "https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.254"
author: "rtk-release-bot[bot]"
published_at: 2026-05-31T15:40:58+00:00
fetched_at: 2026-05-31T18:01:19.089313+00:00
content_hash: "57f422e1bada6e8df5c1a337825a10754dcd8229ec13d0ecfec8f1b9bdd0faf6"
lang: en
caption_quality: None
raw: true
topics: []
---

# dev-0.43.0-rc.254

fix(gh): show fallback note when PR/issue body is filtered to empty 

 When `filter_markdown_body()` strips a PR or issue body to empty
 (body contained only badges, images, HTML comments, or horizontal
 rules), `format_pr_view` and `format_issue_view` previously skipped
 the body section silently. Users had no indication that body content
 had been present and filtered. 

 Now both views emit a fallback note when the filtered body is empty
 but the raw body was not: 

 PR view: (body contained only badges/images/comments)
 Issue view: Description: (body contained only badges/images/comments) 

 The 4 added tests cover:
 - PR body with only badges/images/comments -&gt; fallback note appears
 - PR body with real content -&gt; no fallback note (sanity)
 - PR body empty (raw) -&gt; no fallback note (no signal to give)
 - Issue body badges-only -&gt; fallback note appears 

 Closes #235 

 Co-authored-by: polaminggkub-debug &lt;polaminggkub-debug@users.noreply.github.com&gt;