# TP1: 在GitHub上配置Claude Code

**时长**: 30分钟
**难度**: 初级
**前置要求**: GitHub账号，Git基础知识

## 学习目标

完成本实践练习后，你将能够：
- 在你的仓库中设置Claude Code GitHub集成
- 通过GitHub issues触发Claude Code
- 理解使用Claude Code的基本工作流程

## 介绍

Claude Code是一个AI助手，可以直接通过GitHub帮助你完成编码任务。配置完成后，你可以在issues或pull requests中提及`@claude`，Claude会自动响应并帮助你处理请求。

## 第一部分：仓库设置（10分钟）

### 步骤1：Fork或创建仓库

1. 前往GitHub，然后：
   - Fork一个现有仓库，或者
   - 为本练习创建一个新仓库

2. 确保你的仓库：
   - 是公开的，或者是私有的（如果你有权限在私有仓库中使用GitHub Apps）
   - 至少包含一个文件（如README.md）

### 步骤2：安装Claude Code GitHub App

在终端打开Claude Code，运行 ```/install-github-app```，按照说明操作
[参考文档](https://code.claude.com/docs/en/github-actions)

## 第二部分：基本配置（5分钟）

### 步骤3：创建CLAUDE.md文件（可选但推荐）

在仓库根目录创建一个名为`CLAUDE.md`的文件。这个文件为Claude提供项目上下文。

示例内容：
```markdown
# CLAUDE.md

## 项目概述

这是一个用于学习如何在GitHub中使用Claude Code的练习仓库。

## 开发指南

- 保持代码简洁并有良好的注释
- 遵循Python PEP 8风格指南
- 编写清晰的提交信息
```

**为什么重要**：CLAUDE.md文件帮助Claude理解你的项目上下文、编码标准和偏好。

## 第三部分：测试集成（10分钟）

### 步骤4：创建你的第一个Issue

1. 前往仓库的**Issues**标签页
2. 点击**"New Issue"**
3. 输入标题：`测试Claude Code集成`
4. 在描述中输入：
   ```
   @claude 你好！你能帮我创建一个简单的Python函数来计算两个数的和吗？
   ```
5. 点击**"Submit new issue"**

### 步骤5：观察Claude的响应

1. 等待片刻（通常10-30秒）
2. Claude会自动在你的issue上发布评论
3. Claude会显示正在处理的任务清单
4. 观察Claude：
   - 创建请求的代码
   - 将更改提交到新分支
   - 提供创建pull request的链接

### 步骤6：审查Claude的工作

1. 点击Claude提供的分支链接
2. 审查Claude创建的代码
3. 如果Claude创建了PR链接，点击它来创建pull request
4. 审查pull request，如果一切正常就合并它

## 第四部分：练习场景（5分钟）

现在你理解了基础知识，尝试这些额外的练习：

### 练习A：代码审查
创建一个新issue并请求：
```
@claude 你能审查这段代码并建议改进吗？
[粘贴一些简单的代码]
```

### 练习B：Bug修复
创建一个issue：
```
@claude 我的代码在第X行有一个bug。你能帮我修复吗？
```

### 练习C：文档
请求Claude：
```
@claude 你能为我的主Python文件添加文档吗？
```

## 预期成果

完成本TP后，你应该拥有：
- ✅ 在你的仓库中工作正常的Claude Code集成
- ✅ 至少一个在Claude帮助下成功解决的issue
- ✅ 理解基本工作流程：Issue → Claude响应 → 分支 → PR → 合并
- ✅ 包含项目上下文的CLAUDE.md文件

## 故障排除

### 问题：Claude不响应我的issue
**解决方案**：
- 确保你输入的是`@claude`（不是@Claude或@CLAUDE）
- 验证GitHub App是否正确安装
- 检查issue是否在安装了Claude的仓库中
- 多等待一会儿（有时需要一分钟）

### 问题：Claude创建了代码但我看不到
**解决方案**：
- Claude会自动创建新分支
- 在Claude的评论中查找分支名称
- 点击分支链接查看代码

### 问题：我想给Claude更具体的指令
**解决方案**：
- 使用CLAUDE.md文件设置项目级偏好
- 在issue描述中更加具体
- 包含代码片段、文件路径和明确的需求

## 最佳实践

1. **具体明确**：提供的细节越多，Claude就能更好地帮助你
2. **使用CLAUDE.md**：设置项目指南以获得一致的结果
3. **审查所有内容**：合并前始终审查Claude的代码
4. **迭代改进**：如果Claude的第一次尝试不完美，在后续评论中请求改进
5. **从小开始**：从简单任务开始以理解工作流程

## 其他资源

- [Claude Code文档](https://github.com/anthropics/claude-code)
- [Claude Code GitHub Action](https://github.com/anthropics/claude-code-action)
- [CLAUDE.md示例文件](https://github.com/search?q=filename%3ACLAUDE.md)

## 提交

完成本TP需要提交：
1. 安装了Claude Code的仓库链接
2. 至少一个Claude成功帮助你的issue链接
3. 合并的pull request截图
4. 简短反思（2-3句话）：你认为Claude Code在你的项目中最适合用于什么任务？

---

**恭喜！** 你已成功设置并测试了GitHub上的Claude Code。现在你可以使用这个强大的工具来协助编码任务、代码审查、文档编写等工作。
