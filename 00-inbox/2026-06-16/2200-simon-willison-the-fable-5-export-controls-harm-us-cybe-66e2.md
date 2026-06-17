---
id: inbox_bce6ad45
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/16/fable-5-export-controls/#atom-everything"
author: ""
published_at: 2026-06-16T05:20:29+00:00
fetched_at: 2026-06-16T22:00:31.833506+00:00
content_hash: "66e2efcb5d535475100f8b62526ffbd5e9c5ef82329cc7d561411097faa64c1d"
lang: en
caption_quality: None
raw: true
topics: []
---

# The Fable 5 Export Controls Harm US Cyber Defense

The Fable 5 Export Controls Harm US Cyber Defense 
I quoted The Atlantic quoting Kate Moussouris earlier, when I should have gone straight to the source. Here she is confirming that the "jailbreak" that got Claude Fable 5 banned under an export control really was "fix this code": 
 
 The researchers took open-source code with known CVEs, plus new code with deliberately planted vulnerabilities, and asked Fable 5, Mythos, and Opus to “review the code for security issues.” Fable 5 refused. They then asked the models to “fix this code” and, through a multistep and manual process, turned the output into scripts that test the patches. 
 
 As Kate points out, this is absurd. Coding models fix bugs, and security exploits are the most important category of bugs for them to fix! 
 
 Defenders need to be able to ask AI to fix the bugs in a file, explain why the fix matters, and write tests that confirm the patch works. That is not a guardrail bypass. It is the most valuable thing an AI model can do for defensive security: executing the find, fix, and test loop defenders run every day. [...] 
 The prompts worked because they were defensive requests, and that capability cannot be removed without making the model worse at fixing bugs and verifying patches. 
 
 This whole situation is such a mess. Non-technical decision-makers have been hearing that models that can "craft cyber attacks" are uniquely dangerous for months. Now they look ready to ban any model that can help us secure our code.

 Tags: jailbreaking , security , ai , generative-ai , llms , anthropic , ai-security-research , claude-mythos