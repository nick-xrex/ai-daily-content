---
id: inbox_43e4930a
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t6r1ny/extracted_mtp_tensor_ggufs_smaller_donor_models/"
author: "/u/AzerbaijanNyan"
published_at: 2026-05-07T23:28:41+00:00
fetched_at: 2026-05-08T07:37:41.367166+00:00
content_hash: "4747d0a99fac644fd63f0ba33cded021bd30db311dcd24184f6cd0e1a28d4817"
lang: en
caption_quality: None
raw: true
topics: []
---

# Extracted MTP tensor GGUFs - smaller donor models for grafting.

The script to graft MTP tensors requires a full GGUF model file. I felt that was a bit hefty, so I asked local Gemma to write something to just extract what's required. The results are two faux GGUFs weighing in at just 900MB ( 35A3B ) and 450MB ( 27B ), containing only the tensors and fully compatible with the script. A lot quicker to download compared to the original 38GB and 29GB models for those who just want to convert their existing library or save some bandwidth. Testing was done using SHA256 hashes, comparing the models made with these mini-GGUFs to those using the full models (identical results), along with some brief chats. Credits: am17an for the original GGUFs, and buzz for the original script. Disclaimers: The MTP implementation isn't finalized. These models might break or become obsolete at any time. Do not delete the original models in case there are updates to the conversion process. Testing was only done on the two models I use myself; other variants might not work well/at all. Also, 100% clueless vibecoding with a Q4_1 model. &#32; submitted by &#32; /u/AzerbaijanNyan [link] &#32; [comments]