---
id: inbox_03c3230b
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/1802-hackernews-show-hn-i-derived-a-pancake-8764]]"
title: "Show HN: I Derived a Pancake"
url: https://www.absurdlyoptimized.com/recipes/pancakes/
source: hackernews
published_at: 2026-06-05T06:42:42+00:00
fetched_at: 2026-06-08T18:21:03.608258+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "这是关于从化学和数学原理推导煎饼食谱的项目，不属于 AI 相关范畴。作者基于 25 年烹饪经验，用纯数学/化学方法设计了一个食谱计算工具，用户可选择手头有的材料（黄油、酸奶、酵母等），工具根据酸度、脂肪、盐度、糖分和 CO₂ 等化学目标自动计算最优配方。核心是编程、数值求解（二分法）和化学计量学，与 AI 无关。"
key_points:
  - "化学计量学方法：从实验化学原理逆向工程食谱"
  - "ESM 纯函数库：材料成分映射、二分求解器实现"
  - "参数化食谱：柠檬酸奶酵母煎饼为最优示例"
tags: [chemistry, recipe-optimization, algorithm]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: I Derived a Pancake

这是关于从化学和数学原理推导煎饼食谱的项目，不属于 AI 相关范畴。作者基于 25 年烹饪经验，用纯数学/化学方法设计了一个食谱计算工具，用户可选择手头有的材料（黄油、酸奶、酵母等），工具根据酸度、脂肪、盐度、糖分和 CO₂ 等化学目标自动计算最优配方。核心是编程、数值求解（二分法）和化学计量学，与 AI 无关。

### 重點
- 化学计量学方法：从实验化学原理逆向工程食谱
- ESM 纯函数库：材料成分映射、二分求解器实现
- 参数化食谱：柠檬酸奶酵母煎饼为最优示例

**原文：** [hackernews](https://www.absurdlyoptimized.com/recipes/pancakes/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

After 25 years of making other people&#x27;s pancake recipes - always yearning for more tang, more fluff, and more predictability - I decided to derive the pancake recipe from the chemistry. You mark checkboxes for what you have on hand (ricotta, sour cream, kefir, buttermilk, yogurt, cottage cheese, lemon, cream of tartar, etc.) and it computes the best recipe based on targets for acid, fat, salt, sugar, and CO2. My particular favorite are the yeast-raised lemon ricotta kefir pancakes - the best I&#x27;ve ever had. The math is done in a small pure-ESM library: ingredient composition to component masses and acid moles, a stoichiometry layer, and a bisection solver for the target deficits. I&#x27;m not a chemist, so if something is off, tell me and I will fix it!

</details>