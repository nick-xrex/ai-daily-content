---
id: inbox_2a825f86
date: 2026-07-11
source_ref: "[[00-inbox/.../inbox_2a825f86]]"
title: "rc/accf61c672e38104b3e26611ec3ebe0511e58848: fix(tree-sitter): recover declarations after embedded NUL bytes (#2430)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Faccf61c672e38104b3e26611ec3ebe0511e58848
source: gitnexus-releases
published_at: 2026-07-11T07:33:50+00:00
fetched_at: 2026-07-13T01:00:10.644322+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 修復了 tree-sitter 解析器對內嵌 NUL 字節的處理問題（#2430）。方案在解析器輸入層規範化 NUL 字節，保持 tree-sitter 通過完整源碼形狀恢復的能力。同時新增檔案標籤診斷和回歸測試覆蓋，涵蓋直接字串及回調解析路徑，提升代碼解析穩定性，特別針對含特殊字符的源文件。"
key_points:
  - "NUL 字節規範化限於輸入層，保護 tree-sitter 恢復邏輯完整性"
  - "新增工作線程診斷能力和多路徑回歸測試（直接字串 + 回調解析）"
  - "改進代碼解析穩定性，特別對包含特殊字符的文件"
tags: [gitnexus, tree-sitter, parser-fix, nul-byte-handling]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/accf61c672e38104b3e26611ec3ebe0511e58848: fix(tree-sitter): recover declarations after embedded NUL bytes (#2430)

GitNexus 修復了 tree-sitter 解析器對內嵌 NUL 字節的處理問題（#2430）。方案在解析器輸入層規範化 NUL 字節，保持 tree-sitter 通過完整源碼形狀恢復的能力。同時新增檔案標籤診斷和回歸測試覆蓋，涵蓋直接字串及回調解析路徑，提升代碼解析穩定性，特別針對含特殊字符的源文件。

### 重點
- NUL 字節規範化限於輸入層，保護 tree-sitter 恢復邏輯完整性
- 新增工作線程診斷能力和多路徑回歸測試（直接字串 + 回調解析）
- 改進代碼解析穩定性，特別對包含特殊字符的文件

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Faccf61c672e38104b3e26611ec3ebe0511e58848)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# rc/accf61c672e38104b3e26611ec3ebe0511e58848: fix(tree-sitter): recover declarations after embedded NUL bytes (#2430)

fix(tree-sitter): recover from embedded NUL bytes 
 
 Normalize embedded NUL bytes only in parser input so tree-sitter keeps recovering through the full source shape. Pass the file label through the worker for diagnostics and cover both direct-string and callback parse paths with regression tests. 
 
 
 fix(review): align safe-parser contract count 
 
 
 test(tree-sitter): cover worker NUL diagnostics ( #2430 )

</details>