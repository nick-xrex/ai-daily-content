---
id: inbox_fbc59bf5
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_fbc59bf5]]"
title: "Common and Obscure Models and Ways to Find Them [ Human Written ]"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t4vmgu/common_and_obscure_models_and_ways_to_find_them/
source: reddit-localllama
published_at: 2026-05-05T23:11:18+00:00
fetched_at: 2026-05-06T13:25:41.572783+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "社群使用者彙整了本地 AI 工具和模型的發現清單，包括常見應用（Applio 語音轉換、Ultimate-TTS-Studio 文本轉語音、Open Web UI 桌面版）、較少提及的工具（ComfyUI 流程管理、Ultimate Vocal Remover 人聲分離、OpenASR Leaderboard 語音識別）和冷門應用（Spotify Basic Pitch 音樂轉 MIDI、Meetily 實時字幕）。並提出了發現方法論（GitHub Tags 按主題搜尋、AlternativeTo 尋找開源替代品）以及尚未發現理想方案的功能缺口（批量轉錄管道、語音編輯、統一搜尋前端等）。"
key_points:
  - "彙整 20+ 本地 AI 應用並指出 Whisper 在長文本中的幻覺問題，推薦 Parakeet 0.6b / VibeVoice / CohereTranscribe 為更精確替代品"
  - "明確指出市場空白：Ollama 等通用 LLM 框架已成熟，但音訊處理、影片編輯、批量轉錄等領域缺乏整合方案，類似「LLM 之於文本」的統一工具"
  - "提供了發現方法的實踐清單（GitHub Tags、AlternativeTo、Hugging Face Leaderboards），可幫助開發者系統性探索開源生態"
tags: [local-ai-tools, voice-processing, audio-ml, tool-discovery, ecosystem-gaps]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Common and Obscure Models and Ways to Find Them [ Human Written ]

社群使用者彙整了本地 AI 工具和模型的發現清單，包括常見應用（Applio 語音轉換、Ultimate-TTS-Studio 文本轉語音、Open Web UI 桌面版）、較少提及的工具（ComfyUI 流程管理、Ultimate Vocal Remover 人聲分離、OpenASR Leaderboard 語音識別）和冷門應用（Spotify Basic Pitch 音樂轉 MIDI、Meetily 實時字幕）。並提出了發現方法論（GitHub Tags 按主題搜尋、AlternativeTo 尋找開源替代品）以及尚未發現理想方案的功能缺口（批量轉錄管道、語音編輯、統一搜尋前端等）。

### 重點
- 彙整 20+ 本地 AI 應用並指出 Whisper 在長文本中的幻覺問題，推薦 Parakeet 0.6b / VibeVoice / CohereTranscribe 為更精確替代品
- 明確指出市場空白：Ollama 等通用 LLM 框架已成熟，但音訊處理、影片編輯、批量轉錄等領域缺乏整合方案，類似「LLM 之於文本」的統一工具
- 提供了發現方法的實踐清單（GitHub Tags、AlternativeTo、Hugging Face Leaderboards），可幫助開發者系統性探索開源生態

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t4vmgu/common_and_obscure_models_and_ways_to_find_them/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Common and Obscure Models and Ways to Find Them [ Human Written ]

<!-- SC_OFF --><div class="md"><p>I've been on a binge finding uses for local AI on my machine outside of general LLM usage as I'm not sure what other sub discovery of these things should go on. Here's a collection of my findings. </p> <p>I'd appreciate other contributions that are off the beaten path or collections.</p> <h1>Somewhat &quot;common&quot; apps / models</h1> <p><a href="https://applio.org/"><strong>Applio</strong></a></p> <p>invaluable voice to voice translation app. Was quite easy to find a voice online and map it from one to another. Used it to clean up some crappy lecture recordings. What you use if you want to make a recording sound like Obama.</p> <p><a href="https://github.com/SUP3RMASS1VE/Ultimate-TTS-Studio-SUP3R-Edition"><strong>Ultimate-TTS-Studio</strong></a></p> <p>great for converting any sort of text into audio using a variety of locally running models. Things like transcripts to ebooks. Comes with good tools to parse certain upload types. Used it to make an audiobook out of an EPUB.</p> <p><a href="https://github.com/open-webui/desktop"><strong>Open Web UI</strong></a></p> <p>I know lots of people use this, but there's also a Desktop version in beta. I hate running containers or severs or what have you so this eases a lot of the headache.</p> <p>There are also settings that allow you to use TTS models and STT models so you can have a vocal conversational experience.</p> <p><a href="https://pinokio.co/"><strong>Pinokio</strong></a></p> <p>A good hosting program for a bunch of AI apps. Good for if you want to just click, try something out, and then dip. Irritating though as lots of apps crash. Look for something with a high amount of checkins. Also a good interface for running Open Web UI.</p> <p><a href="https://handy.computer/"><strong>Handy</strong></a></p> <p>easy speech to text for vocal transcription.</p> <h1>Apps / Models I've seen less mentioned</h1> <p><a href="https://www.comfy.org/"><strong>ComfyUI</strong></a></p> <p>Seems like a model pipeline manager, I just can't understand the ecosystem enough to use it with local models. I'm not sure if I have to do a lot of installation myself or how its plugin architecture works. Whenever I look at external plugins they seem to mostly be in chinese w/ english translations and have fewer stars than normal so I'm never sure if I'm doing the right thing. Spent an hour on it.</p> <p><a href="https://ultimatevocalremover.com/"><strong>Ultimate Vocal Remover</strong></a></p> <p>this one is good but a PITA. You have to look at your system monitor to see that it's actually using the GPU and you have to install the latest BETA from the site. The settings are also convoluted. Fails silently a lot.</p> <p><a href="https://github.com/Zackriya-Solutions/meetily"><strong>Meetily - Oddly hard to find closed caption model.</strong></a></p> <p>You'd think this would be the first thing people would use STT for, but oddly it's hard to find something realtime. Handy is more for text input rather than closed captioning.</p> <p><a href="https://github.com/modelscope/ClearerVoice-Studio/"><strong>Voice Upscaling</strong></a></p> <p>Neat package for voice upscaling, but I feel like something better ought to exist.</p> <p><a href="https://huggingface.co/spaces/hf-audio/open_asr_leaderboard"><strong>Long Form Speech Transcription</strong></a></p> <p>Parakeet 0.6b / VibeVoice / CohereTranscribe<br /> I don't know why people keep touting whisper. These are more accurate, hallucinate less, and or run faster, or provide more features ( speaker tagging and voice activation ). Feels like GIMP vs. Krita. Whisper hallucinates because it's train off Youtube data.</p> <p>It's odd that more leaderboards on hugging face aren't posted here. Oddly I feel as though most ASR frontends are geared towards smaller things.</p> <h1>Obscure Examples</h1> <p><a href="https://github.com/spotify/basic-pitch"><strong>Audio to Midi</strong></a></p> <p>Takes music, generates a midi file</p> <p><a href="https://github.com/skier233/nsfw_ai_model_server"><strong>Goon tagging</strong></a></p> <p>Porn classification.</p> <p><a href="https://murtaza-nasir.github.io/speakr/"><strong>Speakr - Seems to require a lot of config as well</strong></a></p> <p>Might need a separate compose setup to spin it up with corresponding models and take it down. For OCD note taking essentially.</p> <h1>Things I've been looking for</h1> <p><strong>Gallery to slideshow</strong></p> <p>I've found this feature a lot in google photos and Samsung gallery. Something like an AMV generator like the old 2000s youtube channels would ma</p> <p><strong>AI video editing</strong></p> <p>Something where I can put in clips and it gives me processing options. Things like action tagging, topic transitions, silence and vocal activity, etc.</p> <p><strong>Voice Cloning -&gt; singing :</strong></p> <p>Applio seems great for that but I'm figuring out how to &quot;train&quot; a voice in the format it requires. I'd be nice to have a tool that uses 30 second one shots like other tools, but I don't know if that'll reduce quality.</p> <p><strong>Speech editing</strong></p> <p>I've had lots of recorded audio where I'd like to get a transcript and re-type a part of my speech to make it seem natural without having to re-record.</p> <p><strong>Good image / video / text search front-end</strong></p> <p>I just want to tag and organize things ideally through embeddings where possible. Just something I can double click, configure, and point at a folder.</p> <p><strong>Spoken Audio Cleanup</strong></p> <p>Also oddly hard to find? There are stem separation tools, but it feels like this needs its own unique pipeline. Not sure which models are best for this.</p> <p><strong>Batch transcription front-end with cleanup pipeline</strong></p> <p>Something that can go Audio cleanup -&gt; voice activation -&gt; asr -&gt; transcription -&gt; output format ideally but anything with batch transcription would be great. Odd that this doesn't exist.</p> <p><strong>Generally the &quot;Ollama&quot; for other means</strong></p> <p>General AI packages and pipelines for things like audio production, conversation analysis, etc.</p> <h1>Discovery Methods</h1> <p><a href="https://repositorystats.com/topics"><strong>Github Tags</strong></a></p> <p>Searching through AI related repository stats</p> <ul> <li>local-ai, speech-to-text, semantic-search, speech-enhancement</li> </ul> <p>** Alternative To ** <a href="https://alternativeto.net/">https://alternativeto.net/</a> Used to find open source alternatives to popular software</p> <p>If you have any suggestions to discovery methods, obscure models, or other comprehensive model packaging tools I'd appreciate you sharing them! Ideally things with</p> <ul> <li>decent communities</li> <li>more recent / capable models</li> <li>alternatives to popular paid tools.</li> </ul> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/iMakeSense"> /u/iMakeSense </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4vmgu/common_and_obscure_models_and_ways_to_find_them/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4vmgu/common_and_obscure_models_and_ways_to_find_them/">[comments]</a></span>

</details>