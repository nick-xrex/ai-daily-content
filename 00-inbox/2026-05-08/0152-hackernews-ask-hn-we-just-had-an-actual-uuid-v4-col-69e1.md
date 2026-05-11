---
id: inbox_d47d8838
source: hackernews
source_type: hn
url: "https://news.ycombinator.com/item?id=48060054"
author: "mittermayr"
published_at: 2026-05-08T07:57:14+00:00
fetched_at: 2026-05-11T01:52:02.260686+00:00
content_hash: "69e14c0fd311df435aa57692a6179dc7578b3a37df6cc82043b7287d96d0bf0f"
lang: en
caption_quality: None
raw: true
topics: []
---

# Ask HN: We just had an actual UUID v4 collision...

I know what you&#x27;re thinking... and I still can&#x27;t believe it, but... This morning, our database flagged a duplicate UUID (v4). I checked, thinking it may have been a double-insert bug or something, but no. The original UUID was from a record added in 2025 (about a year ago), and today the system inserted a new document with a fresh UUIDv4 and it came up with the exact same one: b6133fd6-70fe-4fe3-bed6-8ca8fc9386cd We&#x27;re using this:
https:&#x2F;&#x2F;www.npmjs.com&#x2F;package&#x2F;uuid I thought this is technically impossible, and it will never happen, and since we&#x27;re not modifying the UUIDs in any way, I really wonder how that.... is possible!? We&#x27;re literally only calling: import { v4 as uuidv4 } from &quot;uuid&quot;; const document_id = uuidv4(); ... and then insert into the database, that&#x27;s it. Additionally, the database only has about 15.000 records, and now one collision. Statistically... impossible. Has that ever happened to anyone?! What in the...