---
id: inbox_ffd66334
source: hackernews
source_type: hn
url: https://victorpoughon.github.io/interval-calculator/
author: fouronnes3
published_at: 2026-04-18T01:15:43+00:00
fetched_at: 2026-04-20T02:20:35.624655+00:00
content_hash: "a675605bb46857597acaf6b53ad155559e587d8a9f374493f3ae886038ced4b3"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: I made a calculator that works over disjoint sets of intervals

I&#x27;ve been studying interval arithmetic for the past few weeks and it&#x27;s a really interesting field because while there is a ton of super interesting research published over the past decades, it has never really gotten the recognition that it deserves, IMO.<p>One reason for this is that standard interval arithmetic has really poor handling of division by intervals containing zero. If you compute 1 &#x2F; [-1, 2] in regular interval arithmetic, you get either [-∞, +∞], or you have to say that the operation is undefined. Both solutions are virtually useless. The real answer of course is [-∞, -1] U [0.5, +∞]: i.e. a union of two disjoint intervals.<p>This is useful because you can confidently exclude a non empty set of the real numbers ([-1, 0.5]) from the set of possible values that you can get by dividing 1 by a number between -1 and 2.<p>But this definition of interval division yields a value that is not an interval. This is a problem if you want to define a closed arithmetic system, where you can build and evaluate arbitrary expression over interval values.<p>(This behavior extends to any non continuous function like tan() for example, which is implemented in my project - not without difficulties!)<p>Well the obvious solution is to define your arithmetic over disjoint unions of intervals. This is the subject of a 2017 paper called &quot;Interval Unions&quot; by by Schichl, H., Domes, F., Montanher, T. and Kofler, K..<p>This open-source project I made implements interval union arithmetic in TypeScript in the form of a simple interactive calculator, so you can try it out for yourself! The underlying TypeScript library is dependency free and implements interval union arithmetic over IEEE 754 double precision floats (JS native number type) with outward rounding. This guarantees accuracy of interval results in the presence of rounding issue inherent to floating point.