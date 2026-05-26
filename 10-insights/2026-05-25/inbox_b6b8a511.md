---
id: inbox_b6b8a511
date: 2026-05-25
source_ref: "[[00-inbox/2026-05-25/0014-rtk-releases-dev-0-43-0-rc-244-8264]]"
title: "dev-0.43.0-rc.244"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.244
source: rtk-releases
published_at: 2026-05-25T13:40:27+00:00
fetched_at: 2026-05-26T00:24:06.752617+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "rtk dev-0.43.0-rc.244 修复 bash hook 对行继续符（backslash）的处理。Hook 在匹配 bash 命令时需要先展开行继续符（line continuation），避免因跨行定义导致模式匹配失败。"
key_points:
  - "Hook 处理 bash 命令时需要先展开行继续符，再进行模式匹配（Fixes #1564）"
tags: [rtk, bash-hook, bug-fix]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.244

rtk dev-0.43.0-rc.244 修复 bash hook 对行继续符（backslash）的处理。Hook 在匹配 bash 命令时需要先展开行继续符（line continuation），避免因跨行定义导致模式匹配失败。

### 重點
- Hook 处理 bash 命令时需要先展开行继续符，再进行模式匹配（Fixes #1564）

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.244)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(hook): collapse bash line continuations before matching ( #1572 ) 

 Fixes #1564

</details>