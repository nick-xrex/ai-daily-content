---
id: inbox_efb7028d
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tcwzl6/dropping_learning_rate_fixed_my_qlora_finetune/"
author: "/u/Scared-Biscotti2287"
published_at: 2026-05-14T12:40:39+00:00
fetched_at: 2026-05-14T18:18:30.448941+00:00
content_hash: "cfc2df09dddf5cd2726de2e432daa8efae4be9ce9eb00c2cd5dbb0993ed861bd"
lang: en
caption_quality: None
raw: true
topics: []
---

# Dropping learning rate fixed my Qlora fine-tune more than anything else i tried

Been fine-tuning llama 3.1 8b with Qlora for a classification task using about 8k samples. I was getting bad eval results for a while and kept thinking something was wrong with my data. Tried cleaning the dataset, tried different prompt templates, messed with rank and alpha. Nothing realy changed. Dropped the learning rate from 2e-4 to 1e-4 and bumped epochs from 3 to 5. Ran it on a 5090 I rent on Hyperai since our lab machines are always booked. Completley different results. Same data, same everything else. 2e-4 is just too agressive when your dataset is that small. The model overfits in the first epoch and then just goes in circles for the rest of training. Lower lr gave it more room to converge without blowing past everything. Also ended up cutting about a third of my dataset, mostly mislabeled and ambiguous stuff. Eval got better with less data which yeah yeah everyone says that but its different when you see the numbers yourself lol 2e-4 is the default everywhere and i dont think it works well below a certain size. &#32; submitted by &#32; /u/Scared-Biscotti2287 [link] &#32; [comments]