---
id: inbox_ab94547e
source: openai-blog
source_type: rss
url: "https://openai.com/index/block-sparse-gpu-kernels"
author: ""
published_at: 2017-12-06T08:00:00+00:00
fetched_at: 2026-04-21T01:58:18.549221+00:00
content_hash: "3cb5d664b0c03398704aabfad8e20f69997d73a410914504f77f160d66de86fa"
lang: en
caption_quality: None
raw: true
topics: []
---

# Block-sparse GPU kernels

We’re releasing highly-optimized GPU kernels for an underexplored class of neural network architectures: networks with block-sparse weights. Depending on the chosen sparsity, these kernels can run orders of magnitude faster than cuBLAS or cuSPARSE. We’ve used them to attain state-of-the-art results in text sentiment analysis and generative modeling of text and images.