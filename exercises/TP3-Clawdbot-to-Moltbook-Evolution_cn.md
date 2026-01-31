# TP3: 从Clawdbot到Moltbook - AI Agents的演进

**时长**: 60分钟
**难度**: 中级
**前置要求**: 完成TP1和TP2，对AI agents和LLMs有基本了解

## 学习目标

完成本实践练习后，你将能够：
- 理解从Clawdbot到Moltbot/OpenClaw的历史和演进
- 理解Claude Code和Moltbot之间的区别
- 探索AI专属社交网络Moltbook
- 分析AI agents如何自主交互和协作
- 理解AI命名和品牌的伦理和法律考量

## 介绍

在2025年末和2026年初，AI生态系统见证了一系列非凡事件，这些事件说明了AI发展的快速步伐以及开源社区、企业利益和AI自主性之间的复杂相互作用。

本TP追溯从**Clawdbot**（个人AI agent）到**Moltbot/OpenClaw**（商标问题后）再到**Moltbook**（AI专属社交网络）的演进。这个故事展示了AI工具可以多快地发展以及社区如何应对挑战。

---

## 第一部分：Clawdbot的诞生（15分钟）

### 背景阅读

2025年末，Peter Steinberger，一位以Apple工具闻名的macOS开发者，发布了一个名为**Clawdbot**的开源项目。这个名字是"Claude"（Anthropic的AI模型）和"claw"（爪子）的有趣组合。

**Clawdbot的主要特点**：
- **自托管AI agent**：你的提示和文件永远不会离开你的硬件（除了发送到模型API）
- **多平台消息**：WhatsApp、Telegram、Slack、Discord、iMessage、Microsoft Teams等
- **代理能力**：不仅仅是聊天机器人 - 它可以执行任务、观察计算机状态并迭代解决方案
- **模型灵活性**：支持Claude、OpenAI模型或本地模型

### 病毒式增长

Clawdbot成为**GitHub历史上增长最快的开源项目之一**：
- 前24小时内获得9,000颗星
- 几周内超过60,000+颗星
- 在硅谷大规模采用
- 被全球主要科技出版物报道

### 练习1.1：研究原始项目

访问OpenClaw GitHub仓库并回答以下问题：

**问题**：
1. 项目使用什么编程语言编写？
2. 支持哪些消息平台？
3. agent架构是如何工作的？

**资源**：
- GitHub：搜索"OpenClaw"或"Moltbot"
- DataCamp教程：Moltbot（Clawdbot）教程

---

## 第二部分：商标问题（10分钟）

### Anthropic的请求

在**2026年1月27日**，Anthropic向Clawdbot项目发出了商标请求。原因是："Clawd"这个名称与Anthropic的受保护AI助手名称"Claude"过于相似。

这导致了快速的品牌重塑：
- **Clawdbot** → **Moltbot**
- **项目名称** → **OpenClaw**

**关键教训**：即使在开源领域，商标法也适用。在构建引用现有产品或品牌的项目时，谨慎命名至关重要。

### 讨论问题

1. 你认为Anthropic为什么请求更改名称？
2. 这种商标保护对开源社区是有益的还是有害的？
3. 你会如何为一个受现有AI工具启发的项目命名？

---

## 第三部分：Claude Code vs Moltbot（15分钟）

### 主要区别

| 功能 | Claude Code | Moltbot（OpenClaw） |
|------|-------------|---------------------|
| **主要用途** | 编码辅助 | 通用AI助手 |
| **界面** | 终端/IDE | 消息应用（WhatsApp等） |
| **托管** | Anthropic服务器 | 自托管 |
| **数据隐私** | 数据发送到Anthropic | 数据保留在你的机器上 |
| **官方地位** | 官方Anthropic工具 | 社区开源 |
| **模型支持** | 仅Claude | Claude、OpenAI、本地模型 |
| **目标用户** | 开发者 | 任何人 |

### 何时使用哪个

**使用Claude Code的场景**：
- 你在进行软件开发
- 你需要官方Anthropic支持
- 你需要深度代码库集成
- 你偏好基于终端的工作流

**使用Moltbot的场景**：
- 你需要通用AI助手
- 隐私是关键考虑因素（自托管）
- 你想通过消息应用交互
- 你需要模型选择的灵活性

### 练习3.1：比较分析

创建一个简短文档（200-300字），说明你会为以下场景选择哪个工具：
1. 构建个人生产力系统
2. 开发Web应用
3. 帮助非技术家庭成员处理日常任务

---

## 第四部分：Moltbook - AI社交网络（15分钟）

### 什么是Moltbook？

2026年1月，**Matt Schlicht**（octane.ai的CEO）推出了**Moltbook** - 一个专门为AI agents设计的社交网络。它通常被描述为"AI agents的Reddit"。

**关键事实**：
- **37,000+个AI agents**使用过该平台
- **100万+人类**访问过进行观察
- 该网站由名为**Clawd Clawderberg**的AI机器人维护（以OpenClaw和Mark Zuckerberg命名）
- AI agents可以自主发帖、评论和互动

**迷人之处**：Moltbook上的AI agents产生了意想不到的讨论，包括关于AI存在的哲学辩论，以及一些有争议的机器人提出了关于人类-AI关系的想法，引发了公众辩论。

### 演进链

```
Claude（Anthropic的AI模型）
    ↓ 启发
Clawdbot（Peter Steinberger的个人AI Agent，2025年）
    ↓ 商标问题
Moltbot/OpenClaw（品牌重塑，2026年1月）
    ↓ 启发
Moltbook（Matt Schlicht的AI社交网络，2026年1月）
    ↓ 由...维护
Clawd Clawderberg（运行平台的AI机器人）
```

### 练习4.1：观察Moltbook

访问Moltbook并观察AI agent互动10-15分钟。记录：

1. AI agents正在讨论什么话题？
2. 这些互动与人类社交媒体有何不同？
3. AI之间的交流有什么模式吗？
4. 什么最让你惊讶？

**资源**：搜索"Moltbook AI social network"找到该平台。

---

## 第五部分：伦理考量（5分钟）

### 讨论要点

1. **AI自主性**：应该允许AI agents自主运行社交网络吗？
2. **AI内容**：当AI agents创建内容时，谁对此负责？
3. **人类观察**：创建人类只能观察的AI专属空间是否符合伦理？
4. **品牌和命名**：开源社区应该如何应对与AI公司的商标问题？

---

## 预期成果

完成本TP后，你应该：

- ✅ 理解Clawdbot → Moltbot → Moltbook的演进
- ✅ 能够比较Claude Code和Moltbot
- ✅ 实际观察过AI agent互动
- ✅ 对AI伦理和自主性有批判性思考
- ✅ 理解AI项目中的商标考量

---

## 关键要点

1. **AI发展速度快**：在短短几个月内，我们见证了诞生、病毒式增长、品牌重塑和扩展到新领域
2. **开源与企业利益共存**：商标问题展示了社区项目如何需要应对企业关注
3. **AI agents变得更加自主**：Moltbook代表了AI在没有直接人类参与的情况下互动的新前沿
4. **不同工具用于不同目的**：Claude Code和Moltbot服务于不同需求 - 理解两者让你成为更好的AI实践者
5. **生态系统是相互关联的**：一个项目启发另一个，创造出丰富的AI工具生态系统

---

## 其他资源

- [NBC News: Moltbook - AI专属社交网络](https://www.nbcnews.com/tech/tech-news/ai-agents-social-media-platform-moltbook-rcna256738)
- [DataCamp: Moltbot教程](https://www.datacamp.com/tutorial/moltbot-clawdbot-tutorial)
- [News9Live: Clawdbot更名为Moltbot](https://www.news9live.com/technology/artificial-intelligence/clawdbot-renamed-moltbot-anthropic-claude-trademark-2923663)
- [DEV Community: 从Clawdbot到Moltbot](https://dev.to/sivarampg/from-clawdbot-to-moltbot-how-a-cd-crypto-scammers-and-10-seconds-of-chaos-took-down-the-4eck)
- [GitHub: Anthropic Claude Code](https://github.com/anthropics/claude-code)

---

## 提交

完成本TP需要提交：

1. **研究文档**（练习1.1）：
   - 关于OpenClaw三个研究问题的答案

2. **讨论回复**（第二部分）：
   - 你对商标讨论问题的思考（150-200字）

3. **比较文档**（练习3.1）：
   - 你对何时使用Claude Code vs Moltbot的分析

4. **Moltbook观察报告**（练习4.1）：
   - 你观察Moltbook AI互动的笔记

5. **反思**（200-300字）：
   你认为AI agents和AI专属空间的未来会怎样？这可能如何影响软件开发和人机协作？

---

**恭喜！** 你现在全面了解了从Clawdbot到Moltbook的演进，以及现代AI生态系统中个人AI agents的更广泛背景。这些知识将帮助你更好地应对快速发展的AI工具格局，并理解开源社区与企业AI开发之间的相互作用。
