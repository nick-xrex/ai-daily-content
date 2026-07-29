---
id: inbox_e11c9a79
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_e11c9a79]]"
title: "uv 0.12.0"
url: https://simonwillison.net/2026/Jul/28/uv/#atom-everything
source: simon-willison
published_at: 2026-07-28T21:51:38+00:00
fetched_at: 2026-07-29T03:38:42.109500+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Python 包管理工具 uv 發布 0.12.0 版本，包含 breaking changes。uv init 命令默認改為產生 src/ 目錄結構（之前在項目根放 main.py），增加 uv_build 後端用於打包，並設置 uv-init 腳本別名於 src/uv_init/__init__.py。此變更對應業界 src-layout 打包標準，預示該工具朝向 1.0 方向邁進。"
key_points:
  - "uv init 默認結構從根目錄 main.py 改為 src/ 佈局"
  - "新增 uv_build 後端支持 wheel 和 tarball 打包"
  - "設置腳本別名簡化項目初始化流程"
tags: [uv, python, packaging, breaking-changes]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## uv 0.12.0

Python 包管理工具 uv 發布 0.12.0 版本，包含 breaking changes。uv init 命令默認改為產生 src/ 目錄結構（之前在項目根放 main.py），增加 uv_build 後端用於打包，並設置 uv-init 腳本別名於 src/uv_init/__init__.py。此變更對應業界 src-layout 打包標準，預示該工具朝向 1.0 方向邁進。

### 重點
- uv init 默認結構從根目錄 main.py 改為 src/ 佈局
- 新增 uv_build 後端支持 wheel 和 tarball 打包
- 設置腳本別名簡化項目初始化流程

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/28/uv/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# uv 0.12.0

uv 0.12.0 
Some interesting breaking changes in this release of uv , in particular to the default project produced by the uv init command. 
 uv init is the uv shortcut for creating a new project. The previous version of uv , version 0.11.x, produced this directory when you ran uv init uv-init . 
 Here's what you get with uv 0.12 . I have a GitHub repository that automatically snapshots the output of uv init , so you can also see the full diff : 
 
 uv init now defaults to a src/ shaped package, instead of dropping main.py in the root of the project. It also configures the uv_build backend for building wheels and .tar.gz distribution files when you run uv build . Finally, it sets up uv-init as a script alias which, when run with uv run uv-init , executes a new main() function in src/uv_init/__init__.py . 
 I've so far avoided using src layout in my own projects just out of inertia. I think it's time I switched. 
 I wonder when uv will be judged ready for a 1.0 release?

 Tags: packaging , python , uv

</details>