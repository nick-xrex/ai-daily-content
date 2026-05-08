---
id: inbox_ec87a325
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t6n97x/1167_arcagi2_local_eval_on_a_single_4090_the/"
author: "/u/Doug_Bitterbot"
published_at: 2026-05-07T20:56:47+00:00
fetched_at: 2026-05-08T07:37:41.363491+00:00
content_hash: "fbe2c002cfdc5b99e3e401052b86fd33af497b2507756dc4785207a93989bdef"
lang: en
caption_quality: None
raw: true
topics: []
---

# 11.67% ARC-AGI-2 Local Eval on a Single 4090: The TOPAS Recursive Architecture

I'm not sure too many people care about the ARC-AGI-2 competition anymore, but still...I thought some might find this interesting. They're running it one last time this year. Everyone is currently leaderboard-stuffing using the winning open-source code from last year. That's why if you take a peak it's really just the same scores clogging it up. We're doing something a bit different though, building a highly efficient, deep-recursion model from scratch. We just hit 11.67% on the public LB, but that's with a massive asterisk. We don't have a cluster. We have one RTX 4090 . And we're only 14 days or so into training a 100m parameter model. Locally, this checkpoint actually hit 36%. On the Kaggle submission, our TTT is computationally heavy because of the recursive loops. To avoid a total submission timeout, we set the thresholds too high, and the model ended up outputting [] (null) for nearly half the puzzles...hence the 11.67%. We're trying to show that ARC isn't just a Compute War, but an architecture war. Small models using biological memory models can punch way above their weight class if they can handle the reasoning loops. We're tuning the time-management logic tonight and expect to put a 20% score up tomorrow once we let the model actually finish the thought process. And beyond that...the actual model is still in training, in the Grokking phase. We strongly believe that if we give it another 3-5 weeks to fully train we could drop something really groundbreaking on that leaderboard. If you're interested in how we're scaling recursive reasoning on consumer metal, we'd love to answer questions about it. &#32; submitted by &#32; /u/Doug_Bitterbot [link] &#32; [comments]