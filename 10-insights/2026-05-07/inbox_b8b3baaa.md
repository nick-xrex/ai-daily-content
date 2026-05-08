---
id: inbox_b8b3baaa
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-claudeai-claude-working-on-reverse-engineering-th-a524]]"
title: "Claude working on reverse engineering the firmware for a gamma spectrometer using various radioactive sources"
url: https://www.reddit.com/r/ClaudeAI/comments/1t6n6dt/claude_working_on_reverse_engineering_the/
source: reddit-claudeai
published_at: 2026-05-07T20:53:47+00:00
fetched_at: 2026-05-08T08:11:13.759709+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者用 Claude Chat 與 Claude Code 逆向工程 RadiaCode 110 伽馬能譜儀固件。核心成就：(1) 從固件輸出數據中經驗性提取「事件」固件轉換函數與公司用來平滑計數率的公式；(2) 利用鉛屏障建造的「鉛城堡」阻擋地表輻射但允許宇宙µ子通過，將譜儀轉變為µ子檢測器來探測固件行為；(3) 計畫進行控制輻射實驗——使用美銀釹鈕扣（商用煙霧探測器內）、釷化投影透鏡及鐿-176 樣品。使用者最後一次編程在 1990 年代（Pascal/Fortran），透過 Claude Chat 的研究助手角色與 Claude Code 的軟體工程師角色協作，完成了自己無法獨立完成的跨學科研究。"
key_points:
  - "使用者在無編程基礎（90 年代後未再程式設計）的情況下，透過 Claude Chat + Claude Code 的分工（分析與構建交接）完成複雜固件逆向工程"
  - "利用宇宙射線與地表氡事件作為「探針」來測試固件響應，經驗性提取了計數率平滑公式"
  - "六週內從初始問題到控制輻射測試設計，展示 Claude 在多學科推理與程式碼協作中的能力"
tags: [firmware-reverse-engineering, physics-research, multimodal-reasoning, claude-code, radiation-detection]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude working on reverse engineering the firmware for a gamma spectrometer using various radioactive sources

使用者用 Claude Chat 與 Claude Code 逆向工程 RadiaCode 110 伽馬能譜儀固件。核心成就：(1) 從固件輸出數據中經驗性提取「事件」固件轉換函數與公司用來平滑計數率的公式；(2) 利用鉛屏障建造的「鉛城堡」阻擋地表輻射但允許宇宙µ子通過，將譜儀轉變為µ子檢測器來探測固件行為；(3) 計畫進行控制輻射實驗——使用美銀釹鈕扣（商用煙霧探測器內）、釷化投影透鏡及鐿-176 樣品。使用者最後一次編程在 1990 年代（Pascal/Fortran），透過 Claude Chat 的研究助手角色與 Claude Code 的軟體工程師角色協作，完成了自己無法獨立完成的跨學科研究。

### 重點
- 使用者在無編程基礎（90 年代後未再程式設計）的情況下，透過 Claude Chat + Claude Code 的分工（分析與構建交接）完成複雜固件逆向工程
- 利用宇宙射線與地表氡事件作為「探針」來測試固件響應，經驗性提取了計數率平滑公式
- 六週內從初始問題到控制輻射測試設計，展示 Claude 在多學科推理與程式碼協作中的能力

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t6n6dt/claude_working_on_reverse_engineering_the/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Something I started a little while ago. I've been using Claude chat and Claude code to reverse engineer the firmware transfer function of the RadiaCode 110 gamma spectrometer. Basically the lens (the firmware transfer function) I have to look through to see the actual physics occurring in the scintillator crystal. Once I have the firmware behavior I can then &quot;see&quot; what the scintlator crystal is doing without the layers the radiacode adds before surfacing data to the user. So far we've empirically pulled out the &quot;event&quot; firmware transfer function, the formula the company uses to smooth the gamma counts per second, from reading the firmware's counts per second output by placing it into a lead lined bucket that turned the radiacode into a preferential muon detector. The lead castle blocks out the terrestrial radiation but allows the cosmic muons to still pass through. Allowing me to use cosmic radiation and terrestrial radon events to probe the firmware behavior. Today we are moving on to controlled radiation probing, where I place different radioactive materials at different distances from the device. An Americum button from a commercial smoke detector, a thoriated projector lens, and a sample of lutetium 176.This testing will significantly close the gap in the firmware functions we are after. It's just kind of funny to me that six weeks ago I started with Claude chat asking about the radiacode gamma spectrometer and here I am running controlled radiation tests on it to probe its firmware responses. The last time I did any programming was back in the early 90s and that was Pascal and Fortran. Having Claude chat work with Claude code, through analysis/build handoffs is something I could never program on my own. Claude chat is like having my own research assistant and Claude code is like my software engineer. Together I'm building something I could never do on my own. &#32; submitted by &#32; /u/Beerbrewing [link] &#32; [comments]

</details>