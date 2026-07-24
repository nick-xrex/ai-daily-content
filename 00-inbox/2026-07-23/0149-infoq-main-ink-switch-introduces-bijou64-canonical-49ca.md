---
id: inbox_f45f98a5
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/07/bijou64-canonical-varint/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Steef-Jan Wiggers"
published_at: 2026-07-23T09:43:00+00:00
fetched_at: 2026-07-24T01:49:02.735745+00:00
content_hash: "49ca41d5561d2c9dcaaa03f7899782b16798d4cbd2107698223ef08252f32d6d"
lang: en
caption_quality: None
raw: true
topics: []
---

# Ink & Switch Introduces Bijou64: Canonical Variable-Length Integer Encoding for Safe Parsing

Ink & Switch published bijou64, a variable-length integer encoding where every number has exactly one byte representation, closing the canonicality bug class behind attacks on PKCS#1, JWT libraries, and Bitcoin. The design also decodes two to ten times faster than LEB128. Community ports to Elixir, Go, Perl, and Java followed, while HN commenters debated SIMD performance and residual range checks. By Steef-Jan Wiggers