---
id: inbox_23f14daf
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t2pisc/built_a_voice_agents_from_scratch_github_tutorial/"
author: "/u/purellmagents"
published_at: 2026-05-03T16:06:28+00:00
fetched_at: 2026-05-04T13:38:38.132318+00:00
content_hash: "42a7e1b09a798e6bbdbdd7b7ccde8d4231e0b8cdc26253e78f8d09e5134b5a0d"
lang: en
caption_quality: None
raw: true
topics: []
---

# Built a Voice Agents from Scratch GitHub tutorial: mic > Whisper > local LLM (GGUF) > Kokoro > speaker, fully local, no API keys

<!-- SC_OFF --><div class="md"><p>Been building this for a while and finally cleaned it up enough to share.</p> <p><strong>voice-agents-from-scratch</strong> is a numbered, chapter-by-chapter repo that walks the full real-time pipeline:</p> <ul> <li>Microphone capture</li> <li>Whisper for STT</li> <li>Local GGUF LLM (via llama.cpp)</li> <li>Kokoro for TTS</li> <li>Speaker output</li> </ul> <p>Everything streams - you don't wait for the full LLM response before TTS starts speaking. That's the part that makes it feel like a real conversation instead of a chatbot with a voice skin.</p> <p>Chapters:</p> <ol> <li>Intro</li> <li>Audio IO</li> <li>Speech to Text (STT)</li> <li>Text to Speech (TTS)</li> <li>Full voice loop</li> <li>Real time systems</li> <li>Tools</li> <li>Personality</li> <li>Projects</li> </ol> <p>Each chapter is a runnable script + a short <a href="http://CODE.md">CODE.md</a> walkthrough. There's also a small shared library so you can see how the pieces compose into a real system, not just isolated calls.</p> <p><strong>Why fully local matters here:</strong> you can actually see where latency lives. Warm-up, first-audio time, streaming chunk size - these aren't abstractions when you're running it on your own machine.</p> <p>I plan a deployment chapter, thinking of using <a href="http://modal.com">modal.com</a> for it, wishes and suggestions are welcome.</p> <p>Repo: <a href="https://github.com/pguso/voice-agents-from-scratch">https://github.com/pguso/voice-agents-from-scratch</a></p> <p>I originally wanted to publish this repo using Node.js, but the ecosystem in Node.js is really not ready. There is a very good Kokoro-JS npm package, but when it comes to Whisper support or audio processing in general there are no good options.</p> <p>Happy to answer questions about the architecture or tradeoffs I ran into.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/purellmagents"> /u/purellmagents </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2pisc/built_a_voice_agents_from_scratch_github_tutorial/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2pisc/built_a_voice_agents_from_scratch_github_tutorial/">[comments]</a></span>