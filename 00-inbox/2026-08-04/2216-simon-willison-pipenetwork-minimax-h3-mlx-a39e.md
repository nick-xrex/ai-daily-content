---
id: inbox_15f74172
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Aug/4/minimax-h3-mlx/#atom-everything"
author: ""
published_at: 2026-08-04T19:10:09+00:00
fetched_at: 2026-08-04T22:16:07.143203+00:00
content_hash: "a39e25b35fc1bb29dc96421872afa69887e7da53c5defe72a1e2c98d09e660b0"
lang: en
caption_quality: None
raw: true
topics: []
---

# PipeNetwork/minimax-h3-mlx

PipeNetwork/minimax-h3-mlx 
MiniMax released MiniMax-H3 two days ago - they describe it as a "a general-purpose, omni-modal generative system", which in practice means it accepts text, images, audio and video and can use them to generate up to 15 second video clips with audio included. 
 This Python package ports it to MLX for running on Apple Silicon. 
 I got it running on my M5 Max MacBook Pro. I cloned the repo and ran the model like this: 
 # First download the models
uvx --from huggingface_hub hf download MiniMaxAI/MiniMax-H3 \
 --include 'FL2VA/*' --exclude 'FL2VA/transformer/*'
uvx --from huggingface_hub hf download pipenetwork/MiniMax-H3-MLX-8bit

# Now run the prompt
uv run --with mlx-vlm \
 --with-requirements requirements.txt python scripts/generate.py \
 "a rainbow colored skunk leaps over a mossy log in a supermarket" \
 -o skunk.mp4 \
 -c ~/.cache/huggingface/hub/models--MiniMaxAI--MiniMax-H3/snapshots/fa9c8ab1eaa21c8ae25e7e40b83b2e6002f340af/FL2VA \
 -t ~/.cache/huggingface/hub/models--pipenetwork--MiniMax-H3-MLX-8bit/snapshots/3ac52081470b0488921c3ec3ba84a39097bf2361
 
 Here's the video I got for the prompt: 
 
 a rainbow colored skunk leaps over a mossy log in a supermarket 
 
 
 
 Your browser does not support HTML5 video.
 
 

 It downloaded ~115 GB of model files, and the video generation took just under 45 minutes. 
 The video is impressive, but the audio is weird speech-like garbage, because I didn't provide any prompt guidance as to what the audio should be. The prompting guide (which I didn't read prior to this experiment) has a whole bunch of information on how to get this to work.

 Tags: ai , generative-ai , mlx , text-to-video , minimax