---
id: inbox_ba59993f
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tdtaqt/bytedanceseedcoladlm_hugging_face/"
author: "/u/pmttyji"
published_at: 2026-05-15T11:19:29+00:00
fetched_at: 2026-05-15T18:34:22.470266+00:00
content_hash: "780a3eae65744870dc38d353fc806531fb8ac24edbc7e5819a5f0bbb77384aec"
lang: en
caption_quality: None
raw: true
topics: []
---

# ByteDance-Seed/Cola-DLM · Hugging Face

Cola DLM ( Co ntinuous La tent D iffusion L anguage M odel) is a hierarchical continuous latent-space diffusion language model. It combines a Text VAE with a block-causal Diffusion Transformer (DiT) prior: the VAE maps text into continuous latent sequences and decodes latents back to tokens, while the DiT performs latent prior transport through Flow Matching. This model repository contains the HuggingFace-format checkpoint for the paper Continuous Latent Diffusion Language Model . Links Model repository: https://huggingface.co/ByteDance-Seed/Cola-DLM GitHub repository: https://github.com/ByteDance-Seed/Cola-DLM Paper: https://arxiv.org/abs/2605.06548 HuggingFace Daily Paper: https://huggingface.co/papers/2605.06548 Project page: https://hongcanguo.github.io/Cola-DLM/ Blog post: https://hongcanguo.github.io/posts/2026-cola-dlm.html Zhihu article: https://zhuanlan.zhihu.com/p/2038324180920313704 Model Details Architecture: Text VAE + block-causal DiT latent prior. Training objective: two-stage training with Text VAE pretraining followed by joint Text VAE + DiT training using Flow Matching. Training-compute checkpoint: the released weights correspond to the 2000 EFLOPs checkpoint reported in the paper's RQ4 scaling curve. Tokenizer: OLMo 2 tokenizer with a 100,278-entry vocabulary. Special token ids: pad_token_id=100277 , eos_token_id=100257 , im_end_token_id=100265 . Framework: PyTorch 2.1+ and HuggingFace Transformers 4.40+. License: Apache License 2.0. &#32; submitted by &#32; /u/pmttyji [link] &#32; [comments]