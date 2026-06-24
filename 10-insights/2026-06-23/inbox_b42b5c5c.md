---
id: inbox_b42b5c5c
date: 2026-06-23
source_ref: "[[00-inbox/2026-06-23/2202-hackernews-show-hn-tikz-editor-wysiwyg-editor-for-f-5d6e]]"
title: "Show HN: TikZ Editor – WYSIWYG editor for figures in LaTeX"
url: https://tikz.dev/editor/
source: hackernews
published_at: 2026-06-23T14:24:21+00:00
fetched_at: 2026-06-24T22:18:11.810228+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "TikZ 編輯器是一款 WYSIWYG LaTeX 圖表編輯工具，透過視覺介面與源碼即時同步的雙面編輯方式，讓學術寫手無需手動調整座標、重複編譯即可完成圖表。該編輯器由 Codex（OpenAI 編碼 AI）幾乎全程自動生成，展現 AI 編碼代理在極度繁瑣、重複性工作上的威力。編輯器實現了核心創新：當使用者拖曳元素時，應用僅改寫座標數字，保留所有源碼格式與縮排完好無損。這種雙向同步設計通常被視為不可能實現，因為需要重新實現 TikZ 剖析器、渲染器及多行換行演算法。作者強調的核心洞察：『建構那些因手工編寫不可行而從不存在過的軟體』正成為 AI 編碼代理的新使命。編輯器額外支援 SVG/PPTX/IPE 轉 TikZ 轉換、LaTeX 排版演算法重現等進階功能。"
key_points:
  - "WYSIWYG + 源碼同步編輯：拖曳元素時僅改座標，保留所有格式與縮排"
  - "由 Codex 自動生成，重新實現 TikZ 剖析器及渲染引擎（人工編寫原本不可行）"
  - "模式：AI 編碼代理適合用於『人類視為繁瑣不可行的軟體重寫任務』"
tags: [tikz-editor, wysiwyg, latex, codex, ai-agents]
topics: [foundation_models.gpt]
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: TikZ Editor – WYSIWYG editor for figures in LaTeX

TikZ 編輯器是一款 WYSIWYG LaTeX 圖表編輯工具，透過視覺介面與源碼即時同步的雙面編輯方式，讓學術寫手無需手動調整座標、重複編譯即可完成圖表。該編輯器由 Codex（OpenAI 編碼 AI）幾乎全程自動生成，展現 AI 編碼代理在極度繁瑣、重複性工作上的威力。編輯器實現了核心創新：當使用者拖曳元素時，應用僅改寫座標數字，保留所有源碼格式與縮排完好無損。這種雙向同步設計通常被視為不可能實現，因為需要重新實現 TikZ 剖析器、渲染器及多行換行演算法。作者強調的核心洞察：『建構那些因手工編寫不可行而從不存在過的軟體』正成為 AI 編碼代理的新使命。編輯器額外支援 SVG/PPTX/IPE 轉 TikZ 轉換、LaTeX 排版演算法重現等進階功能。

### 重點
- WYSIWYG + 源碼同步編輯：拖曳元素時僅改座標，保留所有格式與縮排
- 由 Codex 自動生成，重新實現 TikZ 剖析器及渲染引擎（人工編寫原本不可行）
- 模式：AI 編碼代理適合用於『人類視為繁瑣不可行的軟體重寫任務』

**原文：** [hackernews](https://tikz.dev/editor/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hi all! TikZ is a widely-used LaTeX package for drawing figures in papers. It uses commands like \draw[-&gt;] (0,0) -- (1,2); to draw lines, shapes, text, etc. Academics usually code up their figures by hand, so there is lots of twiddling around with the coordinates and recompiling until things look nice. I guess it’s a bit like SVG, but it’s more code than markup, for example it has loops with \foreach. I built an open-source WYSIWYG TikZ editor (available for web and desktop) that allows you to edit your TikZ source code visually by dragging and resizing elements. It simultaneously shows the source code and the rendered figure, and lets you edit either one while the two views stay in sync. I’m not aware of any other editors that are simultaneously source editors and WYSIWYG (even for editing SVG or HTML), and I’m quite pleased with how well the combination works. The way the app is implemented is by parsing the TikZ code, and at all times keeping track of the exact source location of each object. Thereby, when a user drags an element to a new position, the app can override just the numbers in the coordinate without changing anything else in the code (such as line breaks or indentation). This approach essentially required reimplementing a large fraction of TikZ, which is the kind of task that no human would ever want to do. I think building software that doesn’t exist yet because it would be impossibly tedious to code up is one of the great new possibilities thanks to coding agents, and it’s worth brainstorming for other examples. (This app was built almost entirely by Codex.) Implementing the app came with lots of fun side quests, including building converters from SVG &#x2F; pptx &#x2F; ipe to TikZ, re-implementing the LaTeX hyphenation and line-breaking algorithm to support multi-line nodes, and making a color picker that uses the red!20!black color mixing notation used in LaTeX papers.

</details>