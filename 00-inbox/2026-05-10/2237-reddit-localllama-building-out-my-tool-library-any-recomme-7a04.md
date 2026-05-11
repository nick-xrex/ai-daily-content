---
id: inbox_623729de
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t97163/building_out_my_tool_library_any_recommendations/"
author: "/u/Creative-Type9411"
published_at: 2026-05-10T13:31:10+00:00
fetched_at: 2026-05-10T22:37:14.815051+00:00
content_hash: "7a04c0e15df57d74cbbe1999955cf5f216ca3a0f66a7bd124beb0d663fa26096"
lang: en
caption_quality: None
raw: true
topics: []
---

# Building out my tool library, any recommendations? I just added email capability and im starting to get hyped!

I'm using OpenWebUI and and making tools/skills to improve my models functionality. I am currently using Qwen 3.6 35B A3B Q8 (F16) 256k I grabbed `parallel tools` to be able to run multiple tool calls at once.. so far i have the following... -------------- Document Creator: (WIP started it yesterday, testing now, almost done, rest of list is fully working and done) creates DOC/PDF/XLS/PPTX files, using linux prereqs and helpers, allows model to create documents Send_Email: Allows the model to send an email from an smtp server, supports file attachments if the model wants to send an attachment Inline visualizer (I found this here on reddit): allows visualizations to be produced directly in chat, its pretty awesome Github Url converter: converts regular github links into raw links to make it viewable by the model Weather: gets current and/or historical weather information for any location, lookup time is reduced for us based locations based on zip database (reduces call time significantly) Sports: scores/schedules lookup Filesystem: Allows a sandboxed directory (path checking on every command, outside of the models control) to create/modify/delete files, read files, append files, ZIP files (password protected if asked) - The model is aware of all files it has possession of including any generated images, anything its made can be referenced and it will be able to get it and do whatever you want with it Browse_Page: enhanced web scraping leveraging different user agents, filters, this is paired with the default websearch included with OpenWebUI and works really well i hit 20-30 links usually during search where i used to only get 4-5 reliable ones Wayback_archive: this tool is called whenever a site is blocked through normal access to be able to get the data anyway from the latest archived version of it (found this idea here as well on reddit but i made a custom version/tool to save on tokens instead of using it as a prompt) read_microsoft_learn: a tool to enable to model to lookup anything on microsoft learn, to help itself C#/WPF/NET or anything else it's unsure of ----------------------- Im trying to figure out what to build out next after im done the document creator... Im going to try and add SMS, since emails are usually more of a &quot;silent&quot; alert, at least for me.. But right now I can literally tell this thing to create a flyer for my services then go find emails of local business owners and send it to them and it will... While i go do something else... This is crazy im going to make skynet ;P &#32; submitted by &#32; /u/Creative-Type9411 [link] &#32; [comments]