---
id: inbox_5dc38f47
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0132-hackernews-nethack-5-0-0-87f2]]"
title: "NetHack 5.0.0"
url: https://nethack.org/v500/release.html
source: hackernews
published_at: 2026-05-02T18:03:42+00:00
fetched_at: 2026-05-03T02:09:22.160803+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "NetHack 5.0.0 於 2026 年 5 月 2 日發布，這是一次重大現代化版本。核心改進包括：完整達成 C99 標準合規性提升跨平臺相容性；將編譯流程從 yacc/lex 基礎改為 Lua 編譯器（改為在遊戲運行時動態載入而非編譯期靜態編譯），簡化編譯過程；移除交叉編譯障礙，允許使用者在一個系統上為不同平臺編譯；包含超過 3,100 項修複和變更。重要提示：舊版存檔和 bones 檔案與本版不相容，鼓勵社群提交 bug 報告和 pull request。"
key_points:
  - "C99 標準合規化，改進跨平臺相容性"
  - "編譯流程現代化：從靜態 yacc/lex 改為動態 Lua 編譯器 (runtime loading)"
  - "3,100+ 修複和變更，支援交叉編譯，舊存檔不相容"
tags: [nethack, c99, lua-compiler, cross-compilation, open-source-game]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## NetHack 5.0.0

NetHack 5.0.0 於 2026 年 5 月 2 日發布，這是一次重大現代化版本。核心改進包括：完整達成 C99 標準合規性提升跨平臺相容性；將編譯流程從 yacc/lex 基礎改為 Lua 編譯器（改為在遊戲運行時動態載入而非編譯期靜態編譯），簡化編譯過程；移除交叉編譯障礙，允許使用者在一個系統上為不同平臺編譯；包含超過 3,100 項修複和變更。重要提示：舊版存檔和 bones 檔案與本版不相容，鼓勵社群提交 bug 報告和 pull request。

### 重點
- C99 標準合規化，改進跨平臺相容性
- 編譯流程現代化：從靜態 yacc/lex 改為動態 Lua 編譯器 (runtime loading)
- 3,100+ 修複和變更，支援交叉編譯，舊存檔不相容

**原文：** [hackernews](https://nethack.org/v500/release.html)