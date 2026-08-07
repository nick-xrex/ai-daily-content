---
id: inbox_04a2cfaa
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/08/pod-deployment-unit-ai-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Mark Silvester"
published_at: 2026-08-06T06:00:00+00:00
fetched_at: 2026-08-06T22:53:38.456839+00:00
content_hash: "00e67615ae1d8ffd8d126c076c2a880f15eed3a2ddf789ddca068c930f7249a9"
lang: en
caption_quality: None
raw: true
topics: []
---

# Pods as Workers, Not Agents: Rethinking the Deployment Unit for AI Agents on Kubernetes

Running AI agents on Kubernetes raises a key question: should each agent get its own Pod? The kagent project argues no—agents are bursty, short-lived, can spawn subagents, and may wait for human approval, making one Pod per agent wasteful. Agent-substrate adds a control plane to schedule logical “Actors” onto long-lived worker Pods. By Mark Silvester