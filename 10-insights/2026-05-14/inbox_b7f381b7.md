---
id: inbox_b7f381b7
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_b7f381b7]]"
title: "Pinterest Engineers Eliminate CPU Zombies to Resolve Production Bottlenecks"
url: https://www.infoq.com/news/2026/05/pinterest-cpu-zombies-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-05-14T10:00:00+00:00
fetched_at: 2026-05-18T03:35:44.378204+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Pinterest 在 Kubernetes 平台 PinCompute 上解決 ML 訓練性能瓶頸。根本原因是未使用的 Amazon ECS agent 導致 memory cgroup 洩漏造成 CPU 飢餓。禁用該 agent 恢復系統穩定性。案例強調對系統默認設置理解對故障排查的關鍵作用，特別是複雜基礎設施環境。"
key_points:
  - "Pinterest PinCompute 的 CPU 飢餓由 ECS agent 導致的 memory cgroup leak 引起"
  - "禁用未使用的 agent 解決性能問題，恢復 ML 訓練穩定性"
  - "系統默認設置可能引發隱藏性能問題，需要系統化調試"
tags: [kubernetes, cpu-starvation, debugging, memory-leak, pincompute]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Pinterest Engineers Eliminate CPU Zombies to Resolve Production Bottlenecks

Pinterest 在 Kubernetes 平台 PinCompute 上解決 ML 訓練性能瓶頸。根本原因是未使用的 Amazon ECS agent 導致 memory cgroup 洩漏造成 CPU 飢餓。禁用該 agent 恢復系統穩定性。案例強調對系統默認設置理解對故障排查的關鍵作用，特別是複雜基礎設施環境。

### 重點
- Pinterest PinCompute 的 CPU 飢餓由 ECS agent 導致的 memory cgroup leak 引起
- 禁用未使用的 agent 解決性能問題，恢復 ML 訓練穩定性
- 系統默認設置可能引發隱藏性能問題，需要系統化調試

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/05/pinterest-cpu-zombies-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Pinterest Engineers Eliminate CPU Zombies to Resolve Production Bottlenecks

Pinterest identified and resolved CPU starvation issues that affected machine learning training jobs on its Kubernetes-based platform, PinCompute. The engineers traced the problem to an unused Amazon ECS agent, which caused memory cgroup leaks. By disabling the agent, they stabilised performance. This case illustrates the importance of understanding system defaults for effective troubleshooting. By Mark Silvester

</details>