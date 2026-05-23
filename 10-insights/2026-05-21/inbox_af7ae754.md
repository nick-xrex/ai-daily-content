---
id: inbox_af7ae754
date: 2026-05-21
source_ref: "[[00-inbox/2026-05-21/1801-hackernews-show-hn-freenet-a-peer-to-peer-platform-2bb1]]"
title: "Show HN: Freenet, a peer-to-peer platform for decentralized apps"
url: https://freenet.org/
source: hackernews
published_at: 2026-05-21T14:34:57+00:00
fetched_at: 2026-05-22T18:19:55.614217+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "無法處理。內容為去中心化 P2P 平台 Freenet 重新設計的技術公告（WebAssembly contracts、commutative merge 機制），與 AI 產業無關，屬於區塊鏈/分散式系統領域。"
key_points:
tags: []
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Freenet, a peer-to-peer platform for decentralized apps

無法處理。內容為去中心化 P2P 平台 Freenet 重新設計的技術公告（WebAssembly contracts、commutative merge 機制），與 AI 產業無關，屬於區塊鏈/分散式系統領域。

### 重點

**原文：** [hackernews](https://freenet.org/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

For the past 5 years or so I&#x27;ve been working on a ground-up redesign of Freenet, my peer-to-peer project from the early 2000s (now renamed Hyphanet). The new Freenet has been up and running since December along with some early applications like River[1], our decentralized group chat and Delta - a decentralized CMS. Users have already started to build their own apps on Freenet including games, and we have some interesting apps in development like Atlas, a search&#x2F;recommendation engine. Architecturally, this new Freenet is a global, decentralized key-value store where keys are webassembly contracts which define what values (aka &quot;state&quot;) are valid for that key, how or when the values can be mutated, and how the state can be efficiently synchronized between peers. We&#x27;ve developed a unique (AFAIK) solution to the consistency problem, every contract must define a &quot;merge&quot; operation for the contract&#x27;s associated state. This operation must be commutative, meaning that you can merge multiple states in any order and you&#x27;ll get the same end result. This approach allows state updates to spread through the network like a virus[2], which typically achieves consistent global state in a few seconds or less. Like the world wide web, Freenet applications can be downloaded from the network itself and run in a web browser - similar to single-page apps on the normal web. However, rather than connecting back to an API running in a datacenter, the webapp connects locally to the Freenet peer and interacts with Freenet contracts and delegates over a local websocket connection. If you&#x27;d like to try Freenet we have convenient installers for the major desktop OSs but not yet mobile, and you can be chatting with other users on River within seconds[3]. Happy to answer any questions, you&#x27;re also welcome to read our FAQ[4], or watch a talk I gave back in March[5]. [1] https:&#x2F;&#x2F;github.com&#x2F;freenet&#x2F;river [2] https:&#x2F;&#x2F;freenet.org&#x2F;about&#x2F;news&#x2F;summary-delta-sync&#x2F; [3] https:&#x2F;&#x2F;freenet.org&#x2F;quickstart&#x2F; [4] https:&#x2F;&#x2F;freenet.org&#x2F;faq&#x2F; [5] https:&#x2F;&#x2F;youtu.be&#x2F;3SxNBz1VTE0

</details>