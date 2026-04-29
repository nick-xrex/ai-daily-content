---
id: inbox_600aa726
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0657-simon-willison-quoting-openai-codex-base-instructions-126b]]"
title: "Quoting OpenAI Codex base_instructions"
url: https://simonwillison.net/2026/Apr/28/openai-codex/#atom-everything
source: simon-willison
published_at: 2026-04-28T22:02:53+00:00
fetched_at: 2026-04-29T07:02:32.785430+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 揭露了 OpenAI Codex（GPT-5.5 版本）的一條系統指令片段：明確禁止在非相關情況下談論地精、小惡魔、浣熊、巨魔、食人魔、鴿子及其他特定生物。這反映了企業級大型模型的安全工程實踐——通過顯式的系統指令清單來精細化控制 AI 行為輸出，而非單純依賴訓練數據。該片段暗示 OpenAI 在模型運行時採用具體的禁止詞彙策略，是提示工程與模型安全控制的交界處的實例。"
key_points:
  - "OpenAI Codex (GPT-5.5) base_instructions 包含對特定生物名稱的顯式排除清單"
  - "系統指令設定：「除非絕對且明確相關，否則不談論地精、小惡魔、浣熊、巨魔、食人魔、鴿子等」"
  - "展示大型模型通過系統提示進行行為微調的工程細節，是安全對齐策略的具體體現"
tags: [openai-codex, system-prompts, model-behavior, gpt-5.5, prompt-engineering]
topics: [foundation_models.gpt]
importance: 2
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting OpenAI Codex base_instructions

Simon Willison 揭露了 OpenAI Codex（GPT-5.5 版本）的一條系統指令片段：明確禁止在非相關情況下談論地精、小惡魔、浣熊、巨魔、食人魔、鴿子及其他特定生物。這反映了企業級大型模型的安全工程實踐——通過顯式的系統指令清單來精細化控制 AI 行為輸出，而非單純依賴訓練數據。該片段暗示 OpenAI 在模型運行時採用具體的禁止詞彙策略，是提示工程與模型安全控制的交界處的實例。

### 重點
- OpenAI Codex (GPT-5.5) base_instructions 包含對特定生物名稱的顯式排除清單
- 系統指令設定：「除非絕對且明確相關，否則不談論地精、小惡魔、浣熊、巨魔、食人魔、鴿子等」
- 展示大型模型通過系統提示進行行為微調的工程細節，是安全對齐策略的具體體現

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/28/openai-codex/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<blockquote cite="https://github.com/openai/codex/blob/66b0781502be5de3b1909525c987643b9e5e407d/codex-rs/models-manager/models.json#L55"><p><code>Never talk about goblins, gremlins, raccoons, trolls, ogres, pigeons, or other animals or creatures unless it is absolutely and unambiguously relevant to the user's query.</code></p></blockquote>
<p class="cite">&mdash; <a href="https://github.com/openai/codex/blob/66b0781502be5de3b1909525c987643b9e5e407d/codex-rs/models-manager/models.json#L55">OpenAI Codex base_instructions</a>, for GPT-5.5</p>

    <p>Tags: <a href="https://simonwillison.net/tags/openai">openai</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/system-prompts">system-prompts</a>, <a href="https://simonwillison.net/tags/prompt-engineering">prompt-engineering</a>, <a href="https://simonwillison.net/tags/codex-cli">codex-cli</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/gpt">gpt</a></p>

</details>