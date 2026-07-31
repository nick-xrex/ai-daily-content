---
id: inbox_f12aa69b
source: medium-towards-data-science
source_type: rss
url: "https://towardsdatascience.com/avoiding-entity-key-drift-in-a-data-lake-step-1-normalization/"
author: "Rahul Saha"
published_at: 2026-07-29T12:00:00+00:00
fetched_at: 2026-07-29T23:50:25.300928+00:00
content_hash: "b4554beb9c0228c18f43c5a6fd2a630e806f6fa813a556f3cfa28dffd74b860d"
lang: en
caption_quality: None
raw: true
topics: []
---

# Avoiding Entity Key Drift in a Data Lake: Step 1, Normalization

This is the opening piece of a four-part deep dive series, on building a high-frequency streaming pipeline against a live public API. The data source is openSenseMap, a citizen-science IoT network used for climate research, mostly in Germany. A live public API is what makes it useful: it produces data-quality problems and edge cases that clean sample datasets never show. This article focuses on step-1: Normalization, later pieces cover matching algorithms, adaptive polling and noise filtering, and a vendor-agnostic Apache Iceberg pipeline with Terraform that runs locally in Docker and moves to AWS or GCP with minimal change. 
 The post Avoiding Entity Key Drift in a Data Lake: Step 1, Normalization appeared first on Towards Data Science .