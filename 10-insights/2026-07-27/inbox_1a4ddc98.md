---
id: inbox_1a4ddc98
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_1a4ddc98]]"
title: "v3.32.14 — parser scoping fix + hooks route --parallel canonical restored"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.14
source: ruflo-releases
published_at: 2026-07-27T02:20:52+00:00
fetched_at: 2026-07-28T01:16:18.473947+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.14 修復 CLI 解析器架構缺陷：全局 boolean flag 集合在所有命令中污染同名 flag。舊實作 getBooleanFlags() 走遍所有註冊命令與子命令，將所有 boolean 選項合併到單一全局集合，導致任何地方聲明某名稱為 boolean 就會在其他命令中被當作 boolean，迫使 v3.32.13 改名為 --moa-parallel。新實作 getScopedBooleanFlags 改為實現「narrowest scope wins」原則，當解析的子命令聲明該 flag 為 non-boolean 時從全局集合中移除。同時恢復 `hooks route --parallel` 作為規範 fanout flag（短 -p），--moa-parallel 保留為已棄用兼容別名。通過 56/56 解析器測試（新增 1 個回歸測試）與完整 E2E 矩陣驗證（--parallel 5 → 5、--moa-parallel 6 → 6、-p 4 → 4）。"
key_points:
  - "根本原因：全局 boolean 集合污染導致 v3.32.13 被迫改名 flag，scope 隔離失效"
  - "修復：getScopedBooleanFlags 實現 narrowest-scope-wins，子命令 non-boolean 聲告時移除全局集合"
  - "恢復 `hooks route --parallel`（短 -p）規範 flag，--moa-parallel 為兼容別名，56/56 回歸測試通過"
tags: [cli-parser, flag-scoping, scope-isolation, bug-fix]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.14 — parser scoping fix + hooks route --parallel canonical restored

Ruflo v3.32.14 修復 CLI 解析器架構缺陷：全局 boolean flag 集合在所有命令中污染同名 flag。舊實作 getBooleanFlags() 走遍所有註冊命令與子命令，將所有 boolean 選項合併到單一全局集合，導致任何地方聲明某名稱為 boolean 就會在其他命令中被當作 boolean，迫使 v3.32.13 改名為 --moa-parallel。新實作 getScopedBooleanFlags 改為實現「narrowest scope wins」原則，當解析的子命令聲明該 flag 為 non-boolean 時從全局集合中移除。同時恢復 `hooks route --parallel` 作為規範 fanout flag（短 -p），--moa-parallel 保留為已棄用兼容別名。通過 56/56 解析器測試（新增 1 個回歸測試）與完整 E2E 矩陣驗證（--parallel 5 → 5、--moa-parallel 6 → 6、-p 4 → 4）。

### 重點
- 根本原因：全局 boolean 集合污染導致 v3.32.13 被迫改名 flag，scope 隔離失效
- 修復：getScopedBooleanFlags 實現 narrowest-scope-wins，子命令 non-boolean 聲告時移除全局集合
- 恢復 `hooks route --parallel`（短 -p）規範 flag，--moa-parallel 為兼容別名，56/56 回歸測試通過

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.14)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.14 — parser scoping fix + hooks route --parallel canonical restored

Follow-up to v3.32.13 that closes the last thing I left as a documented workaround. 
 Fixed 
 Parser: subcommand's non-boolean flag now overrides the global boolean set. The prior getBooleanFlags() walked every registered command + subcommand and merged all boolean options into one flat set that governed value-consumption everywhere. Any command anywhere declaring a name as boolean poisoned that name on every other command. That forced the --moa-parallel rename in v3.32.13. Fix: getScopedBooleanFlags now REMOVES flags from the boolean set when the resolved subcommand declares them as non-boolean. Narrowest scope wins. 
 hooks route --parallel restored as the canonical MoA fanout flag (with short -p ). --moa-parallel kept as a deprecated compat alias for anyone who upgraded to v3.32.13 in the ~15-minute window before this patch. 
 Test plan run 
 
 Parser tests: 55/55 → 56/56 (new regression test guarding the scoping fix) 
 hooks route --mode moa E2E matrix, all pass: --parallel 5 → 5, --moa-parallel 6 → 6, -p 4 → 4, default → 3, both-passed → canonical wins. 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.14

</details>