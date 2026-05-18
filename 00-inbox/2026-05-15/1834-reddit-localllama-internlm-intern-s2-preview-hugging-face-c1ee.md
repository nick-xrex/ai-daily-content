---
id: inbox_dd2ab048
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tdrw0s/internlminterns2preview_hugging_face/"
author: "/u/pmttyji"
published_at: 2026-05-15T10:09:59+00:00
fetched_at: 2026-05-15T18:34:22.435989+00:00
content_hash: "c1ee9df3808c1004dd5fbb07a29b397b3c47d837e3191ac4da51fbce67cd288a"
lang: en
caption_quality: None
raw: true
topics: []
---

# internlm/Intern-S2-Preview · Hugging Face

Introduction We introduce Intern-S2-Preview , an efficient 35B scientific multimodal foundation model. Beyond conventional parameter and data scaling, Intern-S2-Preview explores task scaling : increasing the difficulty, diversity, and coverage of scientific tasks to further unlock model capabilities. By extending professional scientific tasks into a full-chain training pipeline from pre-training to reinforcement learning, Intern-S2-Preview achieves performance comparable to the trillion-scale Intern-S1-Pro on multiple core professional scientific tasks, while using only 35B parameters (continued pretrained from Qwen3.5) . At the same time, it maintains strong general reasoning, multimodal understanding, and agent capabilities. Features Scientific task scaling with full-chain training. Intern-S2-Preview scales hundreds of professional scientific tasks from pre-training to RL, enabling strong performance across multiple specialized domains at only 35B parameters. It further strengthens spatial modeling for small-molecule structures and introduces real-valued prediction modules, making it the first open-source model with both material crystal structure generation capability and strong general capabilities. Enhanced agent capabilities for scientific workflows. Intern-S2-Preview significantly improves agentic abilities over the previous generation, achieving strong results on multiple scientific agent benchmarks. Efficient RL reasoning with MTP and CoT compression. During RL, Intern-S2-Preview adopts shared-weight MTP with KL loss to reduce the mismatch between training and inference behavior, substantially improving MTP accept rate and token generation speed. It also introduces CoT compression techniques to shorten responses while preserving strong reasoning capability, achieving improvements in both performance and efficiency. &#32; submitted by &#32; /u/pmttyji [link] &#32; [comments]