---
id: inbox_6aab94c7
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/29/ai-worming-through-word/#atom-everything"
author: ""
published_at: 2026-07-29T18:43:03+00:00
fetched_at: 2026-07-29T23:36:31.175194+00:00
content_hash: "ff5f10b31607b8855ae4fee290028be2fe36017bf07f014f5dde74ffb72b426a"
lang: en
caption_quality: None
raw: true
topics: []
---

# AI Worming through Word

AI Worming through Word 
Neat new prompt injection variant by Håkon Måløy, who found a way to upgrade prompt injection attacks against Microsoft Word to full self-replicating worms: 
 
 An attacker places hidden instructions in a document that is later used as source material in Copilot for Word. Copilot may interpret those instructions as part of the user’s request, causing it to manipulate the document being drafted or edited. Copilot may then also copy the hidden instructions into the resulting document, turning that document into a new carrier. If the carrier is subsequently used in another Copilot-assisted workflow, the instructions can trigger again and propagate into further documents, even without the attacker’s original document being present. 
 
 We've seen plenty of hidden white-on-white text before - the kids are using it in their job applications now - but this is the first one I've seen that deliberately copies instructions to self-replicate itself. 
 It was responsibly disclosed to Microsoft who then had 144 days to work on a fix, but so far (unsurprisingly) there's no mitigation that covers the full class of attack.

 Via Hacker News 

 Tags: microsoft , security , ai , prompt-injection , generative-ai , llms