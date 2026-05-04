---
id: inbox_6d96e553
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t2v0zh/qwen3tts_but_in_openvino_from_scratch/"
author: "/u/Echo9Zulu-"
published_at: 2026-05-03T19:30:02+00:00
fetched_at: 2026-05-04T13:38:38.139176+00:00
content_hash: "f33871ff48b2b5030b3487808c1e951dda08d4b7a9a052b7f2d40c98b5070fd0"
lang: en
caption_quality: None
raw: true
topics: []
---

# Qwen3-TTS but in OpenVINO, from scratch

<!-- SC_OFF --><div class="md"><p>Hello everyone,</p> <p>I finally got around to preparing my implementation of Qwen3-TTS in OpenVINO format as a codebase. This work was done in early 2026, merged to OpenArc in March and I kept forgetting about releasing the code. Here we are. <a href="https://github.com/SearchSavior/Qwen3-TTS-OpenVINO">https://github.com/SearchSavior/Qwen3-TTS-OpenVINO</a></p> <p>One guy from our discord speaks russian and I wanted to voice clone elmo on my A770,so I decided to from scratch Qwen3-TTS in pytorch, ignoring transformers (except for AutoTokenizer, my beloved) to really get inside how you design an OpenVINO conversion to their model format. </p> <p>The key learning is: you take an <code>nn.Module</code> with some logic, it's forward method, study the data flow, then iterate until you find the combination of data flow and device placement which lets the openvino compiler choose the best kernels. Interfering with this process ie, custom kernels is a totally seperate mission for future work. There were a ton of steps in between, and a key learning for me in this project was taking better notes. </p> <p>AI assistance was used... but honestly I'm not sure how it could be done without it. Even Opus 4.5 could not make good openvino flavored choices, especially around stateful kv cache and could not anticipate kernel fusion without extensive guidance. Intel does not put enough effort into documenting their engineering practices... which makes openvino feel not so open after all. BUT, with AI tools and some effort, it is possible.</p> <p>This codebase can be generalized for optimizing any pytorch model for openvino IR format. I tried to make sure the code is easy to follow, but it is quite demanding conceptually, drawing on poorly documented openvino concepts Opus implemented based on targeted examples from the upstream source I was able to conjure from memory, with hours of testing on top. Though AI assisted, this code was in no way <em>full send vibe coded</em>.</p> <p>It's all live in OpenArc now, covering only 1.7B size for CPUs and GPUs; I had issues with 0.6B I did not investigate further. NPU support PRs are most welcome. </p> <p>Unlike other implementation posts, I haven't included any benchmarks mostly due to time constraints plus changes I made to the inference code in the OpenArc PR vs what's in this repo. If there is interest we can bench OpenArc vs pytorch cpu/xpu.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Echo9Zulu-"> /u/Echo9Zulu- </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2v0zh/qwen3tts_but_in_openvino_from_scratch/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2v0zh/qwen3tts_but_in_openvino_from_scratch/">[comments]</a></span>