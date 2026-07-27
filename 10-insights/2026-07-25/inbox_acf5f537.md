---
id: inbox_acf5f537
date: 2026-07-25
source_ref: "[[00-inbox/2026-07-25/0123-medium-towards-data-science-the-fluid-simulator-that-doesnt-solve-th-27cc]]"
title: "The Fluid Simulator That Doesn’t Solve the Fluid Equations"
url: https://towardsdatascience.com/the-fluid-simulator-that-doesnt-solve-the-fluid-equations/
source: medium-towards-data-science
published_at: 2026-07-25T13:00:00+00:00
fetched_at: 2026-07-27T01:39:17.415659+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文介紹格子 Boltzmann 方法（LBM）進行流體動力學模擬，以之替代求解傳統 Navier-Stokes 偏微分方程組。作者從第一性原理推導 LBM 理論，並以 C++ 實作卡門渦街（Kármán Vortex Street）的完整模擬，在超級電腦上執行。LBM 將流體流動轉化為格點上的粒子碰撞與傳播過程，自然地適應平行計算，提供計算物理的高效替代途徑。此方法在 CFD 應用中日益普及，特別是對需要高可擴展性的大規模模擬。"
key_points:
  - "LBM 迴避求解複雜的 Navier-Stokes 方程，改採離散粒子碰撞模型，降低計算複雜度"
  - "格子 Boltzmann 演算法天生適合 GPU/多核平行計算，可在超級電腦上高度可擴展"
  - "從第一性原理完整推導至卡門渦街模擬實作，展示物理直觀性與計算效率結合的典範"
tags: [lattice-boltzmann-method, computational-physics, fluid-dynamics, supercomputing, cfd]
topics: []
importance: 1
novelty: 2
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## The Fluid Simulator That Doesn’t Solve the Fluid Equations

本文介紹格子 Boltzmann 方法（LBM）進行流體動力學模擬，以之替代求解傳統 Navier-Stokes 偏微分方程組。作者從第一性原理推導 LBM 理論，並以 C++ 實作卡門渦街（Kármán Vortex Street）的完整模擬，在超級電腦上執行。LBM 將流體流動轉化為格點上的粒子碰撞與傳播過程，自然地適應平行計算，提供計算物理的高效替代途徑。此方法在 CFD 應用中日益普及，特別是對需要高可擴展性的大規模模擬。

### 重點
- LBM 迴避求解複雜的 Navier-Stokes 方程，改採離散粒子碰撞模型，降低計算複雜度
- 格子 Boltzmann 演算法天生適合 GPU/多核平行計算，可在超級電腦上高度可擴展
- 從第一性原理完整推導至卡門渦街模擬實作，展示物理直觀性與計算效率結合的典範

**原文：** [medium-towards-data-science](https://towardsdatascience.com/the-fluid-simulator-that-doesnt-solve-the-fluid-equations/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I generated a Kármán vortex street without solving a single fluid equation. Here's how the Lattice Boltzmann Method gets there instead, derived from first principles, implemented in C++, and run on a supercomputer. 
 The post The Fluid Simulator That Doesn’t Solve the Fluid Equations appeared first on Towards Data Science .

</details>