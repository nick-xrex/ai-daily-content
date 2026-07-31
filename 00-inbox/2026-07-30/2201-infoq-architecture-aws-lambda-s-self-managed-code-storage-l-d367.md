---
id: inbox_83d54939
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/07/lambda-self-managed-storage/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Steef-Jan Wiggers"
published_at: 2026-07-30T07:57:00+00:00
fetched_at: 2026-07-30T22:01:38.867847+00:00
content_hash: "d36726f1a165325e4a974dcf1e5b3f58ae848a61353b22ceac5653714320541b"
lang: en
caption_quality: None
raw: true
topics: []
---

# AWS Lambda's Self-Managed Code Storage Lifts the Account Quota, Not the Function Size Limit

AWS Lambda can now reference deployment packages directly in customer-owned S3 buckets, removing the per-Region code storage quota and raising the managed default from 75 GB to 300 GB. Per-function package limits are unchanged, and UpdateFunctionCode is still required after replacing an object. Terraform provider support remains an open enhancement request. By Steef-Jan Wiggers