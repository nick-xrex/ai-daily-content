---
id: inbox_493efffa
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/05/linkedin-kernel-lock-freeze/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Sergio De Simone"
published_at: 2026-05-27T18:00:00+00:00
fetched_at: 2026-05-27T23:45:23.612876+00:00
content_hash: "8e37a25bd2d038996813930f94e2a4d309514fdc28e6ed5226d4b82d2b94bd06"
lang: en
caption_quality: None
raw: true
topics: []
---

# How LinkedIn Identified a Kernel Lock Contention Issue Causing Recurring System Freezes

When LinkedIn engineers encountered short-lived, recurring outages where the database powering their user feed became unavailable and then recover without leaving helpful traces, they had to devise a novel approach to uncover the root cause using off-CPU profiling with eBPF. By Sergio De Simone