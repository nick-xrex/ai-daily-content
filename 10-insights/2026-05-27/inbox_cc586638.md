---
id: inbox_cc586638
date: 2026-05-27
source_ref: "[[00-inbox/2026-05-27/2345-infoq-architecture-how-linkedin-identified-a-kernel-lock-co-c7d3]]"
title: "How LinkedIn Identified a Kernel Lock Contention Issue Causing Recurring System Freezes"
url: https://www.infoq.com/news/2026/05/linkedin-kernel-lock-freeze/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-05-27T18:00:00+00:00
fetched_at: 2026-05-27T23:54:48.994160+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LinkedIn 工程师在排查用户 feed 数据库周期性故障时，采用 eBPF off-CPU profiling 技术诊断内核级锁竞争问题。与传统 CPU profiling 不同，off-CPU profiling 捕捉线程被 I/O 或锁阻塞的时间，无需修改应用代码。这项技术突破帮助 LinkedIn 识别并修复了长期无日志痕迹的间歇性故障，展示了 eBPF 在大规模系统诊断中的威力。"
key_points:
  - "eBPF off-CPU profiling：捕捉线程阻塞（I/O、锁等）而非 CPU 执行的时间，对诊断内核级性能问题更精确"
  - "实时诊断无日志痕迹的故障：系统自动恢复导致传统日志缺失，off-CPU 技术可绕过日志依赖"
  - "内核空间调试：不修改应用代码，直接从内核态捕捉锁竞争和调度延迟等底层问题"
tags: [ebpf-profiling, kernel-debugging, system-reliability, off-cpu-tracing]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## How LinkedIn Identified a Kernel Lock Contention Issue Causing Recurring System Freezes

LinkedIn 工程师在排查用户 feed 数据库周期性故障时，采用 eBPF off-CPU profiling 技术诊断内核级锁竞争问题。与传统 CPU profiling 不同，off-CPU profiling 捕捉线程被 I/O 或锁阻塞的时间，无需修改应用代码。这项技术突破帮助 LinkedIn 识别并修复了长期无日志痕迹的间歇性故障，展示了 eBPF 在大规模系统诊断中的威力。

### 重點
- eBPF off-CPU profiling：捕捉线程阻塞（I/O、锁等）而非 CPU 执行的时间，对诊断内核级性能问题更精确
- 实时诊断无日志痕迹的故障：系统自动恢复导致传统日志缺失，off-CPU 技术可绕过日志依赖
- 内核空间调试：不修改应用代码，直接从内核态捕捉锁竞争和调度延迟等底层问题

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/05/linkedin-kernel-lock-freeze/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

When LinkedIn engineers encountered short-lived, recurring outages where the database powering their user feed became unavailable and then recover without leaving helpful traces, they had to devise a novel approach to uncover the root cause using off-CPU profiling with eBPF. By Sergio De Simone

</details>