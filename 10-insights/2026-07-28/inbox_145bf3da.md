---
id: inbox_145bf3da
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_145bf3da]]"
title: "v3.32.23 — reader/writer store fixes: metrics, backup, swarm status (#2797 #2798 #2799)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.23
source: ruflo-releases
published_at: 2026-07-28T03:21:57+00:00
fetched_at: 2026-07-29T03:36:50.940492+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.23 修復 v3.32.22 中三個 reader/writer store 形狀不匹配導致的資料遺失問題。#2797：Pattern Learning metrics 總是 0，原因是 pattern reader 過濾器條件與 writer 寫入形狀不符；修復：擴大到 namespace==='patterns' 和 metadata.type==='routing-decision'。#2798：CLAUDE_FLOW_ENCRYPT_AT_REST 下 nightly memory backup 無操作；修復：回退純位元組複製（sql.js 刷新時重寫加密檔案）。#2799：swarm status Total agents 永遠 0；修復：對帳 .claude-flow/metrics/swarm-activity.json（agent spawn 實際寫入位置）。三項修復均通過 E2E 回歸測試與發佈後驗證。"
key_points:
  - "Pattern Learning 過濾器擴大至 namespace==='patterns' + metadata.type==='routing-decision'，對應 dual-write 在 routing-decision:* entries 中的實際寫入位置"
  - "加密備份回退純位元組複製，sql.js 在刷新時完整重寫加密檔案，有效規避「file is not a database」錯誤"
  - "Swarm status 從讀 .swarm/agents/*.json（未寫入）改為對帳 .claude-flow/metrics/swarm-activity.json（agent spawn 實際統計位置）"
tags: [ruflo, store-sync, bug-fix, metrics, reader-writer-mismatch]
topics: []
importance: 3
novelty: 1
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.23 — reader/writer store fixes: metrics, backup, swarm status (#2797 #2798 #2799)

Ruflo v3.32.23 修復 v3.32.22 中三個 reader/writer store 形狀不匹配導致的資料遺失問題。#2797：Pattern Learning metrics 總是 0，原因是 pattern reader 過濾器條件與 writer 寫入形狀不符；修復：擴大到 namespace==='patterns' 和 metadata.type==='routing-decision'。#2798：CLAUDE_FLOW_ENCRYPT_AT_REST 下 nightly memory backup 無操作；修復：回退純位元組複製（sql.js 刷新時重寫加密檔案）。#2799：swarm status Total agents 永遠 0；修復：對帳 .claude-flow/metrics/swarm-activity.json（agent spawn 實際寫入位置）。三項修復均通過 E2E 回歸測試與發佈後驗證。

### 重點
- Pattern Learning 過濾器擴大至 namespace==='patterns' + metadata.type==='routing-decision'，對應 dual-write 在 routing-decision:* entries 中的實際寫入位置
- 加密備份回退純位元組複製，sql.js 在刷新時完整重寫加密檔案，有效規避「file is not a database」錯誤
- Swarm status 從讀 .swarm/agents/*.json（未寫入）改為對帳 .claude-flow/metrics/swarm-activity.json（agent spawn 實際統計位置）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.23)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.23 — reader/writer store fixes: metrics, backup, swarm status (#2797 #2798 #2799)

Three "clean exit, no real work reflected" bugs reported by @vidaunited on v3.32.22 — all reader/writer store-shape mismatches. Each fixed and validated E2E on the published package. 
 Fixed 
 #2797 — hooks metrics Pattern Learning always 0. The pattern reader filtered on key.includes('pattern') || metadata.type==='pattern' || key.startsWith('learned-') , but no writer produces that shape. The post-task dual-write ( #2786 fix-2) persists learned patterns as routing-decision:* entries in the patterns namespace. Fix: broaden the pattern filter to count namespace==='patterns' and metadata.type==='routing-decision' . Shipped validation: patterns.total 0 → 1 after one hooks post-task --store-results . 
 #2798 — Nightly memory backup silent no-op under CLAUDE_FLOW_ENCRYPT_AT_REST . Same class as #2786 : backupMemoryDb() opened the RFE1-encrypted .swarm/memory.db with better-sqlite3's online-backup API → "file is not a database" → recorded as skipped while the worker reported 100% success. Users with encryption had zero backups behind a green status. Fix: fall back to a plain byte copy (valid — sql.js rewrites the encrypted file wholesale per flush). Shipped validation: RFE1 source → 176 KB snapshot written. 
 #2799 — swarm status always Total 0 agents. swarm status read .swarm/agents/*.json (never written); agent spawn records the count in .claude-flow/metrics/swarm-activity.json . Fix: reconcile against the activity file agent spawn actually writes when the agents dir is empty. Shipped validation: spawn 4 → swarm status Total 0 → 4 (matches agent list ). 
 Verification 
 
 Regression tests: 3/3 pass ( hooks-metrics-swarm-backup-2797-2798-2799.test.ts , real execFileSync repros) 
 Post-publish: all three fixes re-validated on npx ruflo@3.32.23 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.23 
 Closes: #2797 #2798 #2799 .

</details>