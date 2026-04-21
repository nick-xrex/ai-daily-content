---
id: inbox_c2caec8e
date: 2026-04-20
source_ref: "[[00-inbox/.../inbox_c2caec8e]]"
title: "The “Senior” Dev Who Doesn’t Know SQL is a Liability"
url: https://blog.stackademic.com/the-senior-dev-who-doesnt-know-sql-is-a-liability-d1188440c3b9?source=rss----d1baaa8417a4---4
source: medium-stackademic
published_at: 2026-04-20T17:08:50+00:00
fetched_at: 2026-04-21T07:17:49.930233+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "資深後端工程師若只依賴 ORM 而不理解 SQL，會成為公司的負債。作者 12 年內審計 12 家公司，發現普遍現象：單一儀表板頁面產生 450 個查詢請求，每月白白花費 $15k 在資料庫成本上。核心問題不在工具而在認知——開發者習慣隱藏在 ORM 抽象後，無法識別 N+1 查詢、不當索引策略（例如給所有欄位都加索引），或連線池耗盡的根本原因。真正的優化需要掌握 EXPLAIN ANALYZE、複合索引設計、keyset 分頁等基礎技巧；單一 JOIN 和 GROUP BY 往往勝過添購更多伺服器。"
key_points:
  - "ORM 隱藏的 N+1 問題：審計案例單頁面 450 查詢，修復只需一個 JOIN 和 GROUP BY"
  - "索引不是「灑水車式」：亂加索引反而拖慢 INSERT/UPDATE/DELETE，應設計複合索引精準覆蓋常見查詢的 WHERE 和 ORDER BY"
  - "連線池耗盡是設計問題：作者遇到 100 連線上限 vs 150 K8s pods 自動擴容的故障；需要理解應用與 DB 在網路層的互動"
tags: [sql-performance, orm-limitations, n-plus-1, database-design, backend-fundamentals]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## The “Senior” Dev Who Doesn’t Know SQL is a Liability

資深後端工程師若只依賴 ORM 而不理解 SQL，會成為公司的負債。作者 12 年內審計 12 家公司，發現普遍現象：單一儀表板頁面產生 450 個查詢請求，每月白白花費 $15k 在資料庫成本上。核心問題不在工具而在認知——開發者習慣隱藏在 ORM 抽象後，無法識別 N+1 查詢、不當索引策略（例如給所有欄位都加索引），或連線池耗盡的根本原因。真正的優化需要掌握 EXPLAIN ANALYZE、複合索引設計、keyset 分頁等基礎技巧；單一 JOIN 和 GROUP BY 往往勝過添購更多伺服器。

### 重點
- ORM 隱藏的 N+1 問題：審計案例單頁面 450 查詢，修復只需一個 JOIN 和 GROUP BY
- 索引不是「灑水車式」：亂加索引反而拖慢 INSERT/UPDATE/DELETE，應設計複合索引精準覆蓋常見查詢的 WHERE 和 ORDER BY
- 連線池耗盡是設計問題：作者遇到 100 連線上限 vs 150 K8s pods 自動擴容的故障；需要理解應用與 DB 在網路層的互動

**原文：** [medium-stackademic](https://blog.stackademic.com/the-senior-dev-who-doesnt-know-sql-is-a-liability-d1188440c3b9?source=rss----d1baaa8417a4---4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

-d1baaa8417a4---4"
author: "Bug to Solution"
published_at: 2026-04-20T17:08:50+00:00
fetched_at: 2026-04-21T03:52:58.713675+00:00
content_hash: "78152221311f8cf5751ed6db229c9b2f7c9e454cbdc2f713b850cf842d0eedad"
lang: en
caption_quality: None
raw: true
topics: []
---

# The “Senior” Dev Who Doesn’t Know SQL is a Liability

<h4>Stop hiding behind your ORM and start reading your EXPLAIN ANALYZE output.</h4><figure><img alt="" src="https://cdn-images-1.medium.com/max/942/1*GybKJGBYjEn1JKzoFhc4zg.png" /></figure><p>I’ve been a contractor for 12 companies in the last 4 years. From FinTech giants to “disruptive” AI startups, the pattern is identical: the team is burning $15k a month on RDS instances because no one knows how a B-tree works.</p><p>You call yourself a Senior Backend Engineer, but you treat the database like a magical black box. You write User.all() in a loop and wonder why the API response takes 4 seconds. You add a microservice to &quot;handle the load&quot; when a single composite index would have solved the problem for free.</p><p>If you can’t write raw SQL, you aren’t a senior; you’re a liability.</p><h3>1. The ORM Tax is Bankrupting You</h3><p>ORMs are great for productivity, but they are dangerous for performance. I recently audited a startup where a single “Dashboard” page was triggering <strong>450 SQL queries</strong> per request.</p><p>It was the classic N+1 problem, hidden behind five layers of abstraction. The developers were busy refactoring their “Clean Architecture” folders while the database was screaming for help.</p><p>The fix wasn’t a “Cache.” The fix wasn’t “Go.” The fix was a single JOIN and a GROUP BY.</p><p>If you want to stop guessing and start fixing, you need to understand what’s actually happening under the hood. Most “mysterious” slow-downs are just common anti-patterns that are easy to spot once you know where to look: → <a href="https://www.google.com/search?q=https://yusufseyitoglu.gumroad.com/l/sql-performance-cheatsheet"><strong>SQL Performance Cheatsheet</strong></a> (free)</p><h3>2. Indexing is Not “Spray and Pray”</h3><p>I see “Senior” devs adding an index to every single column in a table.</p><p>That’s not an optimization strategy; that’s a sabotage. Every index you add slows down your INSERT, UPDATE, and DELETE operations. It bloats your storage and messes with the query optimizer’s head.</p><p>A real expert knows how to design a <strong>Composite Index</strong> that covers the exact WHERE and ORDER BY clauses of their most frequent queries. They know why a leading wildcard in a LIKE clause renders their index useless.</p><p>If your database is sluggish, don’t throw more RAM at it. Throw better logic at it. Start with this playbook to stop the bleeding: → <a href="https://www.google.com/search?q=https://yusufseyitoglu.gumroad.com/l/db-incident-playbook"><strong>Your Database Is Bleeding Money. The Incident Playbook.</strong></a> (free)</p><h3>3. The Silent Killer: Connection Pool Exhaustion</h3><p>Last month, a client’s production environment went dark. The logs were clean. The CPU was low.</p><p>The culprit? They had set their maximum database connections to 100, but their Kubernetes cluster had autoscaled to 150 pods. Every pod was trying to grab a connection on startup and timing out.</p><p>This is the kind of “infrastructure” failure that is actually a backend design failure. If you don’t understand how your application interacts with the DB at the networking layer, you are a ticking time bomb.</p><p>You need to know your limits. Literally. → <a href="https://www.google.com/search?q=https://yusufseyitoglu.gumroad.com/l/production-incidents"><strong>30 Production Incidents That Cost $10K+</strong></a> (free)</p><h3>4. Scaling is Just Solving for Bottlenecks</h3><p>Most “Scaling” problems are just “I didn’t think about the data growth” problems.</p><p>You wrote a query that worked fine with 1,000 rows. Now you have 10 million, and that OFFSET 500000 is scanning half the disk just to show page 50 of your results.</p><p>A Senior dev switches to <strong>keyset pagination</strong> (cursor-based). They don’t use SELECT * because they know fetching 40 columns when you only need 2 is a waste of I/O. They use EXPLAIN ANALYZE as their primary debugging tool, not their debugger.</p><h3>5. Stop Blaming the Tool</h3><p>“PostgreSQL is slow.” No, your schema is trash. “MySQL is locking up.” No, you’re running long-running transactions that are holding onto row locks for 30 seconds.</p><p>The database is usually the most stable part of your stack. It’s the code you’re wrapping around it that causes the chaos. If you’re heading into an interview for a Senior role and you can’t explain the difference between INNER and OUTERjoins or how ACID properties actually work in a distributed system, you’re going to get roasted.</p><p>Don’t be that candidate. Review the basics: → <a href="https://www.google.com/search?q=https://yusufseyitoglu.gumroad.com/l/backend-interview-mistakes"><strong>Top 50 Backend Interview Mistakes</strong></a> (free)</p><h3>The Bottom Line</h3><p>In 12 companies, I’ve saved teams hundreds of thousands of dollars just by deleting “elegant” code and replacing it with efficient SQL.</p><p>Complexity is a choice. Performance is a discipline.</p><p>Stop treating your data layer like an inconvenience and start treating it like the core of your application. Your company’s runway (and your sanity) depends on it.</p><p>The best way to ensure your code doesn’t become a “production incident” is to master the scenarios that actually happen in the wild.</p><p>Froquiz has 10,000+ questions across SQL, Docker, Git, AWS, JavaScript, Java, Python, React, Microservices and more — plus a Senior Dev Challenge with real scenario-based questions, not syntax drills. → <a href="https://froquiz.com/"><strong>Froquiz</strong></a></p><img alt="" height="1" src="https://medium.com/_/stat?event=post.clientViewed&amp;referrerSource=full_rss&amp;postId=d1188440c3b9" width="1" /><hr /><p><a href="https://blog.stackademic.com/the-senior-dev-who-doesnt-know-sql-is-a-liability-d1188440c3b9">The “Senior” Dev Who Doesn’t Know SQL is a Liability</a> was originally published in <a href="https://blog.stackademic.com">Stackademic</a> on Medium, where people are continuing the conversation by highlighting and responding to this story.</p>

</details>