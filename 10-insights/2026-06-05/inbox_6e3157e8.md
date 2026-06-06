---
id: inbox_6e3157e8
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/1800-rtk-releases-v0-42-3-a1d5]]"
title: "v0.42.3"
url: https://github.com/rtk-ai/rtk/releases/tag/v0.42.3
source: rtk-releases
published_at: 2026-06-05T16:29:54+00:00
fetched_at: 2026-06-05T18:05:41.429493+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.42.3 發布。新增 Copilot CLI 原生整合。修復內容：許可協議從 MIT 改為 Apache 2.0、輸出管道化時防止當機、grep 單檔案輸出解析修正、ls 八進位權限資訊保留、bash 行延續折疊修正、gh/glab 子命令 ID 檢查改進、多位元組字元 panic 修復。新增葡萄牙文文檔翻譯。"
key_points:
  - "新增 Copilot CLI 原生整合（#2101）"
  - "許可協議從 MIT 改為 Apache 2.0 全面更新"
  - "修正輸出管道化當機、多位元組字元 panic、bash 行延續解析問題"
tags: [rtk, cli, copilot, integration]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.42.3

RTK v0.42.3 發布。新增 Copilot CLI 原生整合。修復內容：許可協議從 MIT 改為 Apache 2.0、輸出管道化時防止當機、grep 單檔案輸出解析修正、ls 八進位權限資訊保留、bash 行延續折疊修正、gh/glab 子命令 ID 檢查改進、多位元組字元 panic 修復。新增葡萄牙文文檔翻譯。

### 重點
- 新增 Copilot CLI 原生整合（#2101）
- 許可協議從 MIT 改為 Apache 2.0 全面更新
- 修正輸出管道化當機、多位元組字元 panic、bash 行延續解析問題

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/v0.42.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

0.42.3 (2026-06-05) 
 Feats 
 
 feat(copilot): CLI native integration #2101 
 
 Fix 
 
 fix(docs): replace remaining MIT license references with Apache 2.0 #2084 
 fix: prevent crashes when output is piped #1048 close #1004 
 fix(grep): parse single-file output containing colons #1554 ; close #1436 . 
 fix(ls): preserve permission info as octal when -l/-la is passed #1675 
 fix(cicd): MIT to Apache 2.0 #2092 
 fix(pkg): rtk is Apache 2.0 and no MIT #2082 
 fix(hook): collapse bash line continuations before matching #1572 close Hook matcher: leading backslash-newline 
defeats command rewrite #1564 
 fix(gh,glab): don't pre-reject view/checks/run subcommands missing the id #2123 
 fix(git): fix panic on multibyte chars in commit output #1266 
 
 Other 
 
 docs(readme): add Portuguese translation #2128 
 doc(init): fix documentation inconsistencies arount rtk init #2173 
 fix(provider): sanatize more chars when encoding claude code project pathes #2172

</details>