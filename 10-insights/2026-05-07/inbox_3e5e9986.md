---
id: inbox_3e5e9986
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-medium-stackademic-the-single-entry-point-paradox-high-avai-89b7]]"
title: "The Single Entry Point Paradox: High-Availability Without a Single Point of Failure"
url: https://blog.stackademic.com/the-single-entry-point-paradox-high-availability-without-a-single-point-of-failure-120c6a30130c?source=rss----d1baaa8417a4---4
source: medium-stackademic
published_at: 2026-05-07T13:37:01+00:00
fetched_at: 2026-05-08T07:59:56.317946+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章解答系統設計中的悖論：若所有流量經過單一入口點（Load Balancer 或 API Gateway），不是就有單點故障風險嗎？答案是否定的，透過 DNS 層級分佈、健康檢查和 Round Robin 實現容錯。單一入口點實際上是功能概念而非物理概念：DNS 將域名解析到多個 Load Balancer 實例（不同機房、不同 IP），客戶端靠 Round Robin 輪流指向不同 IP；當某個節點故障，健康檢查自動移除其 IP，新用戶不再收到該 IP。關鍵權衡是 TTL（Time To Live）：高 TTL（如 3600 秒）減少 DNS 查詢開銷但故障恢復慢，低 TTL（如 60 秒）恢復快但增加 DNS 開銷。Load Balancer 只做流量分佈，API Gateway 進一步處理限流、認證、請求轉換。"
key_points:
  - "Single Entry Point 是功能概念而非物理概念：DNS 名稱背後實際有多個 LB 實例分散在不同機房和 IP（如 3.14.x.x、5.8.x.x、17.65.x.x）"
  - "Round Robin + 健康檢查提供容錯：故障節點自動從 DNS 回應移除，新請求不再路由至死節點；TTL 決定恢復速度權衡"
  - "API Gateway vs Load Balancer：Gateway 提供限流、認證、請求轉換等應用感知功能，LB 只做基礎流量分佈"
tags: [system-design, load-balancing, dns, high-availability, api-gateway]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The Single Entry Point Paradox: High-Availability Without a Single Point of Failure

文章解答系統設計中的悖論：若所有流量經過單一入口點（Load Balancer 或 API Gateway），不是就有單點故障風險嗎？答案是否定的，透過 DNS 層級分佈、健康檢查和 Round Robin 實現容錯。單一入口點實際上是功能概念而非物理概念：DNS 將域名解析到多個 Load Balancer 實例（不同機房、不同 IP），客戶端靠 Round Robin 輪流指向不同 IP；當某個節點故障，健康檢查自動移除其 IP，新用戶不再收到該 IP。關鍵權衡是 TTL（Time To Live）：高 TTL（如 3600 秒）減少 DNS 查詢開銷但故障恢復慢，低 TTL（如 60 秒）恢復快但增加 DNS 開銷。Load Balancer 只做流量分佈，API Gateway 進一步處理限流、認證、請求轉換。

### 重點
- Single Entry Point 是功能概念而非物理概念：DNS 名稱背後實際有多個 LB 實例分散在不同機房和 IP（如 3.14.x.x、5.8.x.x、17.65.x.x）
- Round Robin + 健康檢查提供容錯：故障節點自動從 DNS 回應移除，新請求不再路由至死節點；TTL 決定恢復速度權衡
- API Gateway vs Load Balancer：Gateway 提供限流、認證、請求轉換等應用感知功能，LB 只做基礎流量分佈

**原文：** [medium-stackademic](https://blog.stackademic.com/the-single-entry-point-paradox-high-availability-without-a-single-point-of-failure-120c6a30130c?source=rss----d1baaa8417a4---4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The “Single Entry Point” Paradox: Building High-Availability Systems Without a Single Point of Failure In system design, we often talk about having a single entry point for a client. Whether it’s an API Gateway or a Load Balancer, this entry point acts as the front door to your entire ecosystem of services. But this raises a critical question: If everything goes through one door, isn’t that a Single Point of Failure (SPOF)? The short answer is no — but the “how” involves a clever combination of DNS tricks, distributed infrastructure, and health management. Here is a breakdown of how modern architectures handle traffic distribution and resilience. Photo by Dima Pechurin on Unsplash 1. The Entry Point: Gateway or Load Balancer? When a client makes a request, it first hits an entry point. Depending on the complexity of your architecture, this is usually one of two things: Load Balancer (LB): Primarily focuses on distributing incoming network traffic across multiple backend servers. API Gateway: A more advanced “front door” that handles not just routing, but also Rate Limiting, Authentication logic, and Request Transformation. While a Load Balancer like AWS ELB can route requests to different services based on request path or host headers, it is technically not a Gateway because it lacks these specialized “application-aware” features. 2. Solving the SPOF: The DNS Layer If we point our domain (e.g., api.myapp.com) to a single IP address, and that machine dies, our system goes dark. To prevent this, we use DNS-level distribution. When you use a service like AWS ELB, you aren’t pointing your domain to a single machine. You are pointing it to a DNS name (e.g., my-load-balancer-123.aws.com). How DNS Distributes Traffic: Multiple IPs: Behind that one DNS name, there are actually multiple Load Balancer instances running on different physical machines in different data centers. Round Robin: When a client asks DNS for the IP of api.myapp.com, the DNS server returns a list of IPs (e.g., 3.14.x.x, 5.8.x.x, 17.65.x.x). Client Selection: The client (browser or mobile app) typically picks one of these IPs to initiate the connection. By rotating which IP is listed first (Round Robin), different users are sent to different physical Load Balancer instances. 3. What Happens When a Node Dies? No hardware is immortal. Eventually, a Load Balancer instance will fail. Systems remain “Highly Available” through a process of Health Checks. Detection: AWS or your infrastructure provider constantly “pings” the Load Balancer nodes. Removal: If a node stops responding, its IP is immediately removed from the DNS response. New clients will no longer receive the IP of the dead node. The “Cache” Problem: Browsers often cache DNS lookups. If a browser has cached the IP of a dead node, the request might temporarily fail. DNS records have a “lifespan.” If the TTL is set to 60 seconds, the browser will check for a fresh IP every minute. High TTL means fewer DNS lookups (faster for the user) but longer downtime if a node fails. Low TTL means faster recovery but more overhead. 4. The Path of a Request To visualize the whole flow, imagine a user logging into an app: Client → DNS: The client resolves myapp.com and gets three healthy IPs. Client → Load Balancer: The client picks one IP and hits an LB instance. LB → API Gateway: The LB sends the request to the Gateway, which checks if the user is hitting the “Rate Limit” or needs “Authentication.” Gateway → Auth Service: If it’s a /login request, the Gateway routes it to the specific Auth Service . Gateway → Email Service: Once logged in, the user wants to send an email. The Email Service will handle this. Conclusion A “Single Entry Point” is a functional concept, not a physical one. By distributing that entry point across multiple machines and using DNS to point to them dynamically, we gain the simplicity of a single URL with the power of a distributed, fault-tolerant system. Whether you are using an AWS ELB for simple routing or a full-scale API Gateway for complex logic, the underlying principle remains: Redundancy is the only cure for failure. The Single Entry Point Paradox: High-Availability Without a Single Point of Failure was originally published in Stackademic on Medium, where people are continuing the conversation by highlighting and responding to this story.

</details>