---
id: inbox_7075bc02
date: 2026-04-27
source_ref: "[[00-inbox/2026-04-27/0248-simon-willison-microsoft-vibevoice-9983]]"
title: "microsoft/VibeVoice"
url: https://simonwillison.net/2026/Apr/27/vibevoice/#atom-everything
source: simon-willison
published_at: 2026-04-27T23:46:56+00:00
fetched_at: 2026-04-28T02:53:57.489666+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Microsoft 於 2026 年 1 月發布 VibeVoice，MIT 許可的開源語音轉文本模型，內置多說話人辨別。Simon Willison 測試在 128GB M5 Max MacBook Pro 上，使用 5.71GB MLX 4-bit 量化版本，轉錄 1 小時播客用時 8 分 45 秒。峰值記憶體 30.44GB，提示詞階段 50.718 tokens/sec，生成速率 38.585 tokens/sec。輸出為結構化 JSON 格式，含精確時間戳和 speaker_id。支援 .wav 和 .mp3 檔案，單次最多處理 1 小時音頻（預設 --max-tokens 8192 對應約 25 分鐘），超長音頻需分段處理。"
key_points:
  - "MIT 開源許可，支援本地運行的多說話人辨別語音轉文本，與 MLX 蘋果矽生態整合"
  - "M5 Max MacBook Pro (128GB) 上轉錄 1 小時播客：8 分 45 秒，峰值記憶體 30.44GB，生成速率 38.585 tokens/sec"
  - "提供 5.71GB MLX 4-bit 量化版本，輸出結構化 JSON 含精確時間戳和說話人 ID，單次最多 1 小時音頻"
tags: [microsoft-vibevoice, speech-to-text, mlx-quantization, speaker-diarization, open-source]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## microsoft/VibeVoice

Microsoft 於 2026 年 1 月發布 VibeVoice，MIT 許可的開源語音轉文本模型，內置多說話人辨別。Simon Willison 測試在 128GB M5 Max MacBook Pro 上，使用 5.71GB MLX 4-bit 量化版本，轉錄 1 小時播客用時 8 分 45 秒。峰值記憶體 30.44GB，提示詞階段 50.718 tokens/sec，生成速率 38.585 tokens/sec。輸出為結構化 JSON 格式，含精確時間戳和 speaker_id。支援 .wav 和 .mp3 檔案，單次最多處理 1 小時音頻（預設 --max-tokens 8192 對應約 25 分鐘），超長音頻需分段處理。

### 重點
- MIT 開源許可，支援本地運行的多說話人辨別語音轉文本，與 MLX 蘋果矽生態整合
- M5 Max MacBook Pro (128GB) 上轉錄 1 小時播客：8 分 45 秒，峰值記憶體 30.44GB，生成速率 38.585 tokens/sec
- 提供 5.71GB MLX 4-bit 量化版本，輸出結構化 JSON 含精確時間戳和說話人 ID，單次最多 1 小時音頻

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/27/vibevoice/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://github.com/microsoft/VibeVoice">microsoft/VibeVoice</a></strong></p>
VibeVoice is Microsoft's Whisper-style audio model for speech-to-text, MIT licensed and with speaker diarization built into the model.</p>
<p>Microsoft released it on January 21st, 2026 but I hadn't tried it until today. Here's a one-liner to run it on a Mac with <code>uv</code>, <a href="https://github.com/Blaizzy/mlx-audio">mlx-audio</a> (by Prince Canuma) and the 5.71GB <a href="https://huggingface.co/mlx-community/VibeVoice-ASR-4bit">mlx-community/VibeVoice-ASR-4bit</a> MLX conversion of the <a href="https://huggingface.co/microsoft/VibeVoice-ASR/tree/main">17.3GB VibeVoice-ASR</a> model, in this case against a downloaded copy of my recent <a href="https://simonwillison.net/2026/Apr/2/lennys-podcast/">podcast appearance with Lenny Rachitsky</a>:</p>
<pre><code>uv run --with mlx-audio mlx_audio.stt.generate \
  --model mlx-community/VibeVoice-ASR-4bit \
  --audio lenny.mp3 --output-path lenny \
  --format json --verbose --max-tokens 32768
</code></pre>
<p><img alt="Screenshot of a macOS terminal running an mlx-audio speech-to-text command using the VibeVoice-ASR-4bit model on lenny.mp3, showing download progress, a warning that audio duration (99.8 min) exceeds the 59 min maximum so it's trimming, encoding/prefilling/generating progress bars, then a Transcription section with JSON segments of speakers discussing AI coding agents, followed by stats: Processing time 524.79 seconds, Prompt 26615 tokens at 50.718 tokens-per-sec, Generation 20248 tokens at 38.585 tokens-per-sec, Peak memory 30.44 GB." src="https://static.simonwillison.net/static/2026/vibevoice-terminal.jpg" /></p>
<p>The tool reported back:</p>
<pre><code>Processing time: 524.79 seconds
Prompt: 26615 tokens, 50.718 tokens-per-sec
Generation: 20248 tokens, 38.585 tokens-per-sec
Peak memory: 30.44 GB
</code></pre>
<p>So that's 8 minutes 45 seconds for an hour of audio (running on a 128GB M5 Max MacBook Pro).</p>
<p>I've tested it against <code>.wav</code> and <code>.mp3</code> files and they both worked fine.</p>
<p>If you omit <code>--max-tokens</code> it defaults to 8192, which is enough for about 25 minutes of audio. I discovered that through trial-and-error and quadrupled it to guarantee I'd get the full hour.</p>
<p>That command reported using 30.44GB of RAM at peak, but in Activity Monitor I observed 61.5GB of usage during the prefill stage and around 18GB during the generating phase.</p>
<p>Here's <a href="https://gist.github.com/simonw/d2c716c008b3ba395785f865c6387b6f">the resulting JSON</a>. The key structure looks like this:</p>
<pre><code>{
  "text": "And an open question for me is how many other knowledge work fields are actually prone to these agent loops?",
  "start": 13.85,
  "end": 19.5,
  "duration": 5.65,
  "speaker_id": 0
},
{
  "text": "Now that we have this power, people almost underestimate what they can do with it.",
  "start": 19.5,
  "end": 22.78,
  "duration": 3.280000000000001,
  "speaker_id": 1
},
{
  "text": "Today, probably 95% of the code that I produce, I didn't type it myself. I write so much of my code on my phone. It's wild.",
  "start": 22.78,
  "end": 30.0,
  "duration": 7.219999999999999,
  "speaker_id": 0
}
</code></pre>
<p>Since that's an array of objects we can <a href="https://lite.datasette.io/?json=https://gist.github.com/simonw/d2c716c008b3ba395785f865c6387b6f#/data/raw?_facet=speaker_id">open it in Datasette Lite</a>, making it easier to browse.</p>
<p>Amusingly that Datasette Lite view shows three speakers - it identified Lenny and me for the conversation, and then a separate Lenny for the voice he used for the additional intro and the sponsor reads!</p>
<p>VibeVoice can only handle up to an hour of audio, so running the above command transcribed just the first hour of the podcast. To transcribe more than that you'd need to split the audio, ideally with a minute or so of overlap so you can avoid errors from partially transcribed words at the split point. You'd also need to then line up the identified speaker IDs across the multiple segments.


    <p>Tags: <a href="https://simonwillison.net/tags/microsoft">microsoft</a>, <a href="https://simonwillison.net/tags/python">python</a>, <a href="https://simonwillison.net/tags/datasette-lite">datasette-lite</a>, <a href="https://simonwillison.net/tags/uv">uv</a>, <a href="https://simonwillison.net/tags/mlx">mlx</a>, <a href="https://simonwillison.net/tags/prince-canuma">prince-canuma</a>, <a href="https://simonwillison.net/tags/speech-to-text">speech-to-text</a></p>

</details>