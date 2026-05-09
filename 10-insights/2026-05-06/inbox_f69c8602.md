---
id: inbox_f69c8602
date: 2026-05-06
source_ref: "[[00-inbox/.../inbox_f69c8602]]"
title: "Kindergarten-grade nouns"
url: https://www.reddit.com/r/ClaudeAI/comments/1t5dfjn/kindergartengrade_nouns/
source: reddit-claudeai
published_at: 2026-05-06T13:46:47+00:00
fetched_at: 2026-05-09T02:54:48.957642+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "技術分析揭示 Claude Opus 在詞彙頻率認知上的系統性盲點。用戶利用 Opus 開發詞彙遊戲時發現，Opus 無法區分「幼稚園習得但成人少寫」的詞彙（STETHOSCOPE、CAMPANILE、AGAVE）與真正罕見詞彙；複數/屈折形式（PLAYBILLS vs. PLAYBOOK）與領域常識詞（OXTAIL、RHYOLITE、MIMULUS）亦被嚴重低估。根本原因在於訓練語料庫（Wikipedia、新聞、字幕、Reddit、Twitter）過度代表現代網路寫作，系統性低權重化「學校習得但不常網路寫作」的知識詞彙。"
key_points:
  - "Zipf 頻率測度與人類認知熟悉度存在根本差異；Opus 依賴頻率但不理解文化習得"
  - "複數形式、屈折變化、領域常識詞彙在網路語料庫中嚴重低估"
  - "訓練語料庫偏差：現代網路寫作 > 學校知識，導致詞彙認知失真"
tags: [language-models, vocabulary-bias, training-data, claude-opus]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Kindergarten-grade nouns

技術分析揭示 Claude Opus 在詞彙頻率認知上的系統性盲點。用戶利用 Opus 開發詞彙遊戲時發現，Opus 無法區分「幼稚園習得但成人少寫」的詞彙（STETHOSCOPE、CAMPANILE、AGAVE）與真正罕見詞彙；複數/屈折形式（PLAYBILLS vs. PLAYBOOK）與領域常識詞（OXTAIL、RHYOLITE、MIMULUS）亦被嚴重低估。根本原因在於訓練語料庫（Wikipedia、新聞、字幕、Reddit、Twitter）過度代表現代網路寫作，系統性低權重化「學校習得但不常網路寫作」的知識詞彙。

### 重點
- Zipf 頻率測度與人類認知熟悉度存在根本差異；Opus 依賴頻率但不理解文化習得
- 複數形式、屈折變化、領域常識詞彙在網路語料庫中嚴重低估
- 訓練語料庫偏差：現代網路寫作 > 學校知識，導致詞彙認知失真

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t5dfjn/kindergartengrade_nouns/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Kindergarten-grade nouns

 I've been working with Opus on a web app for a word game, and recently I've been trying to get a rating on how obscure various words are (not by Claude itself, through existing corpuses). Based on the following interaction, I realized that Opus has absolutely no clue what's normal vocabulary for a human: You're right, and the diagnosis is straightforward: Zipf measures production frequency (how often people write/say words), but what you actually want is recognition / familiarity (do most adults know what this word means). Those diverge dramatically for: Recognized but rarely written : STETHOSCOPE, CAMPANILE, AGAVE — kindergarten-grade nouns for things adults rarely type about. Plurals/inflections of familiar words : PLAYBILLS, GROTTOES, CRUNCHES — the singular is everyday, the plural form barely shows up. Domain words people know but don't use : OXTAIL, RHYOLITE, MIMULUS — gardening, geology, biology common-knowledge. wordfreq's corpus (Wikipedia + news + subtitles + Reddit + Twitter) is heavily slanted toward modern internet/news prose. It systematically underweights &quot;things you learned in school but don't post about.&quot; &#32; submitted by &#32; /u/babelphishy [link] &#32; [comments]

</details>