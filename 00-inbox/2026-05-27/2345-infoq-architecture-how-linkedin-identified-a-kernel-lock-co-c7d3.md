---
id: inbox_cc586638
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/05/linkedin-kernel-lock-freeze/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Sergio De Simone"
published_at: 2026-05-27T18:00:00+00:00
fetched_at: 2026-05-27T23:45:25.080498+00:00
content_hash: "c7d3afe1f79dbc20bae076e96fb1bcd087eea78033b0d8ade705036acddca70d"
lang: en
caption_quality: None
raw: true
topics: []
---

# How LinkedIn Identified a Kernel Lock Contention Issue Causing Recurring System Freezes

When LinkedIn engineers encountered short-lived, recurring outages where the database powering their user feed became unavailable and then recover without leaving helpful traces, they had to devise a novel approach to uncover the root cause using off-CPU profiling with eBPF. By Sergio De Simone