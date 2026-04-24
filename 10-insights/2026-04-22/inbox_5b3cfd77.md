---
id: inbox_5b3cfd77
date: 2026-04-22
source_ref: "[[00-inbox/2026-04-22/0246-infoq-architecture-dropbox-collaborates-with-github-to-redu-1e4b]]"
title: "Dropbox Collaborates with GitHub to Reduce Monorepo Size from 87GB to 20GB"
url: https://www.infoq.com/news/2026/04/dropbox-reduces-git-optimization/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-04-22T14:14:00+00:00
fetched_at: 2026-04-24T03:01:00.185238+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Dropbox 與 GitHub 合作優化其後端 monorepo，利用改進的 Git delta 壓縮將存儲空間從 87GB 減至 20GB，降幅達 77%。這項優化直接改善了倉庫克隆時間、CI 管道性能以及開發者開發速度。該案例展示了存儲效率對大規模 monorepo 工作流的實質影響，亦反映了版本控制工具的最佳化仍有重大空間。"
key_points:
  - "Git delta 壓縮優化：87GB → 20GB（節省 67GB）"
  - "改善克隆時間、CI 性能、開發速度等多個工程指標"
  - "大規模 monorepo 的存儲效率是隱形的工程債務"
tags: [git-optimization, monorepo, compression, developer-velocity, infrastructure]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Dropbox Collaborates with GitHub to Reduce Monorepo Size from 87GB to 20GB

Dropbox 與 GitHub 合作優化其後端 monorepo，利用改進的 Git delta 壓縮將存儲空間從 87GB 減至 20GB，降幅達 77%。這項優化直接改善了倉庫克隆時間、CI 管道性能以及開發者開發速度。該案例展示了存儲效率對大規模 monorepo 工作流的實質影響，亦反映了版本控制工具的最佳化仍有重大空間。

### 重點
- Git delta 壓縮優化：87GB → 20GB（節省 67GB）
- 改善克隆時間、CI 性能、開發速度等多個工程指標
- 大規模 monorepo 的存儲效率是隱形的工程債務

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/04/dropbox-reduces-git-optimization/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://www.infoq.com/styles/static/images/logo/logo_bigger.jpg" /><p>Dropbox reduced its backend monorepo from 87GB to 20GB by optimizing Git delta compression in collaboration with GitHub. The changes improved clone times, CI performance, and developer velocity, highlighting how repository storage inefficiencies can impact large-scale engineering workflows.</p> <i>By Leela Kumili</i>

</details>