---
id: inbox_285df0b7
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/2/microsofts-new-models/#atom-everything"
author: ""
published_at: 2026-06-02T22:21:52+00:00
fetched_at: 2026-06-03T00:30:09.326197+00:00
content_hash: "b511444522841fdd492bc99b0f6ced8d4ed7f1f5749bf57e710c7767692836bd"
lang: en
caption_quality: None
raw: true
topics: []
---

# Microsoft's new MAI models

Microsoft announced two new text LLMs this morning - MAI-Thinking-1 (reasoning, 35B parameters, available to "select early partners") and MAI-Code-1-Flash (5B parameters, "purpose-built for GitHub Copilot and VS Code to deliver high performance and lower cost [...] rolling out to GitHub Copilot individual users in Visual Studio Code"). I've not been able to try either of them just yet. 
 It's very interesting to see Microsoft releasing models with such low parameter counts, especially given how expensive larger models are to access right now. They claim MAI-Thinking-1 "is preferred to Sonnet 4.6 in our blind human side-by-side evaluations", which is impressive for a 35B model seeing as I frequently run models larger than that on my own laptop. 
 Also of note : 
 
 We trained [MAI-Thinking-1] from the ground up on enterprise grade, clean and commercially licensed data, without distillation from third-party models. 
 
 And for MAI-Code-1-Flash as well: 
 
 It is built end-to-end by Microsoft using clean and appropriately licensed data. 
 
 I would very much like to learn more about this "appropriately licensed" data! Could these be the first generally useful code-specialist models that didn't train on an unlicensed dump of the web? 

 Tags: llm-release , generative-ai , ai , microsoft , llms