---
id: inbox_23c00fbf
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/28/discovering-cryptographic-weaknesses-with-claude/#atom-everything"
author: ""
published_at: 2026-07-28T22:45:37+00:00
fetched_at: 2026-07-29T03:07:37.505378+00:00
content_hash: "f0b0f70ff8bc1237e618d8784009c8e21fe55fe12701b16b2619cb3c6b60e039"
lang: en
caption_quality: None
raw: true
topics: []
---

# Discovering cryptographic weaknesses with Claude

Discovering cryptographic weaknesses with Claude 
The best part of this article (here's the repo ) about how Anthropic researchers used Claude Mythos to find mathematical flaws in both HAWK and a weaker version of AES ("neither of these results has a practical impact on today’s computer systems") is the prompts that they shared, spelling mistakes included: 
 
 the models tend to think it is impossible to solve so they don't try they need a good amount of prompting. 
 why not do aes-128 r7? the whole point is to find something better than existing approaches. 
 no again the goal is that we have highly inteligent model as good top researcher, we want to find new attacks 
 no we don't want to change the targets [...] agian we need to find something that worth publishing 
 again we are not looking for low hanging fruit, we want proper research to find genuinly hard findings. 
 
 Mythos Preview worked for 60 hours in total (~$100,000 in estimated API cost) and the main human interventions were to encourage it not to give up and "find something that worth publishing". 
 The paper CryptanalysisBench: Can LLMs do Cryptanalysis? describes the new eval that was created as part of this work, in partnership with ETH Zurich, Tel Aviv University, and University of Haifa.

 Via Hacker News 

 Tags: ai , prompt-engineering , generative-ai , llms , anthropic , claude , ai-security-research , claude-mythos-fable