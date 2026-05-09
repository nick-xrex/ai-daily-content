---
id: inbox_f7cee1c6
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0151-medium-stackademic-why-your-apis-feel-slow-even-when-they-a-669b]]"
title: "Why Your APIs Feel Slow (Even When They Aren’t)"
url: https://blog.stackademic.com/why-your-apis-feel-slow-even-when-they-arent-b7762e08ce23?source=rss----d1baaa8417a4---4
source: medium-stackademic
published_at: 2026-05-08T09:09:33+00:00
fetched_at: 2026-05-09T02:07:45.151172+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章分析 API 雖然後端快但仍感覺慢的根本原因。網路延遲、Payload 大小、多個序列化往返、前端渲染、缺乏並行執行等多重因素造成累加延遲。核心洞察：API 性能不只是執行時間，還包括網路行為、資料傳輸和請求結構；使用者體驗的延遲與伺服器測量的執行時間存在本質差異。返回不必要資料會增加網路傳輸時間，序列化成本在大 Payload 或高頻率呼叫時尤其明顯。"
key_points:
  - "網路延遲固有存在（往返時間、多重路由）即使後端高效，遠距離或不穩定網路上更明顯"
  - "Payload 大小直接影響傳輸和客戶端處理；序列化/反序列化成本在大資料量時成倍增長"
  - "多個 API 呼叫的延遲累加與序列化開銷；並行執行可顯著減少總等待時間"
tags: [api-performance, latency, network-behavior, payload-optimization, client-rendering]
topics: []
importance: 3
novelty: 1
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Why Your APIs Feel Slow (Even When They Aren’t)

文章分析 API 雖然後端快但仍感覺慢的根本原因。網路延遲、Payload 大小、多個序列化往返、前端渲染、缺乏並行執行等多重因素造成累加延遲。核心洞察：API 性能不只是執行時間，還包括網路行為、資料傳輸和請求結構；使用者體驗的延遲與伺服器測量的執行時間存在本質差異。返回不必要資料會增加網路傳輸時間，序列化成本在大 Payload 或高頻率呼叫時尤其明顯。

### 重點
- 網路延遲固有存在（往返時間、多重路由）即使後端高效，遠距離或不穩定網路上更明顯
- Payload 大小直接影響傳輸和客戶端處理；序列化/反序列化成本在大資料量時成倍增長
- 多個 API 呼叫的延遲累加與序列化開銷；並行執行可顯著減少總等待時間

**原文：** [medium-stackademic](https://blog.stackademic.com/why-your-apis-feel-slow-even-when-they-arent-b7762e08ce23?source=rss----d1baaa8417a4---4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Understanding the gap between actual performance and perceived latency In previous parts , we explored how backend systems behave under load and how design decisions impact performance. However, not all performance issues come from slow systems. In many cases, the backend is fast, but the API still feels slow. This difference comes from how latency is experienced, not just how it is measured. API performance is not only about execution time. It is also about network behavior, data transfer, and how requests are structured. Why Your APIs Feel Slow (Even When They Aren’t) Network latency matters Every API call travels over a network. Even if the backend processes a request quickly, the total time includes: travel time from client to server routing through multiple network hops return time for the response This delay exists even when the backend is efficient. For users located far from the server, or on unstable networks, this latency becomes noticeable. As a result, a fast backend can still feel slow due to network distance and conditions. Payload size issues The size of the response directly affects how long it takes to deliver. Larger payloads require more time to: transfer over the network process on the client side Even small increases in payload size can add noticeable delay, especially on slower connections. Returning more data than necessary increases latency without improving functionality. Efficient APIs focus on sending only what is required. Too many API calls Frontend applications often depend on multiple API calls. Instead of one request, the system may perform several smaller requests to gather data. For example: one call for user data another for related items another for additional details Even if each call is fast, the total time adds up. Sequential calls increase delay further, as each request waits for the previous one. This creates the perception of a slow system, even when individual endpoints are efficient. Serialization and deserialization cost Data needs to be converted before it is sent and after it is received. On the server: objects are serialized into formats like JSON On the client: responses are parsed back into usable data This process takes time. While the cost is small per request, it becomes noticeable with large payloads or frequent calls. It adds hidden overhead that is often ignored during performance evaluation. Frontend rendering delays API performance is often judged by how quickly users see results. Even after the response arrives: data must be processed UI must be updated components must render These steps add delay beyond the API response time. From the user’s perspective, the system feels slow, even if the backend responded quickly. Lack of parallelism in requests When API calls are made sequentially, total latency increases. Each request waits for the previous one to complete. If multiple independent requests are needed, this approach wastes time. Parallel execution can reduce total wait time, but it is not always implemented. This leads to unnecessary delays in response delivery. Conclusion API performance is not only about backend speed. It is influenced by network latency, payload size, request patterns, and client-side processing. A system can be technically fast but still feel slow to users. Understanding this difference helps in designing APIs that are efficient not only in execution, but also in experience. In the next part, we will explore load testing and why many systems fail to identify performance limits early. Thanks for reading. Why Your APIs Feel Slow (Even When They Aren’t) was originally published in Stackademic on Medium, where people are continuing the conversation by highlighting and responding to this story.

</details>