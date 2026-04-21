---
id: inbox_5a5cf9c8
date: 2026-04-15
source_ref: "[[00-inbox/.../inbox_5a5cf9c8]]"
title: "Gemini 3.1 Flash TTS"
url: https://simonwillison.net/2026/Apr/15/gemini-31-flash-tts/#atom-everything
source: simon-willison
published_at: 2026-04-15T17:13:14+00:00
fetched_at: 2026-04-21T03:14:54.586992+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 於 2026 年 4 月 15 日發布 Gemini 3.1 Flash TTS 文字轉語音模型，使用模型 ID `gemini-3.1-flash-tts-preview`，可透過標準 Gemini API 調用。該模型首創之處在於支援基於結構化提示的精細控制，用戶可在提示中詳細描述角色檔案（如「Jaz R. 來自倫敦布里克斯頓」）、場景設定、聲學風格要求（如「vocal smile」、高動態投射、快速交付）與口音指定，模型據此生成符合描述的語音。模型支援多角色對話模式，使用者可定義多個角色並分別指定不同的語音。原文示例展示了倫敦、紐卡斯爾、德文郡等多種英國區域口音的輸出能力。模型目前限制為只輸出音訊檔案。Simon Willison 並開發了網頁版 UI 方便使用者試驗。"
key_points:
  - "模型 ID：`gemini-3.1-flash-tts-preview`，需透過標準 Gemini API 呼叫，音訊輸出專用"
  - "支援多角色對話模式且口音精確可控：示例展示倫敦、紐卡斯爾、德文郡等區域口音的差異"
  - "提示引導極為詳細：包含 AUDIO PROFILE、THE SCENE、DIRECTOR'S NOTES、SAMPLE CONTEXT 等多層次結構化描述，精細控制聲調、節奏、角色情境"
tags: [gemini, text-to-speech, prompt-engineering, google, api-release]
topics: []
importance: 4
novelty: 5
deep_dive_candidate: false
deep_dive_approved: false
---

## Gemini 3.1 Flash TTS

Google 於 2026 年 4 月 15 日發布 Gemini 3.1 Flash TTS 文字轉語音模型，使用模型 ID `gemini-3.1-flash-tts-preview`，可透過標準 Gemini API 調用。該模型首創之處在於支援基於結構化提示的精細控制，用戶可在提示中詳細描述角色檔案（如「Jaz R. 來自倫敦布里克斯頓」）、場景設定、聲學風格要求（如「vocal smile」、高動態投射、快速交付）與口音指定，模型據此生成符合描述的語音。模型支援多角色對話模式，使用者可定義多個角色並分別指定不同的語音。原文示例展示了倫敦、紐卡斯爾、德文郡等多種英國區域口音的輸出能力。模型目前限制為只輸出音訊檔案。Simon Willison 並開發了網頁版 UI 方便使用者試驗。

### 重點
- 模型 ID：`gemini-3.1-flash-tts-preview`，需透過標準 Gemini API 呼叫，音訊輸出專用
- 支援多角色對話模式且口音精確可控：示例展示倫敦、紐卡斯爾、德文郡等區域口音的差異
- 提示引導極為詳細：包含 AUDIO PROFILE、THE SCENE、DIRECTOR'S NOTES、SAMPLE CONTEXT 等多層次結構化描述，精細控制聲調、節奏、角色情境

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/15/gemini-31-flash-tts/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Gemini 3.1 Flash TTS

<p><strong><a href="https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-1-flash-tts/">Gemini 3.1 Flash TTS</a></strong></p>
Google released Gemini 3.1 Flash TTS today, a new text-to-speech model that can be directed using prompts.</p>
<p>It's presented via the standard Gemini API using <code>gemini-3.1-flash-tts-preview</code> as the model ID, but can only output audio files.</p>
<p>The <a href="https://ai.google.dev/gemini-api/docs/speech-generation#transcript-tags">prompting guide</a> is surprising, to say the least. Here's their example prompt to generate just a few short sentences of audio:</p>
<pre><code># AUDIO PROFILE: Jaz R.
## "The Morning Hype"

## THE SCENE: The London Studio
It is 10:00 PM in a glass-walled studio overlooking the moonlit London skyline, but inside, it is blindingly bright. The red "ON AIR" tally light is blazing. Jaz is standing up, not sitting, bouncing on the balls of their heels to the rhythm of a thumping backing track. Their hands fly across the faders on a massive mixing desk. It is a chaotic, caffeine-fueled cockpit designed to wake up an entire nation.

### DIRECTOR'S NOTES
Style:
* The "Vocal Smile": You must hear the grin in the audio. The soft palate is always raised to keep the tone bright, sunny, and explicitly inviting.
* Dynamics: High projection without shouting. Punchy consonants and elongated vowels on excitement words (e.g., "Beauuutiful morning").

Pace: Speaks at an energetic pace, keeping up with the fast music.  Speaks with A "bouncing" cadence. High-speed delivery with fluid transitions — no dead air, no gaps.

Accent: Jaz is from Brixton, London

### SAMPLE CONTEXT
Jaz is the industry standard for Top 40 radio, high-octane event promos, or any script that requires a charismatic Estuary accent and 11/10 infectious energy.

#### TRANSCRIPT
[excitedly] Yes, massive vibes in the studio! You are locked in and it is absolutely popping off in London right now. If you're stuck on the tube, or just sat there pretending to work... stop it. Seriously, I see you.
[shouting] Turn this up! We've got the project roadmap landing in three, two... let's go!
</code></pre>
<p>Here's what I got using that example prompt:</p>
<p><audio controls="controls" style="width: 100%;">
  <source src="https://static.simonwillison.net/static/2026/gemini-flash-tts-london.wav" type="audio/wav" />
  Your browser does not support the audio element.
</audio></p>
<p>Then I modified it to say "Jaz is from Newcastle" and "... requires a charismatic Newcastle accent" and got this result:</p>
<p><audio controls="controls" style="width: 100%;">
  <source src="https://static.simonwillison.net/static/2026/gemini-flash-tts-newcastle.wav" type="audio/wav" />
  Your browser does not support the audio element.
</audio></p>
<p>Here's Exeter, Devon for good measure:</p>
<p><audio controls="controls" style="width: 100%;">
  <source src="https://static.simonwillison.net/static/2026/gemini-flash-tts-devon.wav" type="audio/wav" />
  Your browser does not support the audio element.
</audio></p>
<p>I <a href="https://gemini.google.com/share/dd0fba5a83c4">had Gemini 3.1 Pro</a> vibe code <a href="https://tools.simonwillison.net/gemini-flash-tts">this UI for trying it out</a>:</p>
<p><img alt="Screenshot of a &quot;Gemini 3.1 Flash TTS&quot; web application interface. At the top is an &quot;API Key&quot; field with a masked password. Below is a &quot;TTS Mode&quot; section with a dropdown set to &quot;Multi-Speaker (Conversation)&quot;. &quot;Speaker 1 Name&quot; is set to &quot;Joe&quot; with &quot;Speaker 1 Voice&quot; set to &quot;Puck (Upbeat)&quot;. &quot;Speaker 2 Name&quot; is set to &quot;Jane&quot; with &quot;Speaker 2 Voice&quot; set to &quot;Kore (Firm)&quot;. Under &quot;Script / Prompt&quot; is a tip reading &quot;Tip: Format your text as a script using the Exact Speaker Names defined above.&quot; The script text area contains &quot;TTS the following conversation between Joe and Jane:\n\nJoe: How's it going today Jane?\nJane: [yawn] Not too bad, how about you?&quot; A blue &quot;Generate Audio&quot; button is below. At the bottom is a &quot;Success!&quot; message with an audio player showing 00:00 / 00:06 and a &quot;Download WAV&quot; link." src="https://static.simonwillison.net/static/2026/gemini-flash-tts.jpg" />


    <p>Tags: <a href="https://simonwillison.net/tags/google">google</a>, <a href="https://simonwillison.net/tags/text-to-speech">text-to-speech</a>, <a href="https://simonwillison.net/tags/tools">tools</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/prompt-engineering">prompt-engineering</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/gemini">gemini</a>, <a href="https://simonwillison.net/tags/llm-release">llm-release</a>, <a href="https://simonwillison.net/tags/vibe-coding">vibe-coding</a></p>

</details>