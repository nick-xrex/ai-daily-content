---
id: inbox_b6dff65f
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_b6dff65f]]"
title: "Your Claude Code agent is always working from stale context. I built it a fix it can rewind, replay, and stay ahead of every edit."
url: https://www.reddit.com/r/ClaudeAI/comments/1t3du61/your_claude_code_agent_is_always_working_from/
source: reddit-claudeai
published_at: 2026-05-04T10:33:23+00:00
fetched_at: 2026-05-04T14:31:31.346980+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者發布 Memtrace，針對 Claude Code 長會話中的 stale context 問題。代理在長會話中會重複讀取同一文件、無法追蹤重構影響、缺乏代碼庫變更認知。Memtrace 的兩大創新：(1) 42ms 增量快照實現 always-fresh 記憶；(2) 雙時間層（valid_time + transaction_time）支持代碼狀態回溯和重放（rewind & replay）。架構核心：零 LLM 推理索引（Tree-sitter AST 解析）+ 混合檢索（Tantivy BM25 詞彙召回 + Jina-code 768D 嵌入語義召回 + Reciprocal Rank Fusion k=60 融合）+ 類型化圖邊（CALLS、IMPORTS、IMPLEMENTS 等）。開發者在構建 Memtrace 時親身遇到該問題，驗證工具必要性。免費發布，限制 50 批准/週，基準測試開源。

```mermaid
graph TB
    A[\"42ms 快照\"] -->|always-fresh| B[\"記憶層\"]
    C[\"雙時間層<br/>valid_time + transaction_time\"] -->|replay| D[\"代碼歷史\"]
    E[\"Tree-sitter AST<br/>0 LLM token\"] -->|structure| F[\"索引\"]
    G[\"BM25<br/>詞彙\"] -->|signal1| H[\"混合檢索\"]
    I[\"Jina 768D<br/>語義\"] -->|signal2| H
    H -->|RRF k=60| J[\"新鮮 context\"]
    B --> J
    D --> J
    F --> H
```"
key_points:
  - "Stale context 症狀：代理重複讀取、無 blast radius 感知、變更歷史遺忘"
  - "技術創新：42ms 增量快照 + 雙時間層 + 混合檢索（詞彙 BM25 + 語義 Jina 768D + RRF k=60）"
  - "架構決策：Tree-sitter AST 提煉結構（0 推理）、Jina 代碼特化嵌入、HNSW 語義索引"
tags: [claude-code, memory-management, code-indexing, bi-temporal, hybrid-retrieval]
topics: [foundation_models.claude]
importance: 4
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Your Claude Code agent is always working from stale context. I built it a fix it can rewind, replay, and stay ahead of every edit.

開發者發布 Memtrace，針對 Claude Code 長會話中的 stale context 問題。代理在長會話中會重複讀取同一文件、無法追蹤重構影響、缺乏代碼庫變更認知。Memtrace 的兩大創新：(1) 42ms 增量快照實現 always-fresh 記憶；(2) 雙時間層（valid_time + transaction_time）支持代碼狀態回溯和重放（rewind & replay）。架構核心：零 LLM 推理索引（Tree-sitter AST 解析）+ 混合檢索（Tantivy BM25 詞彙召回 + Jina-code 768D 嵌入語義召回 + Reciprocal Rank Fusion k=60 融合）+ 類型化圖邊（CALLS、IMPORTS、IMPLEMENTS 等）。開發者在構建 Memtrace 時親身遇到該問題，驗證工具必要性。免費發布，限制 50 批准/週，基準測試開源。

```mermaid
graph TB
    A["42ms 快照"] -->|always-fresh| B["記憶層"]
    C["雙時間層<br/>valid_time + transaction_time"] -->|replay| D["代碼歷史"]
    E["Tree-sitter AST<br/>0 LLM token"] -->|structure| F["索引"]
    G["BM25<br/>詞彙"] -->|signal1| H["混合檢索"]
    I["Jina 768D<br/>語義"] -->|signal2| H
    H -->|RRF k=60| J["新鮮 context"]
    B --> J
    D --> J
    F --> H
```

### 重點
- Stale context 症狀：代理重複讀取、無 blast radius 感知、變更歷史遺忘
- 技術創新：42ms 增量快照 + 雙時間層 + 混合檢索（詞彙 BM25 + 語義 Jina 768D + RRF k=60）
- 架構決策：Tree-sitter AST 提煉結構（0 推理）、Jina 代碼特化嵌入、HNSW 語義索引

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t3du61/your_claude_code_agent_is_always_working_from/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Your Claude Code agent is always working from stale context. I built it a fix it can rewind, replay, and stay ahead of every edit.

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t3du61/your_claude_code_agent_is_always_working_from/"> <img alt="Your Claude Code agent is always working from stale context. I built it a fix it can rewind, replay, and stay ahead of every edit." src="https://external-preview.redd.it/FYzNFNPNBVtAavw4i7WqRcoWLECd4p4G7GXh3YKh0Vg.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=2307f5c036b9c386fd6dee7ee8a11a19a8e3cedb" title="Your Claude Code agent is always working from stale context. I built it a fix it can rewind, replay, and stay ahead of every edit." /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Every long Claude Code session has the same hidden failure mode: the agent is always working from stale context.</p> <p>It re-reads the same 12 files across three sessions to &quot;remind itself&quot; of an interface you already showed it. It refactors getUserById without checking who calls it. It edits a config with no memory of why the previous version was that way. It's not the context window. The window is fine. There's no persistent, time-aware representation of your codebase for the agent to re-query. So it guesses. And you pay tokens for every re-read.</p> <p>I built Memtrace to fix exactly this.</p> <p>Two things it does that no other memory tool does:</p> <p><strong>(1) Always-fresh state.</strong> Every edit you make triggers a 42ms incremental snapshot of the changes applied by the coding agent. The agent's memory is never one-session-old. After a refactor it knows the blast radius before you do: every caller, every test, every consumer of the function you just touched. Your agent stops asking &quot;what does getUserById return?&quot; 30 seconds after seeing it.</p> <p><strong>(2) Rewind and replay.</strong> This is the part nobody else has. Your codebase is stored bi-temporally so every change becomes a recallable episode. When the agent debugs a regression, it can replay how the broken function got to its current state.</p> <ul> <li>What worked before.</li> <li>What changed when.</li> <li>Which commit introduced the bug</li> </ul> <p>Not just &quot;guess from current state.&quot;, instead replay.</p> <p>My architectural bet that makes both possible: zero LLM inference during indexing. Tree-sitter parses your code into an AST, and the AST IS the structural representation. You don't pay an LLM to re-derive what your compiler already knows.</p> <p>Retrieval is hybrid. Tantivy BM25 for lexical recall (the &quot;find getUserById&quot; query). Jina-code 768-dim embeddings indexed in HNSW for semantic recall (the &quot;find anything that authenticates a user&quot; query). Two ranked lists, fused with Reciprocal Rank Fusion at k=60. One signal alone misses, together they hit. The embedding model matters here: Jina-code is trained on code, not generic prose, so the semantic side actually understands &quot;this is an auth handler&quot; instead of pattern-matching on the word &quot;auth.&quot;</p> <p>The bi-temporal layer is what makes rewind possible. Every node and edge carries valid_time AND transaction_time, so &quot;what did this function look like Monday&quot; is a real query, not a git-blame heuristic. It's also what gives the agent the blast radius before a refactor: typed edges (CALLS, IMPORTS, IMPLEMENTS, EXTENDS, CONTAINS, TYPE_REFERENCES, INSTANTIATES) traversed in graph time, not text time.</p> <p>Speed only matters because freshness has to be cheap. If snapshotting after every edit is expensive, you can't afford to do it on every edit. So the indexing path is bottlenecked by I/O, not LLM tokens.</p> <p>I built it using Claude Code. Mid-build, Claude Code lost the plot on Memtrace's own architecture and it started contradicting decisions from 50 turns earlier. It re-read the same files. It forgot which retrieval weights I'd already tuned. I was experiencing the exact pain I was building Memtrace to solve, while building Memtrace.</p> <p>When the beta binary was ready, I pointed it at Memtrace's own codebase. The session-loss stopped. The blind refactor suggestions stopped.</p> <p>It's free, but the binary currently requires an approval key, just so you are warned.</p> <p>Not gatekeeping. Not marketing. The indexer keeps tripping on patterns I didn't anticipate: mixed pnpm/npm lockfiles, Rust proc-macros, Python Python TYPE_CHECKING blocks. Every one of these came from real beta users in the last two weeks, not from my test corpus. When that happens I want to ship you a fix in 24 hours, not lose you to a flaky first impression. So I'm pacing approvals to my own feedback bandwidth, not your patience. I'd rather have 500 users for whom this is magic than 50,000 for whom it's broken.</p> <p>I'm trying to keep approval under 24h, but capping at 50 per week right now. The benchmark harness is fully open and runnable without the key, if you want to verify the numbers before committing to the queue.</p> <p>Repo + waitlist: github.com/syncable-dev/memtrace-public</p> <p>Two questions:</p> <ol> <li>When Claude Code &quot;loses the plot&quot; on YOUR codebase, what specifically does it forget that hurts most? I'm collecting these for the next benchmark.</li> <li>What would you actually want to REWIND in your codebase if you could? Function history, dependency evolution, decision archaeology. Which is the killer one in your day?</li> </ol> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/WEEZIEDEEZIE"> /u/WEEZIEDEEZIE </a> <br /> <span><a href="https://github.com/syncable-dev/memtrace-public">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3du61/your_claude_code_agent_is_always_working_from/">[comments]</a></span> </td></tr></table>

</details>