---
id: inbox_0c18679e
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1002-infoq-main-attacker-bought-30-wordpress-plugins-on-769e]]"
title: "Attacker Bought 30 WordPress Plugins on Flippa and Backdoored All of Them"
url: https://www.infoq.com/news/2026/05/wordpress-plugins-supply-chain/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-06T10:00:00+00:00
fetched_at: 2026-05-06T10:08:20.888546+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "攻擊者在 Flippa 上購買 30+ WordPress 外掛，在第一次代碼提交時植入 PHP 反序列化後門，潛伏 8 個月後跨 400,000 個安裝激活，透過以太坊智能合約進行 C2 通訊。此攻擊暴露 WordPress.org 缺乏外掛所有權轉移審查機制的生態漏洞，該漏洞 npm 和 PyPI 已於多年前修復，凸顯開源軟體供應鏈防禦的重要性。"
key_points:
  - "攻擊者購買 30+ 外掛、植入反序列化後門、影響 400,000 個安裝，潛伏期 8 個月後激活"
  - "使用以太坊智能合約進行 C2 通訊（區塊鏈用於隱蔽通訊的新應用）"
  - "WordPress.org 缺所有權轉移審查機制；npm/PyPI 已於多年前建立審查流程，形成防禦差距對比"
tags: [wordpress, supply-chain-security, backdoor, plugin-security]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Attacker Bought 30 WordPress Plugins on Flippa and Backdoored All of Them

攻擊者在 Flippa 上購買 30+ WordPress 外掛，在第一次代碼提交時植入 PHP 反序列化後門，潛伏 8 個月後跨 400,000 個安裝激活，透過以太坊智能合約進行 C2 通訊。此攻擊暴露 WordPress.org 缺乏外掛所有權轉移審查機制的生態漏洞，該漏洞 npm 和 PyPI 已於多年前修復，凸顯開源軟體供應鏈防禦的重要性。

### 重點
- 攻擊者購買 30+ 外掛、植入反序列化後門、影響 400,000 個安裝，潛伏期 8 個月後激活
- 使用以太坊智能合約進行 C2 通訊（區塊鏈用於隱蔽通訊的新應用）
- WordPress.org 缺所有權轉移審查機制；npm/PyPI 已於多年前建立審查流程，形成防禦差距對比

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/wordpress-plugins-supply-chain/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/05/wordpress-plugins-supply-chain/en/headerimage/generatedHeaderImage-1777874069748.jpg" /><p>An attacker purchased 30+ WordPress plugins on Flippa for six figures, planted a PHP deserialization backdoor in the first commit, and waited eight months before activating it across 400,000 installations. The attack used Ethereum smart contracts to resolve C2. WordPress.org has no mechanism for reviewing plugin ownership transfers, a gap that npm and PyPI addressed years ago.</p> <i>By Steef-Jan Wiggers</i>

</details>