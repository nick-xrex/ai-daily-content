---
id: inbox_40357b9c
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tfzsd6/m5_vs_dgx_spark_vs_strix_halo_vs_rtx_6000/"
author: "/u/Signal_Ad657"
published_at: 2026-05-17T19:49:13+00:00
fetched_at: 2026-05-18T03:08:13.209524+00:00
content_hash: "efdba52b7ffe1989b5aebb7b5b6fb3c8e9ce6169fe6afb748762c1d40e122f9e"
lang: en
caption_quality: None
raw: true
topics: []
---

# M5 vs DGX Spark vs Strix Halo vs RTX 6000

Hey guys, super simple. There have been a lot of online debates about the new M5 Macs vs DGX Sparks vs Strix Halo vs dedicated GPUs etc. So I put them all in a room with good power and cooling and ran everything in parallel with standardized tests for the past 3 days, and published everything to a repo. A lot of it isn’t a big surprise when you just think about headline numbers and fundamentals. An RTX6000 has a memory bandwidth speed of ~1,800 gb/s vs ~600 for the M5 vs ~256 for the Spark and Strix. Tokens per second per piece of hardware follows that math and curve pretty well. For the price point, and assuming you are ecosystem agnostic, the maxed out M5 is genuinely legit and very aggressively outperforms the DGX Spark. Again, not really a surprise when you look at their memory bandwidth speeds (2x+ memory bandwidth speeds on the M5 with the same total unified memory). Second thing worth noting was also probably no surprise but the EVO X2 thermals were an issue with extended runs. The MacBook actually surprised me with how well it held up thermally more than anything. It ran for a few days and cruised in the 80c range. I will say this though, it sounds like a normal gaming laptop when it cooks. There’s a bit of propaganda going on when people say “quiet” with these. You ramp up an M5 MacBook Pro to cook with local AI and it turns into a blow dryer like every other laptop that’s ever tried to cook with local AI. It’s built like an aircraft carrier and performs really well for what it is, but you will 100% know it’s working when it runs lol. I’m now swapping back ends and adding data for things like MLX on Mac, different hosting backends on Strix Halo, etc. for how they all impact performance and outputs. The RTX6000 is not the same as the RTX5090 just so the obvious police don’t grab me, but there are a lot of similarities between cards that could make this data useful for someone debating a 5090 PC vs these other machines. Either way, repo enclosed, hope this helps provide some raw data and numbers for future discussions and debates: https://github.com/Light-Heart-Labs/MMBT-Messy-Model-Bench-Tests/tree/main/hardware-tests &#32; submitted by &#32; /u/Signal_Ad657 [link] &#32; [comments]