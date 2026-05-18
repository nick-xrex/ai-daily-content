---
id: inbox_8ecf74df
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_8ecf74df]]"
title: "Pinterest Engineers Eliminate CPU Zombies to Resolve Production Bottlenecks"
url: https://www.infoq.com/news/2026/05/pinterest-cpu-zombies-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-14T10:00:00+00:00
fetched_at: 2026-05-18T03:32:32.223986+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Pinterest 在 Kubernetes 基礎設施 PinCompute 上遭遇 CPU 飢餓（CPU starvation），影響機器學習訓練任務效能。故障排查後發現根本原因：一個已棄用但未禁用的 Amazon ECS agent 造成 memory cgroup 洩漏，導致記憶體隔離失效。禁用該 agent 後，系統性能立即穩定，ML 訓練恢復正常。案例強調系統預設行為（system defaults）的隱蔽威力：即使未主動使用的元件仍會消耗資源。對 Kubernetes 運維者而言，cgroup 隔離與廢棄元件的週期性稽查為關鍵。"
key_points:
  - "根本原因：閒置 Amazon ECS agent → memory cgroup 洩漏 → CPU contention"
  - "解決方案：禁用不必要的 agent，恢復 ML 訓練效能"
  - "教訓：系統預設值需主動稽查，特別是已棄用、未刪除的元件"
tags: [kubernetes, performance, memory-cgroup, troubleshooting, ml-infra]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Pinterest Engineers Eliminate CPU Zombies to Resolve Production Bottlenecks

Pinterest 在 Kubernetes 基礎設施 PinCompute 上遭遇 CPU 飢餓（CPU starvation），影響機器學習訓練任務效能。故障排查後發現根本原因：一個已棄用但未禁用的 Amazon ECS agent 造成 memory cgroup 洩漏，導致記憶體隔離失效。禁用該 agent 後，系統性能立即穩定，ML 訓練恢復正常。案例強調系統預設行為（system defaults）的隱蔽威力：即使未主動使用的元件仍會消耗資源。對 Kubernetes 運維者而言，cgroup 隔離與廢棄元件的週期性稽查為關鍵。

### 重點
- 根本原因：閒置 Amazon ECS agent → memory cgroup 洩漏 → CPU contention
- 解決方案：禁用不必要的 agent，恢復 ML 訓練效能
- 教訓：系統預設值需主動稽查，特別是已棄用、未刪除的元件

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/pinterest-cpu-zombies-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Pinterest Engineers Eliminate CPU Zombies to Resolve Production Bottlenecks

Pinterest identified and resolved CPU starvation issues that affected machine learning training jobs on its Kubernetes-based platform, PinCompute. The engineers traced the problem to an unused Amazon ECS agent, which caused memory cgroup leaks. By disabling the agent, they stabilised performance. This case illustrates the importance of understanding system defaults for effective troubleshooting. By Mark Silvester

</details>