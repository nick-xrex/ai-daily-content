---
id: inbox_38a7cfbc
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_38a7cfbc]]"
title: "My Spring Boot API Crashed Under 10K Users. Here’s Every Mistake I Made."
url: https://blog.stackademic.com/my-spring-boot-api-crashed-under-10k-users-heres-every-mistake-i-made-25f5a5481136?source=rss----d1baaa8417a4---4
source: medium-stackademic
published_at: 2026-05-04T08:33:26+00:00
fetched_at: 2026-05-04T14:20:54.672898+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Spring Boot API 在 10K 並發用戶時的 4 個生產故障全是可預防的配置與設計問題。(1) 連接池默認僅 10 個連接，應配置為 (核心數×2) + I/O 自旋度；(2) 外部 API 調用無超時導致線程耗盡（例：詐騙檢測 API 延遲 30 秒就阻塞所有請求）；(3) 註冊端同步發郵件阻塞主路徑，改為異步發布事件；(4) 4 小時不變的商品目錄無緩存，每秒查詢 300 次導致 DB CPU 飆至 100%。"
key_points:
  - "HikariCP 連接池配置：최小 (cores × 2) + spindle count，3000ms timeout，默認 10 個是瓶頸"
  - "外部依賴必須設置超時：RestTemplate 需明確 connectTimeout 和 readTimeout，避免一個緩慢服務拖垮整體"
  - "非關鍵路徑操作異步化：郵件、分析事件、審計日誌應發布事件而非同步執行，減少 signup 端點從 3 秒回到 150ms"
tags: [spring-boot, production-reliability, performance-tuning]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## My Spring Boot API Crashed Under 10K Users. Here’s Every Mistake I Made.

Spring Boot API 在 10K 並發用戶時的 4 個生產故障全是可預防的配置與設計問題。(1) 連接池默認僅 10 個連接，應配置為 (核心數×2) + I/O 自旋度；(2) 外部 API 調用無超時導致線程耗盡（例：詐騙檢測 API 延遲 30 秒就阻塞所有請求）；(3) 註冊端同步發郵件阻塞主路徑，改為異步發布事件；(4) 4 小時不變的商品目錄無緩存，每秒查詢 300 次導致 DB CPU 飆至 100%。

### 重點
- HikariCP 連接池配置：최小 (cores × 2) + spindle count，3000ms timeout，默認 10 個是瓶頸
- 外部依賴必須設置超時：RestTemplate 需明確 connectTimeout 和 readTimeout，避免一個緩慢服務拖垮整體
- 非關鍵路徑操作異步化：郵件、分析事件、審計日誌應發布事件而非同步執行，減少 signup 端點從 3 秒回到 150ms

**原文：** [medium-stackademic](https://blog.stackademic.com/my-spring-boot-api-crashed-under-10k-users-heres-every-mistake-i-made-25f5a5481136?source=rss----d1baaa8417a4---4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

-d1baaa8417a4---4"
author: "SYSTEM DESIGN AND PRODUCTION"
published_at: 2026-05-04T08:33:26+00:00
fetched_at: 2026-05-04T13:38:35.906832+00:00
content_hash: "9c7d7e2f25bc4c51656b80d1bab070c43d5218ed44baf8ac33f23584f7beca8c"
lang: en
caption_quality: None
raw: true
topics: []
---

# My Spring Boot API Crashed Under 10K Users. Here’s Every Mistake I Made.

<figure><img alt="" src="https://cdn-images-1.medium.com/max/748/1*LORPBf69IHf6yrptv-bNBQ.png" /></figure><h4>The app worked perfectly in staging. In production, at 10K concurrent users, it fell apart in 4 specific places. Each one was preventable.</h4><p>The launch was supposed to be a good day.</p><p>We’d spent three months building the API. Load tested it. Optimized the slowest endpoints. Fixed the obvious bottlenecks. On the morning of the launch, everything was green.</p><p>By noon, we had 10,000 concurrent users and a completely unresponsive service.</p><p>I spent the next six hours debugging what went wrong. Here’s what I found — and what I’d do differently now.</p><h3>Mistake 1: Default Connection Pool Size</h3><p>The first thing that failed was the database connection pool.</p><p>Spring Boot’s default HikariCP configuration ships with a maximum of 10 connections. Ten. For a service under any meaningful load, that’s not a pool — it’s a bottleneck waiting to happen.</p><p>At 10K concurrent users, each request that touched the database was queuing for a connection. The queue grew. Response times climbed from 200ms to 4 seconds. Then threads started timing out waiting for connections that never came.</p><p>The fix is two lines of configuration:</p><pre>spring:<br />  datasource:<br />    hikari:<br />      maximum-pool-size: 50<br />      connection-timeout: 3000</pre><p>But the right number isn’t 50 for everyone. The formula that actually works: (number of cores × 2) + effective spindle count. For a 4-core instance with SSD storage, that's roughly 9-10 connections. For a service with heavy I/O, you go higher.</p><p>The deeper lesson: never deploy with default connection pool settings. Check them. Understand them. Set them deliberately.</p><h3>Mistake 2: No Timeout on External Calls</h3><p>The second thing that failed was subtler and more expensive.</p><p>We called three external APIs: a payment processor, an email service, and a fraud detection provider. All three were configured with Spring’s default RestTemplate — which has no timeout by default.</p><p>When the fraud detection API started experiencing latency during our launch spike, our requests to it stopped returning. They just… waited. Indefinitely.</p><p>Each waiting request held a thread. Within minutes, our thread pool was full of requests waiting on a fraud detection API that was taking 30 seconds to respond. Our service — which had nothing to do with fraud detection for most endpoints — became completely unresponsive because of one slow dependency.</p><p>The fix:</p><pre>@Bean<br />public RestTemplate restTemplate() {<br />    HttpComponentsClientHttpRequestFactory factory = <br />        new HttpComponentsClientHttpRequestFactory();<br />    factory.setConnectTimeout(2000);<br />    factory.setReadTimeout(5000);<br />    return new RestTemplate(factory);<br />}</pre><p>Or with WebClient and the reactive stack, explicit timeouts per call.</p><p>Every external call needs a timeout. Not “probably.” Not “we should add that.” Every one. No exceptions.</p><h3>Mistake 3: Synchronous Email Sending</h3><p>When a user signed up, we sent a welcome email synchronously — inside the request handler, before returning the response.</p><p>This felt fine during development. We were using a reliable email provider. Emails went out in under a second.</p><p>Under load, the email provider’s API slowed down. Our signup endpoint, which should have taken 150ms, started taking 3 seconds — because it was waiting for an email to be delivered before returning a response.</p><p>Users saw a slow signup flow. Some retried. Some left. The email provider got hammered with duplicate sends as retry logic kicked in.</p><p>The fix is obvious in hindsight: fire and forget.</p><pre>@Async<br />public void sendWelcomeEmail(String userEmail) {<br />    // email sending logic<br />}</pre><p>Or better: publish an event, let a separate consumer handle email delivery asynchronously, with retries and dead-letter handling.</p><p>The rule: anything that doesn’t need to complete before the response returns should not be in the request thread. Email. Analytics events. Audit logs. Webhook calls. All of it.</p><h3>Mistake 4: No Caching on Expensive Queries</h3><p>We had an endpoint that returned product catalog data. It ran a query that joined four tables, applied a dozen filters, and returned about 200 rows.</p><p>In development, with 500 rows per table, it ran in 40ms.</p><p>In production, with 500,000 rows per table, it ran in 1,800ms. Under load, with 300 concurrent requests hitting the same endpoint, it ran the same expensive query 300 times per second. The database CPU hit 100%. Everything else that touched the database slowed down too.</p><p>The catalog data changed once every four hours.</p><p>We were computing it on every request.</p><p>The fix:</p><pre>@Cacheable(value = &quot;productCatalog&quot;, key = &quot;#categoryId&quot;)<br />public List&lt;Product&gt; getProductCatalog(Long categoryId) {<br />    return productRepository.findByCategoryWithDetails(categoryId);<br />}</pre><p>With a TTL matching the actual update frequency — in this case, 4 hours. One query. Cached. Served from memory for every subsequent request until invalidation.</p><p>The rule: if data doesn’t change on every request, it shouldn’t be computed on every request.</p><h3>The Pattern Across All Four</h3><p>None of these were exotic bugs. No race conditions, no algorithmic complexity problems, no infrastructure failures.</p><p>They were configuration defaults accepted without question. External dependencies trusted without timeouts. Synchronous work that should have been asynchronous. Expensive computation repeated where caching was obvious.</p><p>Every one of them was invisible in staging. Every one of them was predictable in production, if I’d asked the right questions before launch.</p><p>The questions I ask now before every deploy:</p><ul><li>What are our connection pool limits, and what happens when we hit them?</li><li>What happens to every external call if the dependency is slow or down?</li><li>Which operations in the request path could be moved out of the request thread?</li><li>Which database queries run on every request, and which could be cached?</li></ul><p>Four questions. If I’d asked them three months earlier, the launch would have been a good day.</p><p>If you want a complete production-readiness system for Spring Boot — connection pool tuning, timeout configuration, async patterns, caching strategy, and the 47-point checklist I run before every deploy — I put it together here.</p><p><strong>→ </strong><a href="https://devrimozcay.gumroad.com/l/epxiu"><strong>Spring Boot Production System</strong></a> — run your APIs without crashing under load. Built from real incidents, not documentation.</p><p><em>I write about Java, Spring Boot, production engineering, and backend systems every week.</em></p><p><a href="https://substack.com/@devrimozcay1"><strong><em>Devrim’s Engineering Notes →</em></strong></a><em> — 1.2K+ engineers already reading.</em></p><p><em>Follow for more on Spring Boot, backend performance, and the production mistakes that are cheaper to read about than to live through.</em></p><img alt="" height="1" src="https://medium.com/_/stat?event=post.clientViewed&amp;referrerSource=full_rss&amp;postId=25f5a5481136" width="1" /><hr /><p><a href="https://blog.stackademic.com/my-spring-boot-api-crashed-under-10k-users-heres-every-mistake-i-made-25f5a5481136">My Spring Boot API Crashed Under 10K Users. Here’s Every Mistake I Made.</a> was originally published in <a href="https://blog.stackademic.com">Stackademic</a> on Medium, where people are continuing the conversation by highlighting and responding to this story.</p>

</details>