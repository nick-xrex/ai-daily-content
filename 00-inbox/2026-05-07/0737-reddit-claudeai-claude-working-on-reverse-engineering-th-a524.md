---
id: inbox_b8b3baaa
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t6n6dt/claude_working_on_reverse_engineering_the/"
author: "/u/Beerbrewing"
published_at: 2026-05-07T20:53:47+00:00
fetched_at: 2026-05-08T07:37:42.318560+00:00
content_hash: "a524467cebdf362463dca9274db9e6b7014b43b1a8f7b2906aa89b371934c4e1"
lang: en
caption_quality: None
raw: true
topics: []
---

# Claude working on reverse engineering the firmware for a gamma spectrometer using various radioactive sources

Something I started a little while ago. I've been using Claude chat and Claude code to reverse engineer the firmware transfer function of the RadiaCode 110 gamma spectrometer. Basically the lens (the firmware transfer function) I have to look through to see the actual physics occurring in the scintillator crystal. Once I have the firmware behavior I can then &quot;see&quot; what the scintlator crystal is doing without the layers the radiacode adds before surfacing data to the user. So far we've empirically pulled out the &quot;event&quot; firmware transfer function, the formula the company uses to smooth the gamma counts per second, from reading the firmware's counts per second output by placing it into a lead lined bucket that turned the radiacode into a preferential muon detector. The lead castle blocks out the terrestrial radiation but allows the cosmic muons to still pass through. Allowing me to use cosmic radiation and terrestrial radon events to probe the firmware behavior. Today we are moving on to controlled radiation probing, where I place different radioactive materials at different distances from the device. An Americum button from a commercial smoke detector, a thoriated projector lens, and a sample of lutetium 176.This testing will significantly close the gap in the firmware functions we are after. It's just kind of funny to me that six weeks ago I started with Claude chat asking about the radiacode gamma spectrometer and here I am running controlled radiation tests on it to probe its firmware responses. The last time I did any programming was back in the early 90s and that was Pascal and Fortran. Having Claude chat work with Claude code, through analysis/build handoffs is something I could never program on my own. Claude chat is like having my own research assistant and Claude code is like my software engineer. Together I'm building something I could never do on my own. &#32; submitted by &#32; /u/Beerbrewing [link] &#32; [comments]