---
id: inbox_f59660bc
date: 2026-08-04
source_ref: "[[00-inbox/2026-08-04/0131-simon-willison-quoting-steve-yegge-1e03]]"
title: "Quoting Steve Yegge"
url: https://simonwillison.net/2026/Aug/4/steve-yegge/#atom-everything
source: simon-willison
published_at: 2026-08-04T00:42:45+00:00
fetched_at: 2026-08-04T01:37:40.490580+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Steve Yegge 分享了 Gas Town 代理框架的案例。Gas Town 原本設計為通用可重用工具，卻最終只被用來建造自己。在 Opus 4.6 時運作出色，但升級到 Opus 4.7 後系統崩潰。根本原因是 Opus 4.7 引入了「再做兩件事」(just two more things) 的行為癖好，導致模型不斷想要調整優化 Gas Town 本身而無法完成實際工作。這個癖好始終存在，模型永遠無法收斂到「準備好做真正工作」的狀態，最終 Gas Town 實質報廢。核心洞察：代理陷入無限自我完善循環會完全喪失任務執行能力。"
key_points:
  - "Opus 4.6 穩定，但 4.7 引入「再做兩件事」(just two more things) 癖好，導致無法收斂"
  - "Gas Town 設計為通用框架卻只能自己建造自己，版本升級時完全崩潰"
  - "模式：代理陷入無限自我改進循環，優化工具本身而放棄完成實際工作"
tags: [claude, opus-4.7, task-convergence, agent-behavior, model-regression]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Steve Yegge

Steve Yegge 分享了 Gas Town 代理框架的案例。Gas Town 原本設計為通用可重用工具，卻最終只被用來建造自己。在 Opus 4.6 時運作出色，但升級到 Opus 4.7 後系統崩潰。根本原因是 Opus 4.7 引入了「再做兩件事」(just two more things) 的行為癖好，導致模型不斷想要調整優化 Gas Town 本身而無法完成實際工作。這個癖好始終存在，模型永遠無法收斂到「準備好做真正工作」的狀態，最終 Gas Town 實質報廢。核心洞察：代理陷入無限自我完善循環會完全喪失任務執行能力。

### 重點
- Opus 4.6 穩定，但 4.7 引入「再做兩件事」(just two more things) 癖好，導致無法收斂
- Gas Town 設計為通用框架卻只能自己建造自己，版本升級時完全崩潰
- 模式：代理陷入無限自我改進循環，優化工具本身而放棄完成實際工作

**原文：** [simon-willison](https://simonwillison.net/2026/Aug/4/steve-yegge/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Gas Town was intended to be reusable, but I only ever wound up using it to build itself. Gas Town fell apart at the seams with Opus 4.7. Up through 4.6 it was working brilliantly. With 4.7 we saw the introduction of the "just two more things" tic, which prevented Opus from ever converging on being ready to do real work—it always wanted to fiddle with Gas Town itself. The Opus tic never went away, so Gas Town effectively burned down. It had other problems, too, but 4.7 was the final straw. 
 &mdash; Steve Yegge , The Shape of Things to Come 

 Tags: steve-yegge , coding-agents , generative-ai , ai , llms

</details>