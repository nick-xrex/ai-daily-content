---
id: inbox_f473f357
date: 2026-05-23
source_ref: "[[00-inbox/.../inbox_f473f357]]"
title: "On the &lt;dl&gt;"
url: https://simonwillison.net/2026/May/23/on-the-dl/#atom-everything
source: simon-willison
published_at: 2026-05-23T20:24:48+00:00
fetched_at: 2026-05-24T04:27:56.123611+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 介紹 HTML description list（<dl>）標籤的最新最佳實踐。文章指出：<dt> 可對應多個 <dd> 元素；可用 <div> 包裹 <dt>/<dd> 進行分組（僅 <div> 被允許）；可用 ARIA 屬性標注整個列表。自 2008 年 HTML5 草案起，該元素正式更名為「description list」而非「definition list」。文章亦引述 Adrian Roselli 的屏幕閱讀器支持指南，強調無障礙設計的重要性。"
key_points:
  - "<dt> 可對應多個 <dd>，支持複雜描述關係；可用 aria-labelledby 標注"
  - "僅允許用 <div> 分組 <dt>/<dd> 元素進行樣式化控制"
  - "屏幕閱讀器支持参考 Adrian Roselli 指南，確保無障礙設計"
tags: [html, dl-element, description-list, aria, accessibility, screen-readers]
topics: []
importance: 2
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## On the <dl>

Simon Willison 介紹 HTML description list（<dl>）標籤的最新最佳實踐。文章指出：<dt> 可對應多個 <dd> 元素；可用 <div> 包裹 <dt>/<dd> 進行分組（僅 <div> 被允許）；可用 ARIA 屬性標注整個列表。自 2008 年 HTML5 草案起，該元素正式更名為「description list」而非「definition list」。文章亦引述 Adrian Roselli 的屏幕閱讀器支持指南，強調無障礙設計的重要性。

### 重點
- <dt> 可對應多個 <dd>，支持複雜描述關係；可用 aria-labelledby 標注
- 僅允許用 <div> 分組 <dt>/<dd> 元素進行樣式化控制
- 屏幕閱讀器支持参考 Adrian Roselli 指南，確保無障礙設計

**原文：** [simon-willison](https://simonwillison.net/2026/May/23/on-the-dl/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# On the 

On the &lt;dl&gt; 
I learned a few new-to-me things about the &lt;dl&gt; element from this article by Ben Meyer: 
 
 A &lt;dt&gt; can be followed by multiple &lt;dd&gt; 
 You can optionally group the &lt;dt&gt; and &lt;dd&gt; elements in a &lt;div&gt; for styling - but only a &lt;div&gt; . 
 You can label them using ARIA. 
 They've been called "description lists", not "definition lists", since an HTML5 draft in 2008 . 
 
 So this is valid: 
 &lt; h2 id =" credits " &gt; Credits &lt;/ h2 &gt; 
 &lt; dl aria-labelledby =" credits " &gt; 
 &lt; div &gt; 
 &lt; dt &gt; Author &lt;/ dt &gt; 
 &lt; dd &gt; Jeffrey Zeldman &lt;/ dd &gt; 
 &lt; dd &gt; Ethan Marcotte &lt;/ dd &gt; 
 &lt;/ div &gt; 
 &lt;/ dl &gt; 

 Here's a useful note from Adrian Roselli on screen reader support for description lists .

 Via Hacker News 

 Tags: css , html , screen-readers , web-standards

</details>