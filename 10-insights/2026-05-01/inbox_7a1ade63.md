---
id: inbox_7a1ade63
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/1257-reddit-localllama-finetuning-dataset-claude-opus-4-6-4-7-8-8959]]"
title: "Finetuning Dataset: Claude Opus 4.6/4.7 - 8.7k Chats"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t0l2c8/finetuning_dataset_claude_opus_4647_87k_chats/
source: reddit-localllama
published_at: 2026-05-01T06:13:22+00:00
fetched_at: 2026-05-01T13:33:00.690573+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "HuggingFace 上發佈了包含 8,706 個合成示例的 Claude Opus 4.6/4.7 微調數據集，約 1,701 萬 token，涵蓋 28 個領域（編程、數學、人文、角色扮演等）。編程任務最多（1,628 例），多轮對話占 39.7%。該數據集來自 Claude 4.6（53.7%）與 4.7（46.3%）的合成數據，適合本地模型微調使用。"
key_points:
  - "數據集規模：8,706 例，1,701 萬 token，28 個領域類別"
  - "編程示例最多（1,628 例），多轮對話占 39.7%，平均 1,954 token/例"
  - "來源分布：Claude 4.6（4,675 例）與 4.7（4,031 例）合成"
tags: [claude-4.6, claude-4.7, finetuning-dataset, synthetic-data]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Finetuning Dataset: Claude Opus 4.6/4.7 - 8.7k Chats

HuggingFace 上發佈了包含 8,706 個合成示例的 Claude Opus 4.6/4.7 微調數據集，約 1,701 萬 token，涵蓋 28 個領域（編程、數學、人文、角色扮演等）。編程任務最多（1,628 例），多轮對話占 39.7%。該數據集來自 Claude 4.6（53.7%）與 4.7（46.3%）的合成數據，適合本地模型微調使用。

### 重點
- 數據集規模：8,706 例，1,701 萬 token，28 個領域類別
- 編程示例最多（1,628 例），多轮對話占 39.7%，平均 1,954 token/例
- 來源分布：Claude 4.6（4,675 例）與 4.7（4,031 例）合成

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t0l2c8/finetuning_dataset_claude_opus_4647_87k_chats/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p><a href="https://huggingface.co/datasets/angrygiraffe/claude-opus-4.6-4.7-reasoning-8.7k">https://huggingface.co/datasets/angrygiraffe/claude-opus-4.6-4.7-reasoning-8.7k</a></p> <p>A synthetic fine-tuning dataset created from Claude 4.6/4.7. 8,706 total examples all with reasoning. I haven't reviewed the data but there was some basic cleaning applied. Refusals and safety should be repressed. I ended up with extra usage on a plan before it expired.</p> <pre><code>| Split | File | Examples | Contents | |-------|------|---------:|----------| | **Full** | `full_train.jsonl` | 8,706 | All examples across all 28 categories. | | **Instruct** | `instruct_train.jsonl` | 7,217 | All 24 instructional categories — coding, math, sciences, humanities, arts, finance, medicine, law, business, linguistics, creative writing, general. | | **Roleplay** | `roleplay_train.jsonl` | 1,489 | The four creative categories — `roleplay_hero`, `roleplay_villain`, `roleplay_crossover`, `narrative_prose`. | | **Code** | `code_train.jsonl` | 1,840 | `coding` + `math` only. For coding/math-focused fine-tunes. | ## Overall | Metric | Value | |---|---:| | Examples | 8,706 | | Tokens (estimated) | 17,013,533 | | Avg tokens / example | 1,954 | | Multi-turn | 3,454 (39.7%) | | Single-turn | 5,252 (60.3%) | ## Category Counts | Category | Examples | Tokens | Multi-turn % | |----------|---------:|-------:|-------------:| | coding | 1,628 | 2,545,221 | 30.4% | | humanities | 862 | 1,849,708 | 32.5% | | science | 737 | 1,681,346 | 37.4% | | roleplay_hero | 419 | 640,084 | 63.5% | | roleplay_villain | 378 | 635,984 | 60.8% | | narrative_prose | 377 | 710,807 | 43.0% | | roleplay_crossover | 315 | 581,188 | 56.8% | | creative_writing | 281 | 532,504 | 30.6% | | medicine | 280 | 519,662 | 22.1% | | biology | 277 | 541,013 | 21.3% | | general | 276 | 284,696 | 37.0% | | arts | 245 | 576,170 | 41.2% | | chemistry | 221 | 508,546 | 52.9% | | physics | 220 | 512,196 | 56.8% | | math | 212 | 394,907 | 54.2% | | geography | 155 | 358,321 | 42.6% | | history | 155 | 348,822 | 41.3% | | economics | 155 | 380,372 | 42.6% | | political_science | 154 | 374,901 | 38.3% | | sociology | 154 | 378,261 | 42.2% | | business | 152 | 315,065 | 38.2% | | earth_science | 152 | 358,209 | 41.4% | | finance | 151 | 328,607 | 38.4% | | philosophy | 150 | 335,514 | 41.3% | | linguistics | 150 | 306,889 | 39.3% | | literature | 150 | 299,606 | 38.7% | | psychology | 150 | 339,565 | 39.3% | | law | 150 | 375,360 | 41.3% | ## By Model | Model | Count | Share | Tokens | |---|---:|---:|---:| | claude-opus-4-6 | 4,675 | 53.7% | 6,304,169 | | claude-opus-4-7 | 4,031 | 46.3% | 10,709,363 | </code></pre> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/AldebaranBefore"> /u/AldebaranBefore </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0l2c8/finetuning_dataset_claude_opus_4647_87k_chats/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0l2c8/finetuning_dataset_claude_opus_4647_87k_chats/">[comments]</a></span>

</details>