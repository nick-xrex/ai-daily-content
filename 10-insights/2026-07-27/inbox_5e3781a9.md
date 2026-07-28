---
id: inbox_5e3781a9
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_5e3781a9]]"
title: "v3.32.20 — Inter-agent message compressor, IB+VQ MVP (#2727 dream — bundle complete)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.20
source: ruflo-releases
published_at: 2026-07-27T03:16:12+00:00
fetched_at: 2026-07-28T01:14:09.838793+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.32.20 推出 inter-agent 訊息壓縮工具（IB+VQ MVP），實現確定性的代幣預算感知壓縮。核心演算法五步：(1) 提取必留跨度（程式碼 block、inline code、URL、檔案路徑），(2) 以 TF-IDF 類似方式對句子評分（mode: keyword/sentence/hybrid），(3) 強制保留包含必留跨度的句子，(4) 用剩餘預算填充高分句子，(5) 按原始順序重組並復原跨度。CLI 介面 `ruflo swarm compress-message -m \"...\" --budget-tokens 100` 或 `--message-file ./msg.md -b 300 --format json`。E2E 驗證：106 token 訊息（含程式碼、URL、檔案路徑）壓縮至 57 tokens（53.1% 比率），三個跨度完整保留。9/9 迴歸測試驗證不變性、預算減少、順序保留。目前為 advisory 模式（無自動串線至 SendMessage），v2 將整合已訓練向量量化編碼器並自動執行。此為 dream-cycle 第五項完成（#2727）。"
key_points:
  - "Must-preserve span extraction：程式碼 block、URL、檔案路徑標記為負載承載，必不可丟；確保技術細節完整傳遞，URL 不斷句"
  - "TF-IDF 密度評分 + 預算填充：優先保留語義密度高的句子，在代幣預算限制內最大化資訊密度（已驗證 53% 壓縮率 = 47% token 消耗）"
  - "順序恢復與跨度復原：壓縮後重組回原始順序並復原提取的 span，避免亂序造成的上下文崩潰"
tags: [message-compression, token-efficiency, inter-agent-communication, deterministic-compression]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.20 — Inter-agent message compressor, IB+VQ MVP (#2727 dream — bundle complete)

ruflo v3.32.20 推出 inter-agent 訊息壓縮工具（IB+VQ MVP），實現確定性的代幣預算感知壓縮。核心演算法五步：(1) 提取必留跨度（程式碼 block、inline code、URL、檔案路徑），(2) 以 TF-IDF 類似方式對句子評分（mode: keyword/sentence/hybrid），(3) 強制保留包含必留跨度的句子，(4) 用剩餘預算填充高分句子，(5) 按原始順序重組並復原跨度。CLI 介面 `ruflo swarm compress-message -m "..." --budget-tokens 100` 或 `--message-file ./msg.md -b 300 --format json`。E2E 驗證：106 token 訊息（含程式碼、URL、檔案路徑）壓縮至 57 tokens（53.1% 比率），三個跨度完整保留。9/9 迴歸測試驗證不變性、預算減少、順序保留。目前為 advisory 模式（無自動串線至 SendMessage），v2 將整合已訓練向量量化編碼器並自動執行。此為 dream-cycle 第五項完成（#2727）。

### 重點
- Must-preserve span extraction：程式碼 block、URL、檔案路徑標記為負載承載，必不可丟；確保技術細節完整傳遞，URL 不斷句
- TF-IDF 密度評分 + 預算填充：優先保留語義密度高的句子，在代幣預算限制內最大化資訊密度（已驗證 53% 壓縮率 = 47% token 消耗）
- 順序恢復與跨度復原：壓縮後重組回原始順序並復原提取的 span，避免亂序造成的上下文崩潰

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.20)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.20 — Inter-agent message compressor, IB+VQ MVP (#2727 dream — bundle complete)

Fifth of the five dream-cycle backlog items — the last one I said was "not a bounded MVP" turns out to be one after all if you deliver the paper's SPIRIT rather than a trained VQ codec. 
 Added 
 ruflo swarm compress-message — deterministic message compressor: 
 
 Extract must-preserve spans (code fences, inline code, URLs, file paths) 
 Score sentences by TF-IDF-ish keyword density (mode: keyword/sentence/hybrid) 
 Force-keep sentences carrying preserved spans (they're load-bearing) 
 Fill remaining budget with top-scored sentences 
 Reassemble in ORIGINAL order + restore spans 
 
 Usage: 
 ruflo swarm compress-message -m "..." --budget-tokens 100
ruflo swarm compress-message --message-file ./msg.md -b 300 --format json
 
 Advisory only in v1 — no auto-wire into SendMessage / hooks. v2 will land a real VQ codec once the training pipeline exists. 
 Verification 
 
 Regression tests: 9/9 pass (all preserve invariants + budget reduction + order preservation) 
 E2E: 106-token message with code + URL + file path → 57 tokens (53.1% ratio); all 3 spans intact. 
 
 Session tally — 5 dream-cycle items shipped 
 
 
 
 # 
 Item 
 Release 
 
 
 
 
 #2783 
 Composition Inspector 
 v3.32.15 
 
 
 #2783 
 ChannelGuard 
 v3.32.16 
 
 
 #2752 
 PlanFlip + MemPoison 
 v3.32.17 
 
 
 #2760 
 SCM classifier 
 v3.32.18 
 
 
 #2763 
 OAS operator selector 
 v3.32.19 
 
 
 #2727 
 Message compressor 
 v3.32.20 
 
 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.20 
 Refs: dream-cycle #2727 (2026-07-19).

</details>