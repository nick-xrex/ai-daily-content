---
id: inbox_805f60b8
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/21/cat-and-thariq/#atom-everything"
author: ""
published_at: 2026-07-21T12:54:02+00:00
fetched_at: 2026-07-22T00:16:09.770209+00:00
content_hash: "239c867206250ae1197c8afd5c8681298c55b4b448ac69798772971bbceb9a8c"
lang: en
caption_quality: None
raw: true
topics: []
---

# A Fireside Chat with Cat and Thariq from the Claude Code team

Earlier this month I hosted a fireside chat session at the AI Engineer World's Fair with Cat Wu and Thariq Shihipar from Anthropic's Claude Code team. We talked about Claude Code, Claude Tag, Fable, coding agent security, evals, tool design, and how Anthropic use these tools themselves. 
 The full video of the session is now available on YouTube . Below is an edited copy of the transcript, with extra links and my own bolded highlights. 
 

 A few top-level notes if you don't want to watch the video or wade through the whole transcript: 
 
 Claude Tag (Claude's new collaborative Slack integration) now lands 65% of the product engineering PRs for the Claude Code team. 
 Claude Code ships features to Anthropic employees first, and only ships the features that demonstrate user retention with that cohort 
 
 Critical changes to Claude Code are still reviewed manually, but the team increasingly relies on automated code review for the "outer layers" of the product. 
 Adding examples to a system prompt is no longer best practice for models like Fable 5 or even Opus 4.8. The Claude Code system prompt recently reduced in size by 80% . 
 Likewise, lists of " don't do X and don't do Y " can reduce the quality of results from the latest models. 
 
 Dogfooding inside Anthropic is called " ant fooding ". 
 Anthropic really believe in their auto mode , and see that as an enabling technology for Claude Tag. 
 Thariq advises offsetting coding-agent-induced Deep Blue by " being more ambitious " with the work you take on. 
 Fable is competent at editing video , and Thariq used it to edit its own launch video. 
 Anthropic's culture of working (internally) in public is key to their success, as demonstrated by the way they use Claude Tag in their public Slack Channels. 
 
 How has what you do day-to-day changed in the past year? 
 1:05 
 
 Simon: Claude Code came out in February of last year — it's under a year and a half old, and it was originally just a bullet point on the Claude Sonnet 3.7 launch . How has what you do on a day-to-day basis changed in the past year , now that we have these coding agents that actually work for us? 
 Cat: I remember when we first came out with Claude Code and Sonnet 3.7, you would give it a task and you would have to closely monitor every single little thing it tried to do. I would read every permission prompt extremely carefully. I would frequently say no — no, no, no, did you check this file? Did you check that file? And now it's been incredible with every model generation. I feel like we've all gotten a chance to take a step back and delegate a lot more of the menial implementation to Claude . It's freed up a lot of our time to think about more creative work, like: what is the right experience that we should be providing to our users, now that we know Claude Code can implement a lot of it? And now with Fable it's a totally different step change improvement. We see for a lot of our use cases that you can actually one-shot a ton of features with Fable now . 
 Thariq: I remember the first text I got about Claude Code. One of my best friends was like, "You need to go try Claude Code." It was about when Opus 4 came out, and I tried it and I was like, "Oh, shit. I need to work at Anthropic now." And that was Opus 4 — great model, but you were reading permission prompts. It's kind of crazy how much amnesia we have, where I'm like, oh, auto mode has always been here, right? I don't even remember pressing yes and allow. For me, the big thing I'm trying to push myself on is that we have to do higher quality work than we've ever done before . The outputs are incredibly high quality. I've been using it to edit videos a bunch , and I'm like, okay, it has to meet the very exacting demands of our brand team in a couple of hours or we just can't do it. That's how I'm trying to shift with Fable: the best work we've ever done, faster than we've ever done it before . 
 
 What piece of conventional software engineering no longer holds? 
 3:39 
 
 Simon: What's a piece of conventional software engineering that was true a year ago that you don't think holds anymore in this new world? 
 Cat: One of the biggest shifts we're seeing in the eng skill set: two years ago it was pretty typical for a product manager to go talk to a bunch of customers, align over the course of six months with cross-functional teams on some PRD, and write a thorough spec on exactly how we'll implement this before the first line of code gets written. Now things are completely turned the opposite way. For a lot of engineers, the push I would give to folks in the room is to develop more of your business sense and product sense on what it is we should build , because the timeline between having an idea and building it is so much shorter — it's down from six to twelve months to maybe even a week. That means all of us need to have better taste on what is worth building, what will actually inflect the businesses we're working on. So it's an increase in value on product taste and business sense , and a bit lower on execution in most product domains. Of course, for infra there's still a very heavy emphasis on making sure all the details are right. 
 Thariq: For me, it's that rewrites are now good . 
 Simon: The worst thing you could do is now actually fine! 
 Thariq: Exactly. All the Mythical Man-Month stuff — never rewrite — I'm pro-rewriting now. If you have a good test suite — and I think the rewrite actually forces you to make sure you have a good test suite — but I think what people undercount is that a codebase is a spec, and maybe it's the only copy of the spec that you have , because no one knows every branching part of the codebase. You can take this as an artifact and distill it or create other versions of it. We rewrote Bun in Rust and it works great — it's live for me right now. 
 Simon: You're not shipping Claude Code on Bun-in-Rust yet, right? 
 Thariq: Internally we have. 
 
 (Actually it looks like Anthropic started shipping Claude Code on Bun-in-Rust to everyone on June 17th .) 
 What kind of things are non-engineers doing with Claude Tag? 
 6:36 
 
 Simon: The other big launch recently was Claude Tag — that's what, a week old now, at least for the rest of us. I understand it's being used at Anthropic by non-engineers a great deal. What kind of things are non-engineers doing with Claude Tag? 
 Cat: Claude Tag is a Claude that lives in your team's collaboration tools. We launched it last week within Slack. The thing that's different about Claude Tag is it's multiplayer by default . Once you add Claude Tag to a Slack channel, you can chime in, your teammates can chime in, and you can collaborate together on the PR. The other big difference is that it's proactive instead of reactive. You can tell Claude Tag, "Hey, monitor every bug report in this channel, put up a PR to fix it, and tag the engineer who last touched this part of the codebase," and it'll do it for the lifetime of the channel without you having to manually tag it in. And the third big shift is that we've added team memory into this . If you tell Claude Tag your preferences in the channel, it'll remember them for every future post. If you always want it to debug outages but you don't want it to debug warnings, just tell it that in natural language in the channel and it'll remember it for you and everyone else on your team. 
 Internally, we see Claude Tag as the evolution of Claude Code. We see this as a large shift in how we work internally. Claude Tag currently lands 65% of our product eng PRs. 
 Simon: For all of Anthropic, or just for Claude Code? 
 Cat: This is just for our product engineering team — our internal version of Claude Tag lands 65% of our product PRs right now . And this is a huge shift; this is more than 50% of our PRs. The way we see people split work between Claude Code and Claude Tag is: Claude Code is still the best place for your most complex tasks, when you're interactively iterating with the agent. But Claude Tag is great for having it work proactively on your behalf , so you no longer need to manually kick off Claude Code for all the bug reports that come up for features you're working on. 
 Thariq: And for non-coding cases: for example, before this talk we asked Claude Tag, "Hey, when is Fable releasing?" We wanted to make sure we'd line it up with the announcement. Claude Tag would search our Slack and look at who's been saying what. As a search engine for your company, it's really valuable. It has all the context for your product, so you can ask it metrics-related questions — often when you're making decisions you want them informed by what the metrics say, so you hook it up to your event store. I've seen our marketing team do things like, "Hey, tell me about this feature." They're not programmers, but Claude is a programmer — it can clone the codebase and say, "This is the feature, this is what it looks like, this is a recording of me using the feature ." It enables a whole wide variety of things, and I think we're still early in figuring that out. 
 
 Claude Tag as the team collaborative layer 
 10:06 
 
 Simon: One of the problems I've had with coding agents is that I get how to use them as an individual, but I'm not really clear on how to use them in a team environment. It sounds like Claude Tag is your current answer to that team collaborative layer for this stuff. 
 Cat: Exactly. And a large percentage of our sessions are actually multiplayer right now. Maybe I say, "Hey, I think we should implement this new feature in Cowork," and I'll tag in Claude Tag to do a first pass at it. Then I'll tell Claude Tag, "Share a recording of your final implementation," and I'll tag in design to take a look. They'll nudge it, then pass it on to eng to take it to the finish line and get it out to prod. It's been this very fluid experience. We're still trying to iron out what the social dynamics are for steering the same session , but we've found that people just observe how others use it and follow those social norms — it's been pretty intuitive for us to integrate Claude Tag into our teams. 
 Thariq: It's great for teaching people, and also for reducing slop, because the fact that everyone is seeing you use Claude together sort of levels up how you use Claude as well . 
 
 This reminded me of how Midjourney solved the challenge of teaching people advanced image prompting by enforcing prompting in public in their Discord channels. 
 How do you decide which features are worth building when building is so much cheaper? 
 11:41 
 Something I've found really hard myself is knowing when a feature is worth shipping now that the cost of actually building features has dropped so much. 
 
 Simon: How do you deal with the hardest problem in all of engineering — prioritization? How do you decide which features are worth building and shipping when building a feature is so much more inexpensive now? 
 Cat: This is the hard thing. There are a few ways we approach it. One is we dogfood our products every single day. Whenever there's something we want to be able to do in our products that we're not able to, instead of finding a different solution we fix our product so it can support that case. We have a very heavy dogfooding culture internally. Before we share our products with everyone in the world, we share them with everyone within Anthropic, and with some early customers who give us very honest feedback about it — the more brutal the better — and we iterate until people love it. We have an internal bar for the number of active users and the amount of retention a feature has to have before we share it with the world. Because this bar is very clear, every engineer knows what they're trying to hit. I think this also levels up our polish, because if the feature isn't polished, people will churn — and then we shouldn't ship that feature. 
 
 Using internal user-retention to decide if a feature should ship makes a whole lot of sense to 

[... truncated for safety ...]