---
id: inbox_4ce58d61
source: openai-blog
source_type: rss
url: "https://openai.com/index/fine-tuning-gpt-2"
author: ""
published_at: 2019-09-19T07:00:00+00:00
fetched_at: 2026-04-21T01:58:18.444635+00:00
content_hash: "14dca5806fda0e607b2886f58ef2e5461e5cdf88a8a2affe171f53d11d634139"
lang: en
caption_quality: None
raw: true
topics: []
---

# Fine-tuning GPT-2 from human preferences

We’ve fine-tuned the 774M parameter GPT-2 language model using human feedback for various tasks, successfully matching the preferences of the external human labelers, though those preferences did not always match our own. Specifically, for summarization tasks the labelers preferred sentences copied wholesale from the input (we’d only asked them to ensure accuracy), so our models learned to copy. Summarization required 60k human labels; simpler tasks which continue text in various styles required only 5k. Our motivation is to move safety techniques closer to the general task of “machines talking to humans,” which we believe is key to extracting information about human values.