---
id: inbox_153e97a1
date: 2026-06-18
source_ref: "[[00-inbox/2026-06-18/2200-rtk-releases-dev-0-43-0-rc-279-23d7]]"
title: "dev-0.43.0-rc.279"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.279
source: rtk-releases
published_at: 2026-06-18T14:20:05+00:00
fetched_at: 2026-06-18T22:08:12.238490+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.279 合併修復 PR #2416，針對 uv run 環境改進 pytest 整合。uv 是現代 Python 包管理與執行工具，隨著專案採用 uv 作為構建環境，pytest 測試流程需要相應調整以相容新環境。此次修復確保測試套件在 uv run 上下文中正常執行，強化專案在現代 Python 生態中的相容性和穩定性。"
key_points:
  - "修復 pytest 在 uv run 環境下的執行相容性"
  - "適應專案採用現代 Python 包管理工具（uv）的構建需求"
tags: [rtk, pytest, uv, python-tooling]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.279

RTK dev-0.43.0-rc.279 合併修復 PR #2416，針對 uv run 環境改進 pytest 整合。uv 是現代 Python 包管理與執行工具，隨著專案採用 uv 作為構建環境，pytest 測試流程需要相應調整以相容新環境。此次修復確保測試套件在 uv run 上下文中正常執行，強化專案在現代 Python 生態中的相容性和穩定性。

### 重點
- 修復 pytest 在 uv run 環境下的執行相容性
- 適應專案採用現代 Python 包管理工具（uv）的構建需求

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.279)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2416 from BrokkAi/fix/hook-uv-run-pytest 

 fix(hook): rewrite pytest under uv run

</details>