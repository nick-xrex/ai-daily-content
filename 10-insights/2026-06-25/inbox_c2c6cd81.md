---
id: inbox_c2c6cd81
date: 2026-06-25
source_ref: "[[00-inbox/.../inbox_c2c6cd81]]"
title: "datasette-export-database 0.3a2"
url: https://simonwillison.net/2026/Jun/25/datasette-export-database/#atom-everything
source: simon-willison
published_at: 2026-06-25T17:21:09+00:00
fetched_at: 2026-06-29T00:59:02.344559+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-export-database 0.3a2 版本修正了 pyproject.toml 中的一項關鍵相容性問題：將 Datasette 依賴項從硬性版本 `datasette==1.0a27` 改為相容性需求 `datasette>=1.0a27`，解除該外掛與其他 Datasette 版本的鎖定衝突。雖名為「尷尬的微小版本」，但這項修正對套件生態相容性至關重要。"
key_points:
  - "版本鎖定過度：原設定 `==1.0a27` 導致外掛與所有其他 Datasette 版本不相容"
  - "相容性改進：改為 `>=1.0a27` 後恢復上游版本相容性，重建與 Datasette 生態聯動"
  - "最佳實踐啟示：依賴項版本管理應平衡穩定性與相容性，過度鎖定反而降低套件可用性"
tags: [datasette, packaging, semver]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-export-database 0.3a2

datasette-export-database 0.3a2 版本修正了 pyproject.toml 中的一項關鍵相容性問題：將 Datasette 依賴項從硬性版本 `datasette==1.0a27` 改為相容性需求 `datasette>=1.0a27`，解除該外掛與其他 Datasette 版本的鎖定衝突。雖名為「尷尬的微小版本」，但這項修正對套件生態相容性至關重要。

### 重點
- 版本鎖定過度：原設定 `==1.0a27` 導致外掛與所有其他 Datasette 版本不相容
- 相容性改進：改為 `>=1.0a27` 後恢復上游版本相容性，重建與 Datasette 生態聯動
- 最佳實踐啟示：依賴項版本管理應平衡穩定性與相容性，過度鎖定反而降低套件可用性

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/25/datasette-export-database/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette-export-database 0.3a2

Release: datasette-export-database 0.3a2 
 An embarrassingly tiny release. The pyproject.toml had pinned to datasette==1.0a27 , inadvertently making this plugin incompatible with all other Datasette versions. It's now datasette&gt;=1.0a27 instead. 
 
 
 Tags: datasette

</details>