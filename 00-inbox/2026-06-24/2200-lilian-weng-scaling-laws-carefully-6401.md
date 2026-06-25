---
id: inbox_d5ac02ab
source: lilian-weng
source_type: rss
url: "https://lilianweng.github.io/posts/2026-06-24-scaling-laws/"
author: ""
published_at: 2026-06-24T00:00:00+00:00
fetched_at: 2026-06-25T22:00:34.445756+00:00
content_hash: "6401a71c2a3ca6d1b635868430b10d0a952d6a7bca766d099d5bf794488b367e"
lang: en
caption_quality: None
raw: true
topics: []
---

# Scaling Laws, Carefully

Scaling laws are one of the most critical empirical findings in deep learning. The observation is simple in form: the training loss $L$ decreases predictably as we scale up model size $N$, dataset size $D$, and compute $C$, following a power-law curve, which appears as a straight line on a log-log plot. We can view scaling laws as a framework for describing the relationship between compute, loss, model size and data; at its core, it is about how to allocate precious compute optimally between $N$ and $D$.