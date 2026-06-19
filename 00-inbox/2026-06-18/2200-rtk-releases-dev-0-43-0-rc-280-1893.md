---
id: inbox_fa0d92a3
source: rtk-releases
source_type: rss
url: "https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.280"
author: "rtk-release-bot[bot]"
published_at: 2026-06-18T15:13:04+00:00
fetched_at: 2026-06-18T22:00:32.307408+00:00
content_hash: "1893ae35e1c9dab825649d5bb9bba080a91a8b05773e5a5e5f40568c3149a8fc"
lang: en
caption_quality: None
raw: true
topics: []
---

# dev-0.43.0-rc.280

refactor(grep): extract error-exit decision into pure unit-tested fn 

 Address KuSh review on #2465 :
 - Move the `exit_code &gt;= 2` decision into a pure `is_grep_error_exit`
 function and unit-test it directly (0/1 = normal, &gt;=2 = error),
 instead of faking the rg binary in an integration test.
 - Drop the GREP_ERROR_EXIT const; the doc comment on the function
 conveys the grep/rg exit convention.
 - Remove tests/grep_error_test.rs (faked binary) in favour of the
 unit test. 

 Co-Authored-By: Claude Opus 4.8 (1M context) &lt;noreply@anthropic.com&gt;