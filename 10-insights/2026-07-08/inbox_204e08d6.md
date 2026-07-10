---
id: inbox_204e08d6
date: 2026-07-08
source_ref: "[[00-inbox/.../inbox_204e08d6]]"
title: "Rewriting Bun in Rust"
url: https://simonwillison.net/2026/Jul/8/rewriting-bun-in-rust/#atom-everything
source: simon-willison
published_at: 2026-07-08T23:57:21+00:00
fetched_at: 2026-07-10T00:48:24.702397+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Jarred Sumner 詳述 Bun 從 Zig 用 AI agents（Claude Mythos/Fable）重寫為 Rust 的全過程。核心洞察：現代 frontier models 使過去視為禁忌的大規模代碼重寫成為可行。成功的三層驗證機制：(1) TypeScript 測試套件作為 conformance suite 自動檢驗百萬個 assertions，(2) 對抗性人工代碼 review 檢查 agent 輸出品質，(3) 發現問題時修復代碼生成流程而非手工個案修復。成本涉及 5.9 億 uncached input tokens + 6.9 億 output tokens + 720 億 cached token reads，估計 $165,000（Anthropic 員工享 token 福利）。Claude Code v2.1.181+ 已部署 Rust 版本近一月，Linux 啟動速度快 10%，生產環境運行穩定。"
key_points:
  - "三層驗證框架確保 AI 代碼可靠性：conformance suite（百萬 assertions） + 對抗性 review + 過程層級修復 vs. 逐行手工檢查"
  - "成本 $165K 涉及 5.9B uncached / 6.9M output / 720B cached tokens；Anthropic 內部投資展示對 agent 規模應用的信心"
  - "Claude Code v2.1.181+ 運行 Rust 版 Bun 近一月，Linux 啟動快 10%，展示 agent 生成代碼已達可生產部署品質"
tags: [claude, agents, bun, rust, agentic-rewrite, conformance-testing, adversarial-review]
topics: [foundation_models.claude]
importance: 5
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Rewriting Bun in Rust

Jarred Sumner 詳述 Bun 從 Zig 用 AI agents（Claude Mythos/Fable）重寫為 Rust 的全過程。核心洞察：現代 frontier models 使過去視為禁忌的大規模代碼重寫成為可行。成功的三層驗證機制：(1) TypeScript 測試套件作為 conformance suite 自動檢驗百萬個 assertions，(2) 對抗性人工代碼 review 檢查 agent 輸出品質，(3) 發現問題時修復代碼生成流程而非手工個案修復。成本涉及 5.9 億 uncached input tokens + 6.9 億 output tokens + 720 億 cached token reads，估計 $165,000（Anthropic 員工享 token 福利）。Claude Code v2.1.181+ 已部署 Rust 版本近一月，Linux 啟動速度快 10%，生產環境運行穩定。

### 重點
- 三層驗證框架確保 AI 代碼可靠性：conformance suite（百萬 assertions） + 對抗性 review + 過程層級修復 vs. 逐行手工檢查
- 成本 $165K 涉及 5.9B uncached / 6.9M output / 720B cached tokens；Anthropic 內部投資展示對 agent 規模應用的信心
- Claude Code v2.1.181+ 運行 Rust 版 Bun 近一月，Linux 啟動快 10%，展示 agent 生成代碼已達可生產部署品質

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/8/rewriting-bun-in-rust/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Rewriting Bun in Rust

Rewriting Bun in Rust 
Jarred Sumner has been promising this blog post ( since May 9th ) about his Zig to Rust rewrite of Bun for significantly longer than it took him to finish the rewrite. 
 Honestly, it was worth the wait. This is a detailed description of an extremely sophisticated piece of agentic engineering, featuring dynamic workflows, trial runs, adversarial review and all sorts of other interesting tricks. 
 Jarred spends the first half of the post praising Zig for getting Bun this far. Then we get to a core idea in the piece, emphasis mine: 
 
 Our bugfix list felt bad and I was tired of going to sleep worrying about crashes in Bun. I don't blame Zig for that - other users of Zig don't have the bugs we had, and mixing GC with manually-managed memory is an uncommon enough thing for software to need that no language really designs for it. We wouldn't have gotten this far if not for Zig, and I'll always be grateful. Until very recently, programming language choice was a one-way decision for a project like Bun. 
 
 Everyone knows you should never stop the world and rewrite a large piece of software from the ground up. Joel Spolsky highlighted that in Things You Should Never Do, Part I back in April 2000! 
 Coding agents powered by today's frontier models change that equation. 
 Why pick Rust? It all came down to those challenges with memory management: 
 
 A large percentage of bugs from that list are use-after-free, double-free, and "forgot to free" in an error path. In safe Rust, these are compiler errors and RAII-like automatic cleanup with Drop . 
 
 A crucial enabling factor for the rewrite was that the Bun test suite was written in TypeScript, which meant it could act as a conformance suite . This allowed an agent harness to automate much of the initial port from Bun to Rust, initially as an experiment to try out an earlier version of the model we now have access to as Mythos/Fable. 
 
 At first, I didn't expect it to work. A few days in, a high % of the test suite started passing and I saw how much the new Rust code matched up with the original Zig codebase. My opinion went from "this is worth trying" to "I'm going to merge this". [...] 
 For most of those 11 days (and after), I monitored workflows - manually reading the outputs to check for issues and bugs, and prompting Claude to edit the loop to fix things. 
 How do you review a PR with +1 million lines added? How do you start to build the confidence needed to responsibly merge large quantities of LLM-authored code? 
 A language-independent test suite with a million assertions, adversarial code review and when something does go wrong, fixing the process that generates the code instead of hand-fixing the code. 
 
 The new implementation of Bun has been live in Claude Code for nearly a month now: 
 
 Claude Code v2.1.181 (released June 17th) and later use the Rust port of Bun. Startup got 10% faster on Linux but otherwise, barely anyone noticed. Boring is good. 
 
 A perk of working at Anthropic is that you don't have to pay for your tokens - handy when the estimated cost is $165,000! 
 
 Pre-merge, this took 5.9 billion uncached input tokens, 690 million output tokens, and 72 billion cached input token reads — around $165,000 at API pricing. 
 
 This whole thing is a fascinating case study in taking on wildly ambitious projects with the help of coordinated parallel agents.

 Via Hacker News 

 Tags: ai , rust , zig , generative-ai , llms , ai-assisted-programming , anthropic , bun , conformance-suites , agentic-engineering , claude-mythos-fable

</details>