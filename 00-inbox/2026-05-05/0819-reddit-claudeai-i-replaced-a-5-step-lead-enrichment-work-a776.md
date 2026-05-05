---
id: inbox_70bb62b8
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t47h53/i_replaced_a_5step_lead_enrichment_workflow_with/"
author: "/u/lemnistatic"
published_at: 2026-05-05T06:37:01+00:00
fetched_at: 2026-05-05T08:19:22.499941+00:00
content_hash: "a776d45f1f695e1d1f2699ed453c1ae478fbc48a70b0928b9beb30f45f57ccb3"
lang: en
caption_quality: None
raw: true
topics: []
---

# I replaced a 5-step lead enrichment workflow with Claude custom skills

<!-- SC_OFF --><div class="md"><p>Sharing this because i know a lot of people here are doing what i did.</p> <p>My old workflow was a long process. Build a list in Apollo, enrich through PDL (maybe 50-60% usable, rest is outdated or wrong), take the gaps and pass to a second provider, verify emails separately because enrichment data bounces 15-20% of the time, then manually load everything into HubSpot because none of these tools talk to each other cleanly. 5 steps, 3 vendors, took over an hour and the output was still mediocre.</p> <p>So i built a Claude workflow using MCPs that handles all of this in one pass.</p> <p>Tech stack (all connected as MCPs):</p> <p>Crustdata - people and company data. This replaced Apollo and PDL for me. The data is pulled in realtime so you're not getting outdated job titles. Search filters are granular enough that Claude can find the exact ICP match without me manually cleaning the list after. It also returns social media posts from prospects which I use for personalization.</p> <p>FullEnrich MCP - email waterfall and verification in one step. This replaced the separate enrichment + verification tools I was paying for. They run through 20+ providers so match rates are solid.</p> <p>HubSpot MCP - Claude pushes the final enriched list directly into the CRM. No more manual CSV imports.</p> <p>Example prompt I run: &quot;Find B2B SaaS companies in the US with 50-200 employees that raised Series A or B in the last 9 months and are hiring for sales roles. Find the VP Sales or Head of Growth at each. Get verified emails. Pull their recent social media posts and research their website. Score each prospect against our ICP and rank by fit.&quot;</p> <p>Claude builds the list, enriches everything, verifies emails, scores against my ICP criteria and pushes to HubSpot. Takes about 5 minutes for a list that used to take me over an hour manually across multiple tools.</p> <p>The list quality is also way better. When Claude reads someone's full profile and matches against your ICP instead of relying on keyword filters, you stop getting garbage matches. I wrote a skill describing our ICP in detail so it scores consistently across searches.</p> <p>I still review every list before anything goes out. But the data collection, enrichment and scoring part is basically handled. Happy to answer questions if anyone wants to set up something similar.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/lemnistatic"> /u/lemnistatic </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t47h53/i_replaced_a_5step_lead_enrichment_workflow_with/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t47h53/i_replaced_a_5step_lead_enrichment_workflow_with/">[comments]</a></span>