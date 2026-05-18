---
id: inbox_b60a544b
date: 2026-05-16
source_ref: "[[00-inbox/.../inbox_b60a544b]]"
title: "When \&#34;Distributed Backup\&#34; Isn&#39;t Actually Distributed: Lessons From the Coinbase Outage"
url: https://read.bytesizeddesign.com/p/a-room-got-too-hot-and-coinbase-went
source: substack-byte-sized-design
published_at: 2026-05-16T19:15:36+00:00
fetched_at: 2026-05-18T04:14:00.028050+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "2026年5月7日 AWS US-EAST-1 az4 数据中心冷却系统故障导致 Coinbase 故障7小时。Coinbase 匹配引擎部署在单一可用区以降低延迟，虽然拥有「分布式」备份，但该备份依赖同一故障域，未能自动转移。文章揭示关键矛盾：标榜「分布式备份」的系统若未针对具体故障模式测试，就不是真正的备份。作者指出高可用性（Multi-AZ）与灾难恢复（Multi-Region）本质不同，多数产品只有前者，原因是成本。Coinbase 恢复过程经历取消专用→拍卖模式→实时交易三个阶段，体现规范的事故响应；AWS SLA 赔偿仅约 10% 月度费用，无法覆盖实际业务损失（金融行业停机成本远超此数）。"
key_points:
  - "「分布式備份」陷阱：若備份住在同一 AZ / 同一故障域，AZ 故障連主從一起摧毀；故障轉移只對實際測試過的故障模式生效，未測試 = 假設"
  - "高可用性（Multi-AZ，HA）≠ 災難恢復（Multi-Region，DR）：前者防單區故障，後者防整個區域故障；AWS 按可用區隔離，區域隔離需主動構建、付費複製、事先測試"
  - "成本決策：跨區複製很貴（熱備雙倍計算費用），直到故障發生那一刻才顯得「廉價」；AWS SLA 補償（~10% 月費）遠低於實際損失（金融停機成本百萬級／小時）"
tags: [disaster-recovery, backup-strategy, high-availability-vs-dr, failure-domains, cost-vs-resilience]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## When \"Distributed Backup\" Isn't Actually Distributed: Lessons From the Coinbase Outage

2026年5月7日 AWS US-EAST-1 az4 数据中心冷却系统故障导致 Coinbase 故障7小时。Coinbase 匹配引擎部署在单一可用区以降低延迟，虽然拥有「分布式」备份，但该备份依赖同一故障域，未能自动转移。文章揭示关键矛盾：标榜「分布式备份」的系统若未针对具体故障模式测试，就不是真正的备份。作者指出高可用性（Multi-AZ）与灾难恢复（Multi-Region）本质不同，多数产品只有前者，原因是成本。Coinbase 恢复过程经历取消专用→拍卖模式→实时交易三个阶段，体现规范的事故响应；AWS SLA 赔偿仅约 10% 月度费用，无法覆盖实际业务损失（金融行业停机成本远超此数）。

### 重點
- 「分布式備份」陷阱：若備份住在同一 AZ / 同一故障域，AZ 故障連主從一起摧毀；故障轉移只對實際測試過的故障模式生效，未測試 = 假設
- 高可用性（Multi-AZ，HA）≠ 災難恢復（Multi-Region，DR）：前者防單區故障，後者防整個區域故障；AWS 按可用區隔離，區域隔離需主動構建、付費複製、事先測試
- 成本決策：跨區複製很貴（熱備雙倍計算費用），直到故障發生那一刻才顯得「廉價」；AWS SLA 補償（~10% 月費）遠低於實際損失（金融停機成本百萬級／小時）

**原文：** [substack-byte-sized-design](https://read.bytesizeddesign.com/p/a-room-got-too-hot-and-coinbase-went)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# When "Distributed Backup" Isn't Actually Distributed: Lessons From the Coinbase Outage

The May 2026 AWS thermal event, the latency-versus-resilience tradeoff that broke coinbase, and what happens when &#8220;distributed backup&#8221; isn&#8217;t actually distributed

</details>