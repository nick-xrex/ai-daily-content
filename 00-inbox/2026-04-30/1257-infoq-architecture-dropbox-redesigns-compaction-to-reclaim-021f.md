---
id: inbox_a9d42d0f
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/04/dropbox-tiered-compaction/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Renato Losio"
published_at: 2026-04-30T09:23:00+00:00
fetched_at: 2026-05-01T12:57:11.409004+00:00
content_hash: "021f9f0a86280e3bd754302fcb3ac0836507adca71768b667b48705196d7e030"
lang: en
caption_quality: None
raw: true
topics: []
---

# Dropbox Redesigns Compaction to Reclaim Space from Underfilled Storage Volumes

<img src="https://res.infoq.com/news/2026/04/dropbox-tiered-compaction/en/headerimage/generatedHeaderImage-1776799745799.jpg" /><p>Dropbox recently explained how it improved storage efficiency in Magic Pocket, the company's internal immutable blob store for storing user files at scale, by redesigning compaction strategies to reclaim space from severely underfilled storage volumes. The system now periodically reorganizes valid data into new volumes, allowing old, partially used ones to be cleared and reused.</p> <i>By Renato Losio</i>