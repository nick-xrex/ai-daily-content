---
id: inbox_e3b2b6b4
source: rtk-releases
source_type: rss
url: "https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.278"
author: "rtk-release-bot[bot]"
published_at: 2026-06-16T21:48:04+00:00
fetched_at: 2026-06-16T22:00:30.061467+00:00
content_hash: "d4f0d5c772750b0a283360991adf6023fde89899af4d1d9b211f0152b48f083a"
lang: en
caption_quality: None
raw: true
topics: []
---

# dev-0.43.0-rc.278

fix(grep): use portable --null in system grep fallback (BSD/macOS) 

 The system-grep fallback (used when ripgrep is not installed) passed
 -rnHZ, relying on -Z for the NUL filename separator the match parser
 requires. -Z only means --null on GNU grep; on BSD/macOS grep it is an
 alias for --decompress (zgrep mode), so output is plain
 file:line:content with no NUL. parse_match_line() then matches zero
 filenames and every result collapses into "N matches in 0 files" with
 all lines hidden behind [+N more]. 

 Use the long option --null instead, which both GNU and BSD grep define
 as "print a zero-byte after the file name". 

 Related to #2310 

 Co-Authored-By: Claude Fable 5 &lt;noreply@anthropic.com&gt;