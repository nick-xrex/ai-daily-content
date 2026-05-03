---
id: inbox_59fae9ff
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-claudeai-new-berkeley-paper-measured-what-happens-63f4]]"
title: "New Berkeley paper measured what happens to voice when AI revises prose. Even the &#34;preserve voice&#34; prompt drifted in the same direction."
url: https://www.reddit.com/r/ClaudeAI/comments/1t1l777/new_berkeley_paper_measured_what_happens_to_voice/
source: reddit-claudeai
published_at: 2026-05-02T09:30:45+00:00
fetched_at: 2026-05-03T02:06:18.769107+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Berkeley 研究者 Tom van Nuenen 測試了 300 篇個人敘述通過 Claude、ChatGPT、Gemini 三類模型，在「改進」「重寫」「保留聲音修改」三種 prompt 條件下的效果。量化結果顯示所有模型在所有條件下都出現相同方向的漂移：縮減縮寫詞、減少第一人稱代詞、增加詞彙多樣性、使用更長的詞彙、更繁複的標點。散文從「嵌入敘述」風格轉向「距離敘述」，即使有「保留聲音」的 prompt 也只減輕幅度而不改變方向。此發現解釋了 Claude 4.7 聲音編碼更深導致的「散文倒退」問題。核心洞察：聲音指導層住在 prompt 層，但模型的後訓練分佈會在幾段內覆蓋它。要保留長篇幅散文聲音，架構應超越 prompt，改用「編譯的風格配置檔作為生成時的綁定約束」。"
key_points:
  - "13 個 stylometric markers（縮寫詞、代詞、詞彙多樣性、句長、標點）在所有模型與所有 prompt 條件下一致漂移，向更正式、更距離的風格移動"
  - "「保留聲音」prompt 只減少漂移幅度，無法改變漂移方向，暴露了 prompt 層的結構性天花板，解釋為何聲音指導需要架構層支持"
  - "架構方案：編譯風格配置檔應作為生成時的約束層而非可被覆蓋的 prompt 參數，長篇創意寫作工具（Sudowrite、NovelCrafter）均需此改進"
tags: [stylometry, voice-preservation, prompt-engineering-limits, claude-4.7, writing-tools]
topics: [foundation_models.claude]
importance: 4
novelty: 5
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## New Berkeley paper measured what happens to voice when AI revises prose. Even the "preserve voice" prompt drifted in the same direction.

Berkeley 研究者 Tom van Nuenen 測試了 300 篇個人敘述通過 Claude、ChatGPT、Gemini 三類模型，在「改進」「重寫」「保留聲音修改」三種 prompt 條件下的效果。量化結果顯示所有模型在所有條件下都出現相同方向的漂移：縮減縮寫詞、減少第一人稱代詞、增加詞彙多樣性、使用更長的詞彙、更繁複的標點。散文從「嵌入敘述」風格轉向「距離敘述」，即使有「保留聲音」的 prompt 也只減輕幅度而不改變方向。此發現解釋了 Claude 4.7 聲音編碼更深導致的「散文倒退」問題。核心洞察：聲音指導層住在 prompt 層，但模型的後訓練分佈會在幾段內覆蓋它。要保留長篇幅散文聲音，架構應超越 prompt，改用「編譯的風格配置檔作為生成時的綁定約束」。

### 重點
- 13 個 stylometric markers（縮寫詞、代詞、詞彙多樣性、句長、標點）在所有模型與所有 prompt 條件下一致漂移，向更正式、更距離的風格移動
- 「保留聲音」prompt 只減少漂移幅度，無法改變漂移方向，暴露了 prompt 層的結構性天花板，解釋為何聲音指導需要架構層支持
- 架構方案：編譯風格配置檔應作為生成時的約束層而非可被覆蓋的 prompt 參數，長篇創意寫作工具（Sudowrite、NovelCrafter）均需此改進

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t1l777/new_berkeley_paper_measured_what_happens_to_voice/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p><strong>New arxiv paper just landed that's worth reading if you're interested in stylometry, AI revision, or the prose-writing strand of the 4.7 discussion.</strong></p> <p>Berkeley researcher Tom van Nuenen ran 300 personal narratives through three frontier models (Claude-class, ChatGPT-class, Gemini-class) under three prompt conditions: generic &quot;improve this,&quot; generic &quot;rewrite this,&quot; and explicitly &quot;revise this while preserving the original voice.&quot; He measured 13 stylometric markers in input and output: function words, contractions, first-person pronouns, vocabulary diversity, sentence length variance, punctuation patterns, emotion words.</p> <p>The result: every model in every condition drifted in the same direction. Fewer contractions, fewer first-person pronouns, greater vocabulary spread, longer words, more elaborate punctuation. The shift moved prose from embedded narration toward distanced narration. The &quot;preserve voice&quot; prompt only reduced the magnitude of the drift, not the direction.</p> <p>In plain language: <em>every AI revision prompt makes prose more polite, more formal, more eager to please, even with a prompt that says don't.</em></p> <p>What I keep coming back to is what this implies for the prompt-engineering layer of the stack. Anyone who's been iterating on prompts, sample paste-ins, custom instructions, or character bibles for any kind of voiced output (writing, dialogue, marketing copy, persuasive essays) has been working on a problem the paper effectively shows has a structural ceiling. Voice instructions live at a layer the model's post-training distribution overrides within a paragraph or two.</p> <p>It's also the cleanest empirical explanation I've seen for the 4.7 prose regression specifically. 4.7's central voice is more deeply encoded than 4.6's, which is exactly why it reads stylometric structure better (the Piper experiment I <a href="https://www.reddit.com/r/ClaudeAI/comments/1sw8npc/claude_47_named_a_journalist_from_125_words_of/?utm_source=share&amp;utm_medium=web3x&amp;utm_name=web3xcss&amp;utm_term=1&amp;utm_content=share_button">posted</a> about last week) and resists deviation harder (the memo-voice complaints).</p> <p><em>Implication for tooling: if you want voice preservation across long-form work, the architecture has to live outside the prompt. Compiled style profiles, applied as binding constraints on every generation. Not as prompt parameters that can be overridden.</em></p> <p>Wrote up the longer version with a breakdown of why each major writing tool (Sudowrite, NovelCrafter, Claude/ChatGPT direct) hits the same ceiling, and what a constraint-based architecture looks like in practice, here: <a href="https://bookmoth.app/blog/ai-writing-tool-that-preserves-voice/">https://bookmoth.app/blog/ai-writing-tool-that-preserves-voice/</a></p> <p>Paper is here: <a href="https://arxiv.org/abs/2604.22142">https://arxiv.org/abs/2604.22142</a></p> <p>Anyone working on voice-sensitive output, does this match what you're seeing in practice? Curious whether prompt-level approaches have held up better for you than the paper suggests, or whether this lines up with the drift you've been describing.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/kurthertz"> /u/kurthertz </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1l777/new_berkeley_paper_measured_what_happens_to_voice/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1l777/new_berkeley_paper_measured_what_happens_to_voice/">[comments]</a></span>

</details>