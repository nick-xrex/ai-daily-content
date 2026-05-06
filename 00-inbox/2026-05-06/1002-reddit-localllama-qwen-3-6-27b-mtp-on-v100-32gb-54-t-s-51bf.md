---
id: inbox_aa28a01b
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t4zu88/qwen_36_27b_mtp_on_v100_32gb_54_ts/"
author: "/u/m94301"
published_at: 2026-05-06T02:18:44+00:00
fetched_at: 2026-05-06T10:02:16.905732+00:00
content_hash: "51bf116e1516c8d7d6e2db565a71bc21b743f5b68aa2ea8df5defe30cddfcf20"
lang: en
caption_quality: None
raw: true
topics: []
---

# Qwen 3.6 27B MTP on v100 32GB: 54 t/s

<!-- SC_OFF --><div class="md"><p>Just a quick note that I got a nice result using am17an's MTP branch of llama.cpp on v100 32GB SXM module using one of those pcie card adapters. Pulled and built in one shot, and llama-server ran without a hitch.</p> <p>Tested using am17an's MTP GGUF, q8_0 kv cache and 200k cache limit acting as vscode copilot.</p> <p>29-30 t/s without MTP</p> <p>54-55t/s with MTP, using 150W power limit on the card.</p> <p>Falls to 40-45 t/s after choking down 50k tokens, but doing great with tool calls, sub agents, and made some very insightful code reviews and refactors. </p> <p>Thank you am17an! Can't wait to see this branch mature, this is great stuff.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/m94301"> /u/m94301 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4zu88/qwen_36_27b_mtp_on_v100_32gb_54_ts/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4zu88/qwen_36_27b_mtp_on_v100_32gb_54_ts/">[comments]</a></span>