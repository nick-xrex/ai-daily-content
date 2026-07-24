---
id: inbox_383de6f1
date: 2026-07-23
source_ref: "[[00-inbox/2026-07-23/0148-simon-willison-quoting-seth-larson-657d]]"
title: "Quoting Seth Larson"
url: https://simonwillison.net/2026/Jul/23/seth-larson/#atom-everything
source: simon-willison
published_at: 2026-07-23T04:50:36+00:00
fetched_at: 2026-07-24T02:00:49.555397+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Python Package Index (PyPI) 實施了新的供應鏈安全防禦機制，拒絕接受上傳到超過 14 天前發布的版本中的新文件（基於 Seth Larson 的報告）。此政策針對的是一種潛在的投毒攻擊向量：若發布用的令牌或 CI/CD 工作流程遭到洩露，攻擊者可能會修改已發布的「穩定」舊版本。透過限制舊版本的編輯窗口，PyPI 大幅提高了這類攻擊的成本。雖然尚未觀察到此攻擊方式被實際濫用，但從技術角度並無理由相信這個漏洞沒有被注意到。這是一種先發制人的防禦策略。"
key_points:
  - "PyPI 拒絕在 14 天前發布的版本上上傳新文件（供應鏈防禦機制）"
  - "防止已發布穩定版本遭投毒，對抗發布令牌洩露導致的后續攻擊"
  - "未被濫用但技術上可能，提前採取防禦措施防止社群被大規模波及"
tags: [pypi, supply-chain-security, package-security]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Seth Larson

Python Package Index (PyPI) 實施了新的供應鏈安全防禦機制，拒絕接受上傳到超過 14 天前發布的版本中的新文件（基於 Seth Larson 的報告）。此政策針對的是一種潛在的投毒攻擊向量：若發布用的令牌或 CI/CD 工作流程遭到洩露，攻擊者可能會修改已發布的「穩定」舊版本。透過限制舊版本的編輯窗口，PyPI 大幅提高了這類攻擊的成本。雖然尚未觀察到此攻擊方式被實際濫用，但從技術角度並無理由相信這個漏洞沒有被注意到。這是一種先發制人的防禦策略。

### 重點
- PyPI 拒絕在 14 天前發布的版本上上傳新文件（供應鏈防禦機制）
- 防止已發布穩定版本遭投毒，對抗發布令牌洩露導致的后續攻擊
- 未被濫用但技術上可能，提前採取防禦措施防止社群被大規模波及

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/23/seth-larson/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The Python Package Index (PyPI) now rejects new files being uploaded to releases that are older than 14 days. This restriction was put in place to prevent old and long-stable releases from being poisoned in case publishing tokens or workflows of PyPI projects were compromised. As far as we are aware this has not yet been abused, but there is no technical reason beyond that attackers weren't aware it was possible. 
 &mdash; Seth Larson , PyPI blog 

 Tags: packaging , python , supply-chain , pypi , seth-michael-larson

</details>