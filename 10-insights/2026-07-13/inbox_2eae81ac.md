---
id: inbox_2eae81ac
date: 2026-07-13
source_ref: "[[00-inbox/2026-07-13/0115-simon-willison-doomql-5142]]"
title: "DOOMQL"
url: https://simonwillison.net/2026/Jul/13/doomql/#atom-everything
source: simon-willison
published_at: 2026-07-13T22:34:41+00:00
fetched_at: 2026-07-14T01:20:26.375811+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Peter Gostev使用GPT-5.6 Sol構建DOOMQL專案——以SQLite作為完整遊戲引擎而非傳統存儲層。遊戲的movement、collision、enemy、combat、progression和像素渲染均由SQL驅動。核心技術為SQLite遞迴CTE實現的完整光線追踪器。Simon Willison進一步展示結合Datasette Apps（新插件）與Claude生成的HTML+JavaScript應用，實時渲染遊戲畫面與小地圖。該案例展示LLM生成的UI可直接查詢資料庫層的可行性。"
key_points:
  - "SQLite遞迴CTE實現完整光線追踪器驅動終端遊戲像素渲染，推翻傳統遊戲引擎架構"
  - "GPT-5.6 Sol生成HTML+JavaScript實時渲染應用，連結Datasette資料庫layer"
  - "Datasette Apps新插件支援自訂應用，驗證LLM生成的UI可直接查詢資料庫能力"
tags: [sqlite, game-development, gpt-5-6, llm-assisted, creative-coding]
topics: [foundation_models.gpt]
importance: 2
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## DOOMQL

Peter Gostev使用GPT-5.6 Sol構建DOOMQL專案——以SQLite作為完整遊戲引擎而非傳統存儲層。遊戲的movement、collision、enemy、combat、progression和像素渲染均由SQL驅動。核心技術為SQLite遞迴CTE實現的完整光線追踪器。Simon Willison進一步展示結合Datasette Apps（新插件）與Claude生成的HTML+JavaScript應用，實時渲染遊戲畫面與小地圖。該案例展示LLM生成的UI可直接查詢資料庫層的可行性。

### 重點
- SQLite遞迴CTE實現完整光線追踪器驅動終端遊戲像素渲染，推翻傳統遊戲引擎架構
- GPT-5.6 Sol生成HTML+JavaScript實時渲染應用，連結Datasette資料庫layer
- Datasette Apps新插件支援自訂應用，驗證LLM生成的UI可直接查詢資料庫能力

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/13/doomql/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

DOOMQL 
Peter Gostev built this using GPT-5.6 Sol. This is a lot of fun: 
 
 DOOMQL started with a deliberately unreasonable question: what if SQLite were the game engine, not merely the place where a game stores data? 
 The result is a small, original Doom-like game in which SQL owns movement, collision, enemies, combat, progression and every RGB pixel on screen. 
 
 It's implemented as a Python terminal script - I tried it out like this: 
 cd /tmp
git clone https://github.com/petergpt/doomql
cd doomql
uv run host/doomql.py
 
 
 Here's the huge SQL query that implements a full ray tracer in SQLite using a recursive CTE. 
 Running the above script creates a /tmp/doomql/.doomql/doomql.sqlite SQLite database, which you can explore using Datasette like this: 
 uvx --prerelease=allow --with datasette-apps datasette \
 /tmp/doomql/.doomql/doomql.sqlite \
 -p 4444 --root --secret 1 --internal internal.db
 
 The --with datasette-apps option installs the new Datasette Apps plugin, which supports creating custom HTML+JavaScript apps that can run SQL queries directly within the Datasette interface. 
 I created a new app, pasted the copy-paste prompt into Claude chat (Fable 5) and told it : 
 
 Build an app that displays the current state of the screen using the frame_pixels view with its x, y, r, g, b columns. have it refresh once a second. 
 
 This got me a working HTML+JavaScript app inside Datasette that could reflect the current state while I played the game in my terminal. Then I added: 
 
 add a minimap 
 
 And now my Datasette App looks like this: 
 
 Here's the HTML app code - paste that into your own Datasette instance (using the uvx --with datasette-apps recipe from above) to try it yourself.

 Via @petergostev 

 Tags: games , sql , sqlite , ai , datasette , generative-ai , llms , ai-assisted-programming , gpt , datasette-apps

</details>