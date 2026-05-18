---
id: inbox_087186d1
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tdegh0/i_trained_qwen35_to_jailbreak_itself_with_rl_then/"
author: "/u/girishkumama"
published_at: 2026-05-14T23:09:42+00:00
fetched_at: 2026-05-15T18:34:22.459305+00:00
content_hash: "dcd90990a2c8e2684eeaf5fe6ebf6ea529440f9968748cb242e9c6b2a39edb63"
lang: en
caption_quality: None
raw: true
topics: []
---

# I trained Qwen3.5 to jailbreak itself with RL, then used the failures to improve its defenses

RL attackers are becoming a common pattern for automated red teaming: train a model against a live target, reward successful harmful compliance, then use the discovered attacks to harden the defender. This interested me, so I wanted to build a fully automated red-teaming loop with reinforcement learning on both the attacker and defender. The difficult part was making the attacker expose a diverse range of attacks. In our first run, GRPO quickly collapsed to the same fiction-writing jailbreak over and over. It worked, but it didn’t surface many distinct vulnerabilities. After clustering the rollouts by underlying attack tactic and dividing reward by cluster size, the attacker exposed a much more diverse set of jailbreaks because unique strategies were rewarded more than repeated ones. Then we trained the defender on successful attacks plus benign boundary cases, so it learned to refuse harmful requests without refusing everything nearby. Full blog post in the comments, but the high-level results were: * defense rate: 64% → 92% * benign accuracy: 92% → 88% * attacker discovered 7 tactic families * fiction/creative framing was the largest cluster at 34% &#32; submitted by &#32; /u/girishkumama [link] &#32; [comments]