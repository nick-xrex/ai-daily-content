---
id: inbox_95d6da6b
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/08/pod-deployment-unit-ai-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Mark Silvester"
published_at: 2026-08-06T06:00:00+00:00
fetched_at: 2026-08-06T22:53:34.700933+00:00
content_hash: "f02c3e1da184943da720335b46153ff57340565132ae243be2528ec005833306"
lang: en
caption_quality: None
raw: true
topics: []
---

# Pods as Workers, Not Agents: Rethinking the Deployment Unit for AI Agents on Kubernetes

Running AI agents on Kubernetes raises a key question: should each agent get its own Pod? The kagent project argues no—agents are bursty, short-lived, can spawn subagents, and may wait for human approval, making one Pod per agent wasteful. Agent-substrate adds a control plane to schedule logical “Actors” onto long-lived worker Pods. By Mark Silvester