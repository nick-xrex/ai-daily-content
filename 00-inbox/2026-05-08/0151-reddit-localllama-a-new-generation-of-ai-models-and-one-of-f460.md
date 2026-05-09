---
id: inbox_e0c49834
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t6yra2/a_new_generation_of_ai_models_and_one_of_the_most/"
author: "/u/assemsabryy"
published_at: 2026-05-08T05:38:10+00:00
fetched_at: 2026-05-09T01:51:59.656662+00:00
content_hash: "f46097fc1e3be6122f03b3b7563849601d32f84ca585b30ea977f575804cb226"
lang: en
caption_quality: None
raw: true
topics: []
---

# A new generation of AI models and one of the most powerful research papers out there.

https://preview.redd.it/3ccm5gd1puzg1.png?width=1179&amp;format=png&amp;auto=webp&amp;s=c940d2e6ef1d61288ac214eae4679a7c910b7917 Today, I’m talking about a new research paper from Token AI: &quot;Stable Training with Adaptive Momentum&quot; It introduces what could be one of the strongest optimizers, both in theory and in results. For years, we’ve relied on well-known optimizers like Adam, AdamW, LAMB, and others. No doubt, they’ve been the go-to choices when training AI models. If you’re not familiar with what an optimizer is, in simple terms: it’s a core part of training any AI model. It’s the algorithm responsible for updating the model’s weights during training to reduce the loss. That said, these optimizers come with limitations that affect training. For example, Adam uses a fixed beta1 throughout training, which can carry outdated momentum and keep pushing the model in the wrong direction. STAM addresses this by measuring the difference between the current gradient and previous momentum (g - m). When the difference is large, it reduces beta1, leading to more stable training during noisy phases. Another issue appears when there’s a shift or noise in training. Old momentum can become harmful. STAM handles this with an adaptive beta1 based on residual variance. A major issue in SGD is that if the direction becomes wrong, it keeps going due to fixed momentum. STAM solves this by allowing the first momentum to self-correct. Now let’s talk about STAMLite, the lighter version. It’s designed to replace AdamW as a default choice in many cases. The key difference is that beta1 is dynamic instead of fixed: If gradients are noisy, it reduces momentum If gradients are stable, it keeps momentum high It also improves efficiency in terms of optimizer state memory: AdamW requires about 2× the parameter size STAM Full is close to AdamW STAMLite requires about 1× the parameter size In practice, STAMLite saves around 50% of the resources compared to AdamW and STAM, meaning significantly less GPU usage during training. Looking at benchmarks, the results speak for themselves. In Hyperparameter Sweep, STAMLite achieved: Accuracy: 0.61 Loss: 0.91 In Long-Horizon Non-Stationary MLP, STAM ranked first alongside NAdam with nearly identical results: Accuracy: 0.97 Loss: 0.09 More benchmarks are available on the website and in the research paper. This is an important step from TokenAI, breaking the long-standing reliance on a limited set of optimizers that come with known issues. Even as an early release, it proves strong and promising. Personally, I’ve already shifted to STAM and I’m currently training my first full LLM from scratch using it. I’ll be sharing the results soon. Research paper: https://tokenai.cloud/research/stam Let me know what you think. &#32; submitted by &#32; /u/assemsabryy [link] &#32; [comments]