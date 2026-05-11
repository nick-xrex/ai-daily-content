---
id: inbox_cca0bdcc
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t9k8gy/i_built_an_open_source_hyperparameter_search_tool/"
author: "/u/Compunerd3"
published_at: 2026-05-10T21:58:12+00:00
fetched_at: 2026-05-10T22:37:14.538074+00:00
content_hash: "62affab78f499b98f84102a0b1bf79226f510a854c416a6486d5faa8fd4596ba"
lang: en
caption_quality: None
raw: true
topics: []
---

# I built an open source hyperparameter search tool for diffusion fine-tunes- pick the winner based on scoring

I kept running the same loop: train a LoRA, look at the samples, decide it’s “fine”, change three things at once, train again, then when a new dataset needs training, all the parameters previously need to be reviewed again. So I built something to take the hassle out of this. It’s called Bracket . You point it at a dataset and a model Set a budget (such as sample size to test # of candidates or variations to try out It runs X short training trials in parallel configurations (Optuna TPE for the search). Each run gets scored two ways: The training-loss trajectory, A local VLM (LM Studio) judging the sample images on prompt-adherence, visual quality, and artifact-freeness. At the end you get a Markdown report with Welch’s t-test confidence on which config wins. The whole point is to replace “this LoRA looks better to me” with “config X beats baseline by 0.34 with p=0.03 over 4 seeds”. It doesn’t reimplement training. It drives musubi-tuner and sd-scripts as subprocesses, so the trainers are exactly what kohya already supports — same args, same outputs. Currently covers SDXL, Z-Image, Flux.1, Flux.1-Kontext, Flux-2-Klein, Qwen-Image (+ Edit), SD3.5, HunyuanVideo, Wan 2.1/2.2, LTX-Video, FramePack. LoRA and full FT for most. A few engineering bits that might be interesting: Trainers always launch through accelerate because raw python triggers a 2000-second-per-iteration Accelerator init on Blackwell GPUs. Tqdm is force-disabled because \r writes fill the OS pipe buffer when stdout is captured and freeze the trainer. VRAM-tier-aware search space — detects the GPU and only proposes configs the card can actually run. No wasted OOM trials. Curated warm-start: each trainer adapter ships 3-5 known-good configs that run before TPE takes over, so you get useful comparisons in the first 30 minutes instead of the third hour. VLM judge uses OpenAI-spec response_format: json_schema so the output is grammar-constrained at the llama.cpp level — zero JSON parse failures, no rambling. There’s a toggle that sends chat_template_kwargs={enable_thinking: false} to skip the &lt;think&gt; preamble on Qwen3-class VLMs. Self-updater built into the React UI — toast when there’s a new commit, click Update, it pulls + rebuilds + relaunches. MIT, runs locally, no telemetry, no account. Repo: https://github.com/tlennon-ie/bracket Honest about what it isn’t : it’s not a magic better-LoRA or finetune generator, it’s a search harness. If the dataset is bad it’ll just tell you “all 8 configs are bad” with high confidence. The value is turning “I think this LoRA is better” into a number you can defend. https://preview.redd.it/27w2a7lrtd0h1.png?width=1597&amp;format=png&amp;auto=webp&amp;s=50b47b449bda98ea1b98744e13a83dbdef4cc7c3 &#32; submitted by &#32; /u/Compunerd3 [link] &#32; [comments]