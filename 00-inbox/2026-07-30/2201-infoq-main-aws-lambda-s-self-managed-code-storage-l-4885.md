---
id: inbox_be3daadb
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/07/lambda-self-managed-storage/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Steef-Jan Wiggers"
published_at: 2026-07-30T07:57:00+00:00
fetched_at: 2026-07-30T22:01:37.238675+00:00
content_hash: "488529bda8a378554a8ee3f860eed717e12f8b4900e4c70865804e489ec94b29"
lang: en
caption_quality: None
raw: true
topics: []
---

# AWS Lambda's Self-Managed Code Storage Lifts the Account Quota, Not the Function Size Limit

AWS Lambda can now reference deployment packages directly in customer-owned S3 buckets, removing the per-Region code storage quota and raising the managed default from 75 GB to 300 GB. Per-function package limits are unchanged, and UpdateFunctionCode is still required after replacing an object. Terraform provider support remains an open enhancement request. By Steef-Jan Wiggers