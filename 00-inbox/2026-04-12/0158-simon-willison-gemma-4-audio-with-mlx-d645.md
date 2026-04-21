---
id: inbox_e18ce8ad
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Apr/12/mlx-audio/#atom-everything"
author: ""
published_at: 2026-04-12T23:57:53+00:00
fetched_at: 2026-04-21T01:58:22.536572+00:00
content_hash: "d645f7214dde4282c56187490770078355e7958011b1efd685b8c53bc8b12539"
lang: en
caption_quality: None
raw: true
topics: []
---

# Gemma 4 audio with MLX

<p>Thanks to a <a href="https://twitter.com/RahimNathwani/status/2039961945613209852">tip from Rahim Nathwani</a>, here's a <code>uv run</code> recipe for transcribing an audio file on macOS using the 10.28 GB <a href="https://huggingface.co/google/gemma-4-E2B">Gemma 4 E2B model</a> with MLX and <a href="https://github.com/Blaizzy/mlx-vlm">mlx-vlm</a>:</p>
<pre><code>uv run --python 3.13 --with mlx_vlm --with torchvision --with gradio \
  mlx_vlm.generate \
  --model google/gemma-4-e2b-it \
  --audio file.wav \
  --prompt "Transcribe this audio" \
  --max-tokens 500 \
  --temperature 1.0
</code></pre>
<p><audio controls="controls" style="width: 100%;">
  <source src="https://static.simonwillison.net/static/2026/demo-audio-for-gemma.wav" type="audio/wav" />
  Your browser does not support the audio element.
</audio></p>
<p>I tried it on <a href="https://static.simonwillison.net/static/2026/demo-audio-for-gemma.wav">this 14 second <code>.wav</code> file</a> and it output the following:</p>
<blockquote>
<p>This front here is a quick voice memo. I want to try it out with MLX VLM. Just going to see if it can be transcribed by Gemma and how that works.</p>
</blockquote>
<p>(That was supposed to be "This right here..." and "... how well that works" but I can hear why it misinterpreted that as "front" and "how that works".)</p>

    <p>Tags: <a href="https://simonwillison.net/tags/uv">uv</a>, <a href="https://simonwillison.net/tags/mlx">mlx</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/gemma">gemma</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/speech-to-text">speech-to-text</a>, <a href="https://simonwillison.net/tags/python">python</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a></p>