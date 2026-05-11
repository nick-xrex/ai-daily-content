---
id: inbox_91ad397f
source: hackernews
source_type: hn
url: "https://github.com/imtomt/ymawky"
author: "imtomt"
published_at: 2026-05-10T03:01:44+00:00
fetched_at: 2026-05-10T22:39:19.072443+00:00
content_hash: "f462de7ebbb20b1602a28ed1758da74833b6edfea842eb4901b24d23d110e861"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: Building a web server in assembly to give my life (a lack of) meaning

This is ymawky, a static file web server for MacOS written entirely in ARM64 assembly. It supports GET, PUT, DELETE, HEAD, and OPTIONS requests, and supports Range: bytes=X-Y headers (which allows scrubbing for video streaming). It decodes percent-encoded URLs, strictly enforces docroot, serves custom error pages for any HTTP error response, supports directory listing, and has (some) mitigations against slowloris-like attacks. I’ve also written a more detailed writeup here: https:&#x2F;&#x2F;imtomt.github.io&#x2F;ymawky&#x2F;