---
id: inbox_c1d77e9d
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t6nuhz/i_embedded_an_ai_agent_in_my_shell_it_can_now_run/"
author: "/u/zoomaaron"
published_at: 2026-05-07T21:18:26+00:00
fetched_at: 2026-05-08T07:37:41.359168+00:00
content_hash: "4c88cd26feed63d76051647272198db3d5816575e71d2224df8172133dff965a"
lang: en
caption_quality: None
raw: true
topics: []
---

# I embedded an AI agent in my shell. It can now run interactive programs.

I want to share a fun side project of mine over the past month or so where I tried to build a shell with an AI agent embedded. The embedded agent knows everything happening in the shell so I don't have to keep copy-and-pasting error messages to another coding agent while working in a terminal. Now it has grown into a useful tool in my daily workflow and a fun playground for agent experiments. Here I'm showing a new extension I'm building that launches an agent on a floating overlay that can read my terminal and type out commands for me, which I thought was really cool. I can already see lots of application of this idea such as helping me with interactive installation or helping me over an ssh session without remote installation. The project is fully open source with mit license, feel free to try it out and build on it. It should support local models as well as cloud models. This overlay feature is an experimental extension that only exists in the example folder. You can point your coding agent to the docs to help you set it up should you want to try it out (be sure to grab both the overlay-agent extension for the floating display and the terminal-buffer extension for sending keys to the terminal). Be warned that this is still in development, so things may break! Happy to hear your thoughts and suggestions on this project. &#32; submitted by &#32; /u/zoomaaron [link] &#32; [comments]