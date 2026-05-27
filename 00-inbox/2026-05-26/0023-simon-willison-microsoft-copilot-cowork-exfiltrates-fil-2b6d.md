---
id: inbox_0f65b03c
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/26/copilot-cowork-exfiltrates-files/#atom-everything"
author: ""
published_at: 2026-05-26T15:36:48+00:00
fetched_at: 2026-05-27T00:23:11.940936+00:00
content_hash: "2b6d1ffa53e810043705d183349cbf8b60944e47f00f75b6737526c667524789"
lang: en
caption_quality: None
raw: true
topics: []
---

# Microsoft Copilot Cowork Exfiltrates Files

Microsoft Copilot Cowork Exfiltrates Files 
The biggest challenge in designing agentic systems continues to be preventing them from enabling attackers to exfiltrate data. 
 In this case Microsoft Copilot Cowork (yes, that's a real product name ) was allowing agents to send emails to the user's own inbox without approval... but those messages were then displayed in a way that could leak data to an attacker via rendered images: 
 
 Because these messages can contain external images that trigger network requests to external websites, data can be exfiltrated when a user opens a compromised message sent by the agent. 
 
 Since OneDrive can create pre-authenticated download links, a successful prompt injection could cause those links to be leaked, allowing files to be downloaded by the attacker.

 Via Hacker News 

 Tags: microsoft , security , ai , prompt-injection , generative-ai , llms , exfiltration-attacks , lethal-trifecta