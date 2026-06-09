---
id: inbox_03c3230b
source: hackernews
source_type: hn
url: "https://www.absurdlyoptimized.com/recipes/pancakes/"
author: "bkazez"
published_at: 2026-06-05T06:42:42+00:00
fetched_at: 2026-06-08T18:02:25.527736+00:00
content_hash: "87649aa1c0592e17e7a21804b3b7695bd4a224c71cb66176753f770279e920d0"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: I Derived a Pancake

After 25 years of making other people&#x27;s pancake recipes - always yearning for more tang, more fluff, and more predictability - I decided to derive the pancake recipe from the chemistry. You mark checkboxes for what you have on hand (ricotta, sour cream, kefir, buttermilk, yogurt, cottage cheese, lemon, cream of tartar, etc.) and it computes the best recipe based on targets for acid, fat, salt, sugar, and CO2. My particular favorite are the yeast-raised lemon ricotta kefir pancakes - the best I&#x27;ve ever had. The math is done in a small pure-ESM library: ingredient composition to component masses and acid moles, a stoichiometry layer, and a bisection solver for the target deficits. I&#x27;m not a chemist, so if something is off, tell me and I will fix it!