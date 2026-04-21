---
id: inbox_df15ab69
source: openai-blog
source_type: rss
url: "https://openai.com/index/reptile"
author: ""
published_at: 2018-03-07T08:00:00+00:00
fetched_at: 2026-04-21T01:58:18.528026+00:00
content_hash: "606c59e17cfe592dad2b8d7010800dac7777918b52ffd93cfe4cccfa1c32da95"
lang: en
caption_quality: None
raw: true
topics: []
---

# Reptile: A scalable meta-learning algorithm

We’ve developed a simple meta-learning algorithm called Reptile which works by repeatedly sampling a task, performing stochastic gradient descent on it, and updating the initial parameters towards the final parameters learned on that task. Reptile is the application of the Shortest Descent algorithm to the meta-learning setting, and is mathematically similar to first-order MAML (which is a version of the well-known MAML algorithm) that only needs black-box access to an optimizer such as SGD or Adam, with similar computational efficiency and performance.