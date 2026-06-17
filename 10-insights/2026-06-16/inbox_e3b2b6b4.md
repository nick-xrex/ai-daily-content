---
id: inbox_e3b2b6b4
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-rtk-releases-dev-0-43-0-rc-278-d4f0]]"
title: "dev-0.43.0-rc.278"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.278
source: rtk-releases
published_at: 2026-06-16T21:48:04+00:00
fetched_at: 2026-06-16T22:06:44.946893+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.278 發布。修復系統 grep 回退實現的 BSD/macOS 兼容性缺陷。原實現使用 -Z 標誌期待 NUL 檔名分隔符，但 -Z 在 BSD/macOS 上是 --decompress（zgrep 模式）別名，輸出純文本無 NUL，導致 parse_match_line() 匹配零檔案、所有結果折疊為「N matches in 0 files」並隱藏行內容。改用 --null 長選項，兩者都正確定義為「檔名後列印零字節」，修復 ripgrep 未安裝時的檔案匹配解析。"
key_points:
  - "根因：-Z 在 BSD/macOS 被誤作 --decompress，非 NUL 分隔符"
  - "方案：用 --null 長選項替代，實現 GNU/BSD grep 跨平台一致"
  - "範圍：ripgrep 不可用時系統 grep 回退路徑"
tags: [rtk, grep, portability, bsd-macos, bugfix]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.278

RTK dev-0.43.0-rc.278 發布。修復系統 grep 回退實現的 BSD/macOS 兼容性缺陷。原實現使用 -Z 標誌期待 NUL 檔名分隔符，但 -Z 在 BSD/macOS 上是 --decompress（zgrep 模式）別名，輸出純文本無 NUL，導致 parse_match_line() 匹配零檔案、所有結果折疊為「N matches in 0 files」並隱藏行內容。改用 --null 長選項，兩者都正確定義為「檔名後列印零字節」，修復 ripgrep 未安裝時的檔案匹配解析。

### 重點
- 根因：-Z 在 BSD/macOS 被誤作 --decompress，非 NUL 分隔符
- 方案：用 --null 長選項替代，實現 GNU/BSD grep 跨平台一致
- 範圍：ripgrep 不可用時系統 grep 回退路徑

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.278)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(grep): use portable --null in system grep fallback (BSD/macOS) 

 The system-grep fallback (used when ripgrep is not installed) passed
 -rnHZ, relying on -Z for the NUL filename separator the match parser
 requires. -Z only means --null on GNU grep; on BSD/macOS grep it is an
 alias for --decompress (zgrep mode), so output is plain
 file:line:content with no NUL. parse_match_line() then matches zero
 filenames and every result collapses into "N matches in 0 files" with
 all lines hidden behind [+N more]. 

 Use the long option --null instead, which both GNU and BSD grep define
 as "print a zero-byte after the file name". 

 Related to #2310 

 Co-Authored-By: Claude Fable 5 &lt;noreply@anthropic.com&gt;

</details>