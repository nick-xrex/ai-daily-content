---
id: inbox_87fc6629
date: 2026-05-06
source_ref: "[[00-inbox/.../inbox_87fc6629]]"
title: "PSA: I annotated Claude Code&#39;s forced system prompt"
url: https://www.reddit.com/r/ClaudeAI/comments/1t4yu5v/psa_i_annotated_claude_codes_forced_system_prompt/
source: reddit-claudeai
published_at: 2026-05-06T01:33:36+00:00
fetched_at: 2026-05-06T13:32:42.944842+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 用戶分析並發佈 Claude Code 的完整系統提示註解版本（約 12K tokens），揭示 Anthropic 在每個 turn 注入優先於 CLAUDE.md、memory 檔案、skills 的硬編碼指令。重點問題包括：無條件禁止輸出歌詞、subagent 委派時強制優先 Haiku 結論導致覆蓋使用者代碼、三層疊疊的「保持簡潔」規則無視上下文需求。作者質疑此大雜燴式系統提示架構的可維護性與精準性，呼籲使用者應有透明度了解實際執行的約束。"
key_points:
  - "Claude Code 每 turn 強制注入 ~12K tokens 系統提示，優先序高於用戶 CLAUDE.md、memory、skills，形成對使用者指令的黑盒覆蓋"
  - "三類有問題的規則：（a）不分上下文的絕對禁令（歌詞）；（b）subagent 結論被強制當真理覆蓋用戶代碼；（c）多層『be brief』相互衝突無優先順序"
  - "系統缺乏機制偵測何時需要深度分析，導致規則在不適用場景火發，反映優先序堆疊的設計缺陷"
tags: [claude-code, system-prompt, transparency, constraint-architecture, prompt-hierarchy]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## PSA: I annotated Claude Code's forced system prompt

Reddit 用戶分析並發佈 Claude Code 的完整系統提示註解版本（約 12K tokens），揭示 Anthropic 在每個 turn 注入優先於 CLAUDE.md、memory 檔案、skills 的硬編碼指令。重點問題包括：無條件禁止輸出歌詞、subagent 委派時強制優先 Haiku 結論導致覆蓋使用者代碼、三層疊疊的「保持簡潔」規則無視上下文需求。作者質疑此大雜燴式系統提示架構的可維護性與精準性，呼籲使用者應有透明度了解實際執行的約束。

### 重點
- Claude Code 每 turn 強制注入 ~12K tokens 系統提示，優先序高於用戶 CLAUDE.md、memory、skills，形成對使用者指令的黑盒覆蓋
- 三類有問題的規則：（a）不分上下文的絕對禁令（歌詞）；（b）subagent 結論被強制當真理覆蓋用戶代碼；（c）多層『be brief』相互衝突無優先順序
- 系統缺乏機制偵測何時需要深度分析，導致規則在不適用場景火發，反映優先序堆疊的設計缺陷

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t4yu5v/psa_i_annotated_claude_codes_forced_system_prompt/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# PSA: I annotated Claude Code's forced system prompt

<!-- SC_OFF --><div class="md"><p>Before your <a href="http://CLAUDE.md">CLAUDE.md</a>, before your memory files, before your skills, Anthropic injects ~12K tokens of system prompt into every single turn, as priority instructions that overrule anything you provide.</p> <p>I captured the full text from a Claude Code session and put it up verbatim with my annotations.</p> <p>Some of what's sitting above your code:</p> <ul> <li><strong>&quot;Never reproduce song lyrics in ANY form&quot;</strong>... I find that one funny. A load-bearing rule injected into every turn, while I'm debugging a MCP tool auth in a cloudflare worker.</li> <li><strong>A subagent delegation rule</strong> that, in practice, has Opus hand off architectural reasoning to Haiku use these conclusion as ground truth and ignore your code. </li> <li><strong>Three separate &quot;be brief&quot; rules</strong> stacked on top of each other, with no mechanism to detect when depth is actually warranted.</li> </ul> <p>But more importantly: I hope this approach, one massive patchwork prompt firing in every direction at once, gets replaced by something more serious.</p> <p>My annotations are color-coded by concern: <strong>Behavioral</strong> (rules that shape how Claude responds), <strong>Hierarchy</strong> (where the rule sits in the stack), <strong>Scope</strong> (rules that fire in contexts they were never designed for).</p> <p>Every Claude Code user should have visibility into what's actually running above their stack </p> <p><strong>Report is here:</strong> <a href="http://prompt.anashel.com"><strong>prompt.anashel.com</strong></a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/anashel"> /u/anashel </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t4yu5v/psa_i_annotated_claude_codes_forced_system_prompt/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t4yu5v/psa_i_annotated_claude_codes_forced_system_prompt/">[comments]</a></span>

</details>