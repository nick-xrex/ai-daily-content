---
id: inbox_1ce6ada6
source: infoq-ai-ml
source_type: rss
url: "https://www.infoq.com/news/2026/08/pod-deployment-unit-ai-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering"
author: "Mark Silvester"
published_at: 2026-08-06T06:00:00+00:00
fetched_at: 2026-08-06T22:53:37.002801+00:00
content_hash: "983203f0e8a3287caad110449eb46843f4d9ec7b407a322332dccc9bf5d26056"
lang: en
caption_quality: None
raw: true
topics: []
---

# Pods as Workers, Not Agents: Rethinking the Deployment Unit for AI Agents on Kubernetes

Running AI agents on Kubernetes raises a key question: should each agent get its own Pod? The kagent project argues no—agents are bursty, short-lived, can spawn subagents, and may wait for human approval, making one Pod per agent wasteful. Agent-substrate adds a control plane to schedule logical “Actors” onto long-lived worker Pods. By Mark Silvester