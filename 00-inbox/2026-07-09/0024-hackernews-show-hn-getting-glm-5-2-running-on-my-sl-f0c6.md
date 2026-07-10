---
id: inbox_65c5b1d9
source: hackernews
source_type: hn
url: "https://github.com/JustVugg/colibri"
author: "vforno"
published_at: 2026-07-09T08:05:04+00:00
fetched_at: 2026-07-10T00:24:22.603103+00:00
content_hash: "f0c68eb8a519adce38dc80ed8cfd34ee0784b6eb65b53cb50939d20b93945ff7"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: Getting GLM 5.2 running on my slow computer

A few days ago I found myself trying out GLM 5.2 and was really positively impressed. The capabilities and security I was getting from this LLM are similar to those I&#x27;ve gotten from models like Claude or GPT, and this really surprised me. But then I thought, &quot;I wonder how it would work on a normal computer like mine,&quot; and above all, &quot;I wonder if it would work without going into OOM on a computer like mine.&quot; So I started working with the help of agents to test this possibility. I started converting the model to int4, understanding MTP usage, and if possible implementing DSA for long context. How it responds in int4 and whether the quality is maintained or not. Until I got to the point, on my computer with 32GB of RAM, I was able to communicate with GLM 5.2 with times that, of course, aren&#x27;t high in cold start, but even then, we&#x27;re talking about 0.1 tok&#x2F;s, but that wasn&#x27;t important to me. The important thing was the journey to reach this goal. I just wanted it to work at all costs, even slowly. So I created Colibrì, which was born from a very simple idea, to be honest, but tested in every way, where a 744B Mixture-of-Experts model activates only ~40B parameters per token—and only ~11 GB of those change from token to token (the routed experts). So: The dense part (attention, shared experts, embeddings—~17B params) stays resident in RAM at int4 (~9.9 GB); The 21,504 routed experts (75 MoE layers × 256 experts + the MTP head, ~19 MB each at int4) live on disk (~370 GB) and are streamed on demand, with a per-layer LRU cache, an optional pinned hot-store, and the OS page cache as a free L2. The engine is a single C file (c&#x2F;glm.c, ~1,300 lines) plus small headers. No BLAS, no Python at runtime, no GPU.No GPU or serious hardware because I don&#x27;t have that hardware so I can&#x27;t test it on hardware that is more powerful than my computer.Colibrì is a one-person project, written and tested entirely on a 12-core laptop with 25 GB of RAM — the numbers above are the ceiling of what I can measure at home. Any feedback is welcome! (and if anyone wanted to participate in the project I would be delighted) Repo: https:&#x2F;&#x2F;github.com&#x2F;JustVugg&#x2F;colibri