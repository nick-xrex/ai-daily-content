---
id: inbox_6b3ae383
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Aug/5/third-party-cyber-evaluations/#atom-everything"
author: ""
published_at: 2026-08-05T23:45:32+00:00
fetched_at: 2026-08-06T00:02:40.497156+00:00
content_hash: "93111751c8a3451b1de719f78bbfb5874d994c76693a745fa8acbd738021528a"
lang: en
caption_quality: None
raw: true
topics: []
---

# Third-party cyber evaluations involving OpenAI models

Third-party cyber evaluations involving OpenAI models 
And another one . I had to create a accidental-cyberattacks tag to keep track of them all! 
 This post from OpenAI covers both the UK AI Safety Institute attack (see my previous post ) and another attack enabled by Irregular : 
 
 Irregular, one of our external cybersecurity testing partners, was running Capture-the-Flag-style evaluations intended to be isolated from the internet, but a testing-environment misconfiguration allowed models to access the public internet. [...] 
 In one test, the name of the fictional target for the CTF challenge unintentionally coincided with a real domain. Because the testing environment was mistakenly connected to the internet, the model exploited a real website, mistaking it to be part of the simulated environment. 
 
 Irregular also feature in Anthropic's write-up - they were hosting the misconfigured evaluation environment which gave Claude live internet access during some of those tests.

 Tags: security , ai , openai , llms , accidental-cyberattacks