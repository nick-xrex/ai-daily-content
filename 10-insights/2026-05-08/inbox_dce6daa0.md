---
id: inbox_dce6daa0
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0737-medium-stackademic-how-to-deploy-a-fine-tuned-llm-on-bitten-9100]]"
title: "How to Deploy a Fine-Tuned LLM on Bittensor’s Chutes AI"
url: https://blog.stackademic.com/how-to-deploy-a-fine-tuned-llm-on-bittensors-chutes-ai-366c4b89c7d4?source=rss----d1baaa8417a4---4
source: medium-stackademic
published_at: 2026-05-08T07:08:47+00:00
fetched_at: 2026-05-08T07:59:56.307365+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章詳細介紹如何在 Bittensor 的 Chutes AI（subnet 64）上部署微調後的大語言模型。Chutes AI 是一個去中心化的 AI 推理平台，透過礦工提供的計算資源提供模型部署和 API 調用。作者提供逐步教學：使用 chutes SDK 的 NodeSelector 配置硬體需求（如 gpu_count=1），利用 vLLM 高效推理引擎，設定並發控制參數，最後用 chutes deploy 命令部署。部署後可透過 Chutes API 或 Vercel AI SDK 進行模型推理。適合有基礎 Python 經驗的開發者快速上手去中心化 GPU 基礎設施部署。"
key_points:
  - "Chutes AI（Bittensor subnet 64）提供去中心化模型部署和推理，開發者無需關心區塊鏈細節，感受類似傳統 API 提供商"
  - "部署步驟：pip install chutes → chutes register → 配置 NodeSelector（gpu_count=1）和 build_vllm_chute → chutes deploy --accept-fee 部署"
  - "Concurrency 參數控制併發請求數，直接影響 GPU 記憶體消耗；vLLM 是高吞吐推理引擎，優化 LLM 批量推理"
tags: [bittensor, chutes-ai, llm-deployment, vllm, decentralized-gpu]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## How to Deploy a Fine-Tuned LLM on Bittensor’s Chutes AI

文章詳細介紹如何在 Bittensor 的 Chutes AI（subnet 64）上部署微調後的大語言模型。Chutes AI 是一個去中心化的 AI 推理平台，透過礦工提供的計算資源提供模型部署和 API 調用。作者提供逐步教學：使用 chutes SDK 的 NodeSelector 配置硬體需求（如 gpu_count=1），利用 vLLM 高效推理引擎，設定並發控制參數，最後用 chutes deploy 命令部署。部署後可透過 Chutes API 或 Vercel AI SDK 進行模型推理。適合有基礎 Python 經驗的開發者快速上手去中心化 GPU 基礎設施部署。

### 重點
- Chutes AI（Bittensor subnet 64）提供去中心化模型部署和推理，開發者無需關心區塊鏈細節，感受類似傳統 API 提供商
- 部署步驟：pip install chutes → chutes register → 配置 NodeSelector（gpu_count=1）和 build_vllm_chute → chutes deploy --accept-fee 部署
- Concurrency 參數控制併發請求數，直接影響 GPU 記憶體消耗；vLLM 是高吞吐推理引擎，優化 LLM 批量推理

**原文：** [medium-stackademic](https://blog.stackademic.com/how-to-deploy-a-fine-tuned-llm-on-bittensors-chutes-ai-366c4b89c7d4?source=rss----d1baaa8417a4---4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Exploring Chutes AI in detail and deploying a fine-tuned AI model on Bittensor Basic knowledge of web development, LLMs, and the Bittensor ecosystem will be sufficient for working through the contents of this article. Fond of cryptocurrency? Explore everything related to the Ethereum blockchain with this free, comprehensive dashboard built using Next.js . Get your article audibles here ! I made this tool which makes audio files accessible for any non-paywall Medium articles! Want more content? Visit my tech blog for more articles, AI and software tools, and free shareable resources. Introduction In past articles, we covered Bittensor and the many intricate components that make up its network. We also explored subnet 64, one of the most prominent subnets on Bittensor. In this short article, we will cover deploying a fine-tuned model on Chutes AI (known as subnet 64). If you are a developer with extensive Python experience, this will be an easy follow. I decided to write this small article to serve as a guide for people with limited Python experience so you too can deploy a fine-tuned model on Chutes AI. Bittensor Subnets and Subnet 64: Chutes AI This section will serve as a refresher on Bittensor and Chutes AI. Bittensor is essentially a decentralized AI network/economy which allows users and developers alike to offer incentivized AI services. Each subnet on Bittensor offers its own unique AI service with a unique economy of its own (alpha tokens). Each subnet is numbered and Chutes AI is a prominent subnet on Bittensor (subnet 64). Chutes AI offers the ability for others to deploy models of their own and for others to access via decentralized GPU infrastructure. Rather than rely on a sole provider to access these models, miners offer compute and host these models for inference via API endpoints using the Chutes API. In fact, we covered Chutes AI model inference using the Vercel AI SDK as it contains a customized package for specifically working with the Chutes API provider. Step-by-Step Guide to Model Deployment Now, we will simply proceed to creating and deploying a fine-tuned model. Understand that Chutes AI acts as a provider for you to access these models. You can follow along by cloning this GitHub repository . The directory we will focus on is demos/Demo78_Chutes_AI_Model_Deployment. Model inference with Chutes AI relies on miners (those who provide compute and the ability for inference) who are evaluated by validators based on their performance and rewarded accordingly (we touched on this key aspect of incentives with Bittensor). However, from a developer’s perspective, these blockchain mechanics are largely abstracted away, making the deployment workflow feel similar to working with a traditional AI inference provider. Ensure you have a Python environment setup for this article including the Python package manager as we will need to install the chutes Python package using pip: pip install chutes After that, we will use the chutes CLI command to register using: chutes register You need to register yourself first before you can deploy any model to Chutes AI. Once registration is complete, we can proceed to model deployment. The following Python script details how you can deploy a fine-tuned model on Chutes /codebase/finetuned_chutes_model.py: https://medium.com/media/df065bc4dcef5397cae428282a093278/href Key things to note: NodeSelector — NodeSelector is a configuration class from the Chutes SDK that defines the hardware requirements for your deployment. In this case, gpu_count=1 tells the Chutes platform to provision a single GPU node to run the model. build_vllm_chute — This is the core builder function from the Chutes SDK’s vLLM template. VLLM is a high-throughput inference engine optimized for LLMs, and build_vllm_chute wraps it into a deployable “chute”. Username and Model Name Parameters — These identify who owns the deployment and what model to serve. Username ties the chute to your Chutes AI account and the model_name points to the HuggingFace model repository path. Concurrency Parameter — This controls how many simultaneous inference requests the deployed chute can handle at once. Higher concurrency means more parallel requests, but also more GPU memory consumption. Readme Parameter — This is a markdown string that documents the chute on the Chutes AI platform. You can deploy this as a chute using the following bash command: chutes deploy finetuned_chute:chute --accept-fee That is all there is to it. Chutes AI is a neat subnet that is primarily used for deploying models. The fine-tuning happens elsewhere, but what Chutes allows you to do is deploy these models (“chutes”) to be accessible to anyone through the Chutes AI provider. Run Calls to Deployed Chutes Model Recall that the Chutes SDK is primarily used for the deployment and serving of models (“chutes”) whereas the Chutes API is used for inferring with those models. The following bash script details how you can infer with your deployed models using the Chutes API: https://medium.com/media/a80bb4a3796a8e95dee6069d091948f4/href Of course, you can also use the Vercel AI SDK along with the Chutes AI provider to infer with these models with greater complexity. We covered that in a separate article here . Conclusion In this short article, we covered how easy it is to deploy a fine-tuned model on Chutes AI. You do not need to be a Python expert to do this, the code base provided in this article is adequate enough for you to get started with the deployment process. In the list below, you will find links to the GitHub repository (used in this article), the Chutes AI documentation/provider package, and the Bittensor docs: GitHub Repository Chutes AI Documentation Bittensor Documentation Chutes AI Provider NPM Package I hope you found this article helpful and look forward to more in the future. Thank you! How to Deploy a Fine-Tuned LLM on Bittensor’s Chutes AI was originally published in Stackademic on Medium, where people are continuing the conversation by highlighting and responding to this story.

</details>