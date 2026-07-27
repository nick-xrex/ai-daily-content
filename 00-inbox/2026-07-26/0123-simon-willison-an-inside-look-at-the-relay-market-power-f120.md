---
id: inbox_a0de380c
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/26/relay-market/#atom-everything"
author: ""
published_at: 2026-07-26T19:30:54+00:00
fetched_at: 2026-07-27T01:23:10.549720+00:00
content_hash: "f12012fa52939d62b024b4db1773a8e464778c8e27b5e01e97ae27dc0f2655d0"
lang: en
caption_quality: None
raw: true
topics: []
---

# An Inside Look at the Relay Market Powering Token Resellers and Fraud

An Inside Look at the Relay Market Powering Token Resellers and Fraud 
Fascinating investigation by Matt Lenhard into the market that has grown up around reselling LLM tokens at a discount by pooling API keys from various sources. 
 This looks to be mostly a thing in China. Resellers sell access to an LLM proxy that offers significant discounts on regular API pricing, which they achieve by abusing free trials, proxying through unprotected support bots, or sometimes through stolen credit cards or chargeback attacks. 
 The software they are using for these proxies is open source - mostly one-api and its more actively developed fork new-api , both legitimate API proxy products which can be used to load. balance requests across a pool of API credentials. 
 The buyers are seeking cheap tokens, avoiding geo-restrictions, and in some cases collecting data for model distillation. 
 I've been cautious about exposing my own LLM-driven applications publicly out of fear of abuse leading to big token bills. The existence of this marketplace makes me even more cautious: there's now an entire ecosystem that can profit from finding a new unprotected endpoint to exploit. 
 LLM vendors really need to get better at offering strict caps for their API keys. I want my LLM apps to stop working the moment they hit a dollar threshold I've set for a period of time. 
 Here's the (Chinese language) forum thread that served as the principal source for Matt's article.

 Via Hacker News 

 Tags: ai , generative-ai , llms , llm-pricing , ai-ethics , ai-in-china