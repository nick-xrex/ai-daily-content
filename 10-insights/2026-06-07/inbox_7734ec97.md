---
id: inbox_7734ec97
date: 2026-06-07
source_ref: "[[00-inbox/2026-06-07/1802-hackernews-show-hn-lathe-use-llms-to-learn-a-new-do-05fc]]"
title: "Show HN: Lathe – Use LLMs to learn a new domain, not skip past it"
url: https://github.com/devenjarvis/lathe
source: hackernews
published_at: 2026-06-07T11:16:46+00:00
fetched_at: 2026-06-08T18:21:56.423607+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Lathe 是一個 LLM 驅動的教程生成工具，核心理念是「讓 LLM 輔助學習而非替代工作」。它結合 Go CLI 與 Claude Code/Cursor/Codex 等 LLM agent，可根據使用者提示（如「/lathe build a 3D slicer in Erlang」）自動生成帶有目錄、邊注、練習題和源始參考的互動式教程。用戶通過本地 webapp 手動閱讀和輸入代碼，工具並支援提問驗證、編譯檢查和內容擴展。作者的目標是填補缺乏優質人寫教程的技術領域（如 3D 建模、embedded Zig），而非取代已有資源。該設計體現了一個重要洞察：「使用者參與度越高，對 LLM 輸出的把關越好」，通過讓開發者手動操作來發現並糾正 AI 錯誤。"
key_points:
  - "Go CLI + Claude Code/Cursor/Codex agent 組合，可自動生成含目錄、邊注、練習題和源始引用的交互式教程"
  - "強調「手動輸入代碼 + 使用者驗證」的參與式學習，讓讀者主動發現並修正 LLM 錯誤，提升內容品質"
  - "針對 3D slicer from scratch、embedded Zig 等缺乏好教程的技術領域填補空白，而非取代人寫資源"
tags: [lathe, llm-learning, tutorial-generation, hands-on-learning, claude-code]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Lathe – Use LLMs to learn a new domain, not skip past it

Lathe 是一個 LLM 驅動的教程生成工具，核心理念是「讓 LLM 輔助學習而非替代工作」。它結合 Go CLI 與 Claude Code/Cursor/Codex 等 LLM agent，可根據使用者提示（如「/lathe build a 3D slicer in Erlang」）自動生成帶有目錄、邊注、練習題和源始參考的互動式教程。用戶通過本地 webapp 手動閱讀和輸入代碼，工具並支援提問驗證、編譯檢查和內容擴展。作者的目標是填補缺乏優質人寫教程的技術領域（如 3D 建模、embedded Zig），而非取代已有資源。該設計體現了一個重要洞察：「使用者參與度越高，對 LLM 輸出的把關越好」，通過讓開發者手動操作來發現並糾正 AI 錯誤。

### 重點
- Go CLI + Claude Code/Cursor/Codex agent 組合，可自動生成含目錄、邊注、練習題和源始引用的交互式教程
- 強調「手動輸入代碼 + 使用者驗證」的參與式學習，讓讀者主動發現並修正 LLM 錯誤，提升內容品質
- 針對 3D slicer from scratch、embedded Zig 等缺乏好教程的技術領域填補空白，而非取代人寫資源

**原文：** [hackernews](https://github.com/devenjarvis/lathe)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hey HN! Lathe is an experiment in using LLMs to teach me something new, instead of doing the work for me. It generates a hands-on, source-backed tutorial for any technical topic you want to learn. Then you work through it yourself by reading and typing the code by hand ( gasp ) in a local UI built for exactly that. It&#x27;s a Go CLI plus LLM agent skills (Claude Code &#x2F; Cursor &#x2F; Codex). You prompt something like &quot;&#x2F;lathe build a 3D slicer in Erlang&quot;, run `lathe serve` to spin up a local webapp, and read it in your browser. Every tutorial comes with the things that have made self-learning a pleasant experience for me in the past: - table of contents that follows along as you scroll
- side-notes that nudge you to think
- exercises for the reader
- sources backing up the content that you can use to take you deeper To help make up for the lack of human brainpower behind the tutorial, you can also ask questions about the content, have another LLM verify the tutorial actually compiles and runs, or extend it with another part (no more &quot;Part 4 of 6&quot; that hasn&#x27;t seen an update since 2021). I didn&#x27;t build lathe to replace human-written tutorials. I built lathe because I _love_ human-written tutorials, but wanted to learn technical domains where no good human-written tutorial exists yet (building a 3D slicer from scratch, making embedded Zig approachable, etc). There&#x27;s a longer story in the README about how I got started with programming through PSP homebrew tutorials, and why losing that to LLMs bugged me enough to build this. I&#x27;m not here to sell you anything (there&#x27;s nothing close to a VC-backed startup here :D). It&#x27;s an LLM, and its output is usually good but not perfect by any means. So far, my experience is that because you&#x27;re the one typing and actually engaged, you catch the weird stuff (and I&#x27;m finding that pushing back on it is its own kind of learning). And yes, it&#x27;s vibecoded, because it&#x27;s low scope, low risk, and scratching a personal itch. I run it on Claude Code + macOS personally, other setups should work but I haven&#x27;t been able to verify them yet. If you can find resources to learn something that was written by a human, read that first. But Lathe is here to fill in the gaps when that isn&#x27;t the case, and I hope it serves as an example where LLMs can help us think better, rather than less. Repo: https:&#x2F;&#x2F;github.com&#x2F;devenjarvis&#x2F;lathe Would love your feedback if you decide to check it out!

</details>