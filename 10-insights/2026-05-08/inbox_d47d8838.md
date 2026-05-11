---
id: inbox_d47d8838
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0152-hackernews-ask-hn-we-just-had-an-actual-uuid-v4-col-69e1]]"
title: "Ask HN: We just had an actual UUID v4 collision..."
url: https://news.ycombinator.com/item?id=48060054
source: hackernews
published_at: 2026-05-08T07:57:14+00:00
fetched_at: 2026-05-11T01:59:08.206000+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: ""
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

## Ask HN: We just had an actual UUID v4 collision...



### 重點

**原文：** [hackernews](https://news.ycombinator.com/item?id=48060054)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I know what you&#x27;re thinking... and I still can&#x27;t believe it, but... This morning, our database flagged a duplicate UUID (v4). I checked, thinking it may have been a double-insert bug or something, but no. The original UUID was from a record added in 2025 (about a year ago), and today the system inserted a new document with a fresh UUIDv4 and it came up with the exact same one: b6133fd6-70fe-4fe3-bed6-8ca8fc9386cd We&#x27;re using this:
https:&#x2F;&#x2F;www.npmjs.com&#x2F;package&#x2F;uuid I thought this is technically impossible, and it will never happen, and since we&#x27;re not modifying the UUIDs in any way, I really wonder how that.... is possible!? We&#x27;re literally only calling: import { v4 as uuidv4 } from &quot;uuid&quot;; const document_id = uuidv4(); ... and then insert into the database, that&#x27;s it. Additionally, the database only has about 15.000 records, and now one collision. Statistically... impossible. Has that ever happened to anyone?! What in the...

</details>