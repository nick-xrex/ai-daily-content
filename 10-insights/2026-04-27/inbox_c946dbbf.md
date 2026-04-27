---
id: inbox_c946dbbf
date: 2026-04-27
source_ref: "[[00-inbox/2026-04-27/0956-infoq-architecture-spring-news-roundup-first-release-candid-30ef]]"
title: "Spring News Roundup: First Release Candidates of Boot, Security, Integration, Modulith, AMQP"
url: https://www.infoq.com/news/2026/04/spring-news-roundup-apr20-2026/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-04-27T02:30:00+00:00
fetched_at: 2026-04-27T10:04:57.923394+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Spring 生態在 2026 年 4 月下旬發布多個 RC 版本。Spring Boot 4.1.0-RC1 新增 OpenTelemetry Protocol (OTLP) SDK exporter 環境變數支援和 LazyConnectionDataSourceProxy；Spring Security 7.1.0-RC1 新增 anyOf() 方法和 PreFlightRequestFilter 支援；Spring Integration 7.1.0-RC1 重構 RedisLockRegistry 以支援 Redis 8.4+ 的 CAS/CAD 命令進行鎖更新；Spring Modulith 2.1.0-RC1 引入 @ModuleSlicing 注解避免測試衝突；Spring AMQP 4.1.0-RC1 改進錯誤處理；Spring for Apache Kafka 4.1.0-RC1 新增 ContainerProperties.ShareAckMode enum 和 AcknowledgementCommitCallback 支援。此波發布涵蓋 Boot、Security、Session、Integration、Modulith、AMQP、Kafka、Vault 等七個主要框架。"
key_points:
  - "Spring Boot 4.1.0-RC1：OTLP SDK exporter 環境變數 + LazyConnectionDataSourceProxy 改進事務管理"
  - "Spring Integration 7.1.0-RC1：RedisLockRegistry 利用 Redis 8.4+ 原生 CAS/CAD 指令優化鎖管理"
  - "Spring Modulith 2.1.0-RC1：@ModuleSlicing 注解解決多 @SpringBootApplication 整合測試衝突"
tags: [spring-framework, release-candidate, jvm, microservices]
topics: []
importance: 3
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Spring News Roundup: First Release Candidates of Boot, Security, Integration, Modulith, AMQP

Spring 生態在 2026 年 4 月下旬發布多個 RC 版本。Spring Boot 4.1.0-RC1 新增 OpenTelemetry Protocol (OTLP) SDK exporter 環境變數支援和 LazyConnectionDataSourceProxy；Spring Security 7.1.0-RC1 新增 anyOf() 方法和 PreFlightRequestFilter 支援；Spring Integration 7.1.0-RC1 重構 RedisLockRegistry 以支援 Redis 8.4+ 的 CAS/CAD 命令進行鎖更新；Spring Modulith 2.1.0-RC1 引入 @ModuleSlicing 注解避免測試衝突；Spring AMQP 4.1.0-RC1 改進錯誤處理；Spring for Apache Kafka 4.1.0-RC1 新增 ContainerProperties.ShareAckMode enum 和 AcknowledgementCommitCallback 支援。此波發布涵蓋 Boot、Security、Session、Integration、Modulith、AMQP、Kafka、Vault 等七個主要框架。

### 重點
- Spring Boot 4.1.0-RC1：OTLP SDK exporter 環境變數 + LazyConnectionDataSourceProxy 改進事務管理
- Spring Integration 7.1.0-RC1：RedisLockRegistry 利用 Redis 8.4+ 原生 CAS/CAD 指令優化鎖管理
- Spring Modulith 2.1.0-RC1：@ModuleSlicing 注解解決多 @SpringBootApplication 整合測試衝突

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/04/spring-news-roundup-apr20-2026/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/04/spring-news-roundup-apr20-2026/en/headerimage/java-istock-image-01-1777241266425.jpg" /><p>There was a flurry of activity in the Spring ecosystem during the week of April 20th, 2026, highlighting the first release candidates of: Spring Boot, Spring Security, Spring Integration, Spring Modulith, Spring AMQP, Spring for Apache Kafka and Spring Vault.</p> <i>By Michael Redlich</i>

</details>