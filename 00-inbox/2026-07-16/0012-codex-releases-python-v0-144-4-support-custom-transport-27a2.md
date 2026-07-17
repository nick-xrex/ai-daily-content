---
id: inbox_1ed5f260
source: codex-releases
source_type: rss
url: "https://github.com/openai/codex/releases/tag/python-v0.144.4"
author: "celia-oai"
published_at: 2026-07-16T21:41:00+00:00
fetched_at: 2026-07-17T00:12:05.699787+00:00
content_hash: "27a26df33394d2f5d217d06c989ad58a553404e9dd98462a05af44b788bdcd47"
lang: en
caption_quality: None
raw: true
topics: []
---

# python-v0.144.4: Support custom transports for Amazon Bedrock (#33695)

What changed 
 
 Allow the built-in amazon-bedrock provider to override base_url , auth , 
and http_headers in addition to its AWS profile and region. 
 Use command-based bearer authentication and configured endpoints without 
applying AWS request signing, while retaining regional endpoint resolution 
for the default Bedrock configuration. 
 Replace the Bedrock account credentialSource enum with the 
 usesCodexManagedCredentials boolean so command-authenticated and other 
externally managed configurations are reported consistently. 
 
 Testing 
 
 Cover configuration merging and validation, command-authenticated proxy 
requests with custom headers, and account reporting for managed and external 
credentials. 
 
 GitOrigin-RevId: d1acbe602060470583b5e12f8d304bee5be46f4c