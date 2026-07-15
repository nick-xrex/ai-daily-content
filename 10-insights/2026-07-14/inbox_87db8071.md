---
id: inbox_87db8071
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-simon-willison-quoting-armin-ronacher-785c]]"
title: "Quoting Armin Ronacher"
url: https://simonwillison.net/2026/Jul/14/armin-ronacher/#atom-everything
source: simon-willison
published_at: 2026-07-14T18:04:23+00:00
fetched_at: 2026-07-14T22:11:41.439924+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Armin Ronacher 在《The Tower Keeps Rising》文章中深入討論 AI agents 對軟體工程文化的潛在影響。他指出軟體專案真正的共同語言並非英語或程式語言本身，而是團隊對概念邊界、系統不變式、所有權和架構決策的隱性共同理解，這種理解往往通過代碼審查、團隊討論與變更協調的過程口頭傳承。他認為 AI agents 時代可能削弱此前維持這種同步的「摩擦」，但他提出關鍵洞察：這種摩擦並非純粹浪費，其中部分恰恰是讓不同視角相互貫通、確保系統設計共識的必要成本。"
key_points:
  - "軟體專案的真正共同語言存於文檔、代碼、審查與對話中，是對概念、邊界、所有權的隱性共識而非顯性規範"
  - "前 agent 時代的變更協調成本中包含浪費，但也包含同步團隊認識、驗證系統理解一致性的價值"
  - "Agent 時代風險：自動化降低溝通成本可能導致團隊對系統設計原則、決策依據的理解碎片化與喪失"
tags: [ai-agents, software-engineering, team-dynamics, agentic-era]
topics: []
importance: 3
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Quoting Armin Ronacher

Armin Ronacher 在《The Tower Keeps Rising》文章中深入討論 AI agents 對軟體工程文化的潛在影響。他指出軟體專案真正的共同語言並非英語或程式語言本身，而是團隊對概念邊界、系統不變式、所有權和架構決策的隱性共同理解，這種理解往往通過代碼審查、團隊討論與變更協調的過程口頭傳承。他認為 AI agents 時代可能削弱此前維持這種同步的「摩擦」，但他提出關鍵洞察：這種摩擦並非純粹浪費，其中部分恰恰是讓不同視角相互貫通、確保系統設計共識的必要成本。

### 重點
- 軟體專案的真正共同語言存於文檔、代碼、審查與對話中，是對概念、邊界、所有權的隱性共識而非顯性規範
- 前 agent 時代的變更協調成本中包含浪費，但也包含同步團隊認識、驗證系統理解一致性的價值
- Agent 時代風險：自動化降低溝通成本可能導致團隊對系統設計原則、決策依據的理解碎片化與喪失

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/14/armin-ronacher/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The shared language of a software project is not English or Python but it is the common understanding of what its concepts mean, where the boundaries are, which invariants matter, who owns what, and why the system has the shape it does. This language is rarely written down in one place. It lives partly in documentation and code, but also in code review, conversations, arguments, and the experience of having to explain a change to somebody else. 
 Before agents, some of this shared understanding was maintained by friction. If I wanted to change your storage layer, I usually had to read your code, ask you questions, and perhaps coordinate with another team whose service depended on it. This was slow, and much of that slowness was waste but not all of it was. Some of it was the process by which your understanding became mine, and by which both of us discovered whether we still agreed about how the system worked. This friction synchronizes people. 
 &mdash; Armin Ronacher , The Tower Keeps Rising 

 Tags: ai , software-engineering , llms , coding-agents , ai-assisted-programming , generative-ai , armin-ronacher , agentic-engineering

</details>