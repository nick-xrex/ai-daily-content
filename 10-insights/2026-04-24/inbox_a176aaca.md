---
id: inbox_a176aaca
date: 2026-04-24
source_ref: "[[00-inbox/2026-04-24/0246-simon-willison-russellromney-honker-c013]]"
title: "russellromney/honker"
url: https://simonwillison.net/2026/Apr/24/honker/#atom-everything
source: simon-willison
published_at: 2026-04-24T01:50:07+00:00
fetched_at: 2026-04-24T02:54:19.569146+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "honker 是一個 Rust 實現的 SQLite 擴展（含多語言綁定），提供 Postgres NOTIFY/LISTEN 語義以支援隊列和事件流。核心設計是 transactional outbox pattern：事件僅在事務成功提交時才被入隊，解決分散系統中業務邏輯與副作用同步的難題。提供 20+ 自訂 SQL 函數，Python API 支援 `enqueue()/claim()/ack()` 隊列操作和 `publish()/subscribe()` Kafka 風格流。Worker 透過 poll .db-wal 文件（1ms 檢查一次）達成近實時性能，無需執行完整 SQL 查詢。此實作驗證了事務型出站模式在 SQLite 上的可行性。"
key_points:
  - "SQLite 擴展實現 Postgres NOTIFY/LISTEN，支援隊列和事件流 + 20+ 自訂 SQL 函數"
  - "核心模式：transactional outbox pattern（確保消息僅在事務提交時入隊，解決最難的分散系統同步問題）"
  - "1ms WAL 輪詢 + 事務性保證，無需 RabbitMQ/Kafka，適合單體 + SQLite 架構"
tags: [sqlite-extension, transactional-outbox, job-queue, event-streaming, postgres-patterns]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## russellromney/honker

honker 是一個 Rust 實現的 SQLite 擴展（含多語言綁定），提供 Postgres NOTIFY/LISTEN 語義以支援隊列和事件流。核心設計是 transactional outbox pattern：事件僅在事務成功提交時才被入隊，解決分散系統中業務邏輯與副作用同步的難題。提供 20+ 自訂 SQL 函數，Python API 支援 `enqueue()/claim()/ack()` 隊列操作和 `publish()/subscribe()` Kafka 風格流。Worker 透過 poll .db-wal 文件（1ms 檢查一次）達成近實時性能，無需執行完整 SQL 查詢。此實作驗證了事務型出站模式在 SQLite 上的可行性。

### 重點
- SQLite 擴展實現 Postgres NOTIFY/LISTEN，支援隊列和事件流 + 20+ 自訂 SQL 函數
- 核心模式：transactional outbox pattern（確保消息僅在事務提交時入隊，解決最難的分散系統同步問題）
- 1ms WAL 輪詢 + 事務性保證，無需 RabbitMQ/Kafka，適合單體 + SQLite 架構

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/24/honker/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://github.com/russellromney/honker">russellromney/honker</a></strong></p>
"Postgres NOTIFY/LISTEN semantics" for SQLite, implemented as a Rust SQLite extension and various language bindings to help make use of it.</p>
<p>The design of this looks very solid. It lets you write Python code for queues that looks like this:</p>
<pre><span class="pl-k">import</span> <span class="pl-s1">honker</span>

<span class="pl-s1">db</span> <span class="pl-c1">=</span> <span class="pl-s1">honker</span>.<span class="pl-c1">open</span>(<span class="pl-s">"app.db"</span>)
<span class="pl-s1">emails</span> <span class="pl-c1">=</span> <span class="pl-s1">db</span>.<span class="pl-c1">queue</span>(<span class="pl-s">"emails"</span>)
<span class="pl-c1">emails</span>.<span class="pl-c1">enqueue</span>({<span class="pl-s">"to"</span>: <span class="pl-s">"alice@example.com"</span>})

<span class="pl-c"># Consume (in a worker process)</span>
<span class="pl-k">async</span> <span class="pl-k">for</span> <span class="pl-s1">job</span> <span class="pl-c1">in</span> <span class="pl-s1">emails</span>.<span class="pl-c1">claim</span>(<span class="pl-s">"worker-1"</span>):
    <span class="pl-en">send</span>(<span class="pl-s1">job</span>.<span class="pl-c1">payload</span>)
    <span class="pl-s1">job</span>.<span class="pl-c1">ack</span>()</pre>
<p>And Kafka-style durable streams like this:</p>
<pre><span class="pl-s1">stream</span> <span class="pl-c1">=</span> <span class="pl-s1">db</span>.<span class="pl-c1">stream</span>(<span class="pl-s">"user-events"</span>)

<span class="pl-k">with</span> <span class="pl-s1">db</span>.<span class="pl-c1">transaction</span>() <span class="pl-k">as</span> <span class="pl-s1">tx</span>:
    <span class="pl-s1">tx</span>.<span class="pl-c1">execute</span>(<span class="pl-s">"UPDATE users SET name=? WHERE id=?"</span>, [<span class="pl-s1">name</span>, <span class="pl-s1">uid</span>])
    <span class="pl-s1">stream</span>.<span class="pl-c1">publish</span>({<span class="pl-s">"user_id"</span>: <span class="pl-s1">uid</span>, <span class="pl-s">"change"</span>: <span class="pl-s">"name"</span>}, <span class="pl-s1">tx</span><span class="pl-c1">=</span><span class="pl-s1">tx</span>)

<span class="pl-k">async</span> <span class="pl-k">for</span> <span class="pl-s1">event</span> <span class="pl-c1">in</span> <span class="pl-s1">stream</span>.<span class="pl-c1">subscribe</span>(<span class="pl-s1">consumer</span><span class="pl-c1">=</span><span class="pl-s">"dashboard"</span>):
    <span class="pl-k">await</span> <span class="pl-en">push_to_browser</span>(<span class="pl-s1">event</span>)</pre>
<p>It also adds 20+ custom SQL functions including these two:</p>
<div class="highlight highlight-source-sql"><pre><span class="pl-k">SELECT</span> notify(<span class="pl-s"><span class="pl-pds">'</span>orders<span class="pl-pds">'</span></span>, <span class="pl-s"><span class="pl-pds">'</span>{"id":42}<span class="pl-pds">'</span></span>);
<span class="pl-k">SELECT</span> honker_stream_read_since(<span class="pl-s"><span class="pl-pds">'</span>orders<span class="pl-pds">'</span></span>, <span class="pl-c1">0</span>, <span class="pl-c1">1000</span>);</pre></div>
<p>The extension requires WAL mode, and workers can poll the <code>.db-wal</code> file with a stat call every 1ms to get as close to real-time as possible without the expense of running a full SQL query.</p>
<p>honker implements the <strong>transactional outbox pattern</strong>, which ensures items are only queued if a transaction successfully commits. My favorite explanation of that pattern remains <a href="https://brandur.org/job-drain">Transactionally Staged Job Drains in Postgres</a> by Brandur Leach. It's great to see a new implementation of that pattern for SQLite.

    <p><small></small>Via <a href="https://news.ycombinator.com/item?id=47874647">Show HN</a></small></p>


    <p>Tags: <a href="https://simonwillison.net/tags/databases">databases</a>, <a href="https://simonwillison.net/tags/postgresql">postgresql</a>, <a href="https://simonwillison.net/tags/sqlite">sqlite</a>, <a href="https://simonwillison.net/tags/rust">rust</a></p>

</details>