---
id: inbox_5690945a
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t208qv/implemented_turboquant_and_results_dont_fully/"
author: "/u/Routine-Thanks-572"
published_at: 2026-05-02T20:05:02+00:00
fetched_at: 2026-05-03T01:31:38.482604+00:00
content_hash: "efa829f6130f63f9916ac2194531081a0232ef6461fa8b5e9e7b0a213e877ad5"
lang: en
caption_quality: None
raw: true
topics: []
---

# Implemented TurboQuant and results don’t fully match paper

<!-- SC_OFF --><div class="md"><p>I attempted to implement TurboQuant (arXiv:2504.19874) from scratch over the last few days.</p> <p>Thought I would check something with folks here since my numbers do not match those in the paper. </p> <p>Observations:</p> <p>MSE version performs well (compression &amp; distortion as expected) </p> <p>PROD version:</p> <p>claims in paper exceed 99% correlation</p> <p>my number sits around 95.8% at 4-bit </p> <p>But what’s more interesting:</p> <p>even at this ~95% correlation level, attention quality degrades significantly</p> <p>(only ~67% top-1 accuracy on a simple simulation) </p> <p>My hypothesis:</p> <p>correlation != ranking preservation</p> <p>attention is highly sensitive to any order error </p> <p>Other things I ran into:</p> <p>variance scaling (unit vs 1/d) initially killed the MSE variant</p> <p>QJL variance scaling had to be re-derived</p> <p>bit packing is required for compression to work </p> <p>Not sure if:</p> <p>I am simply missing something in the PROD scaling</p> <p>this is expected behavior when d=256</p> <p>or paper results depend on larger dimensions / setup </p> <p>The code is here if anyone is interested in taking a look:</p> <p><a href="https://github.com/Ashx098/Turboquant-Implementation">https://github.com/Ashx098/Turboquant-Implementation</a></p> <p>Would really appreciate feedback from anyone who has worked on KV cache quantization / similar techniques.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Routine-Thanks-572"> /u/Routine-Thanks-572 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t208qv/implemented_turboquant_and_results_dont_fully/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t208qv/implemented_turboquant_and_results_dont_fully/">[comments]</a></span>