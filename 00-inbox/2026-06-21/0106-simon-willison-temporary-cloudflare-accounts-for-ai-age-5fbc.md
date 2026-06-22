---
id: inbox_4a213d37
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/21/temporary-cloudflare-accounts/#atom-everything"
author: ""
published_at: 2026-06-21T22:01:04+00:00
fetched_at: 2026-06-22T01:06:41.538553+00:00
content_hash: "5fbc4d26d71911a06bd1d8136dd3adbbaf7dbcb5e27f30862b2e2843fa8db292"
lang: en
caption_quality: None
raw: true
topics: []
---

# Temporary Cloudflare Accounts for AI agents

Temporary Cloudflare Accounts for AI agents 
The announcement says this is "for AI agents" but (as is pretty common these days) the AI hook isn't really necessary, this is an interesting feature for everyone else as well. 
 Short version: you can now create a Cloudflare Workers project and run this, without even creating a Cloudflare account: 
 npx wrangler deploy --temporary
 
 Cloudflare will deploy the application to a new, ephemeral project which will stay live for 60 minutes. 
 I had GPT-5.5 xhigh in Codex Desktop build this test application providing a tool for following HTTP redirects and returning the final destination. The temporary deployment worked as advertised. 
 Running the deployment spits out the URL to a page for claiming the new project, for if you want it to last for more than 60 minutes. Here's what that claim screen looks like: 
 

 Via Hacker News 

 Tags: cloudflare