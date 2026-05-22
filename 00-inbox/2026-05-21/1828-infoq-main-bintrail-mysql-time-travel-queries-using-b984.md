---
id: inbox_e2c0fb51
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/05/bintrail-mysql-timetravel/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Renato Losio"
published_at: 2026-05-21T17:03:00+00:00
fetched_at: 2026-05-21T18:28:26.957736+00:00
content_hash: "b98424ceb9377c8b3be8471ef3d4d398df47786ca8686df22820af94520c88b4"
lang: en
caption_quality: None
raw: true
topics: []
---

# Bintrail: MySQL Time-Travel Queries Using Indexed Binlogs

Bintrail is a recently introduced layer that brings point-in-time queries and row-history lookups to MySQL, the only major relational database lacking native temporal querying. Using indexed binlogs behind ProxySQL and without modifying MySQL or application code, Bintrail supports querying data as of a past timestamp and reviewing change history, primarily for recovery and audit scenarios. By Renato Losio