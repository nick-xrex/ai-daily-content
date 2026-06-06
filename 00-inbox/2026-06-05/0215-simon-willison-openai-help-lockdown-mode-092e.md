---
id: inbox_3c5c08e8
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/5/openai-help-lockdown-mode/#atom-everything"
author: ""
published_at: 2026-06-05T23:56:40+00:00
fetched_at: 2026-06-06T02:15:58.141315+00:00
content_hash: "092ebe26b046b2f7625ac820793da26f2e069449732eb49cf1272f91ed30e23b"
lang: en
caption_quality: None
raw: true
topics: []
---

# OpenAI Help: Lockdown Mode

OpenAI Help: Lockdown Mode 
OpenAI first teased this in February , but now it's live and "rolling out to eligible personal accounts, including Free, Go, Plus, and Pro, and self-serve ChatGPT Business accounts": 
 
 Lockdown Mode is designed to help prevent the final stage of data exfiltration from a prompt injection attack by limiting outbound network requests that could transfer sensitive data to an attacker. Lockdown Mode does not prevent prompt injections from appearing in the content ChatGPT processes. For example, a prompt injection could appear in cached web content or in an uploaded file, and could still affect the behavior or accuracy of a response. 
 
 This looks really good to me. 
 The Lethal Trifecta occurs when an LLM system has access to all three of access to private data, exposure to untrusted content and a way to steal data and transmit it back to the attacker. 
 The only way to solve the trifecta is to cut off one of the three legs, and by far the easiest leg to restrict without making your LLM systems far less useful is the exfiltration vectors to steal data. 
 It looks to me like lockdown mode directly attacks that leg, using mechanisms that are deterministic and, crucially, are not evaluated by AI systems that themselves can be subverted by sufficiently devious attacks. 
 The existence of lockdown mode does however imply that ChatGPT, in its default settings, does not provide robust protection against sufficiently determined data exfiltration attacks!

 Tags: security , ai , openai , prompt-injection , llms , lethal-trifecta