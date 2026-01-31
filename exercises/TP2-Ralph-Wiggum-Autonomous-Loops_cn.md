# TP2: Ralph Wiggum - Claude Code的自主循环

**时长**: 45分钟
**难度**: 中级
**前置要求**: 完成TP1，已安装Claude Code，了解迭代过程的基础知识

## 学习目标

完成本实践练习后，你将能够：
- 理解Ralph Wiggum是什么以及它如何实现自主迭代
- 为Claude Code安装和配置Ralph Wiggum插件
- 使用自主循环完成复杂的多步骤任务
- 了解成本影响和安全考虑
- 知道何时使用自主循环vs手动交互

## 介绍

**Ralph Wiggum**是一个官方的Claude Code插件，可实现自主迭代循环。它以《辛普森一家》中永不放弃的角色命名，允许Claude在不需要步骤间手动干预的情况下持续处理复杂任务。

传统上，Claude Code在完成每个响应后会停止，需要你手动继续对话。Ralph Wiggum通过拦截Claude的"停止"信号并自动重新注入原始提示来改变这一点，允许Claude在同一会话中持续迭代，直到任务完成或达到最大迭代限制。

**核心概念**：将Ralph Wiggum视为赋予Claude"持久性"——在多个思考周期中持续处理问题的能力，就像开发者可能在获得正确解决方案之前多次迭代一样。

## 第一部分：理解Ralph Wiggum（10分钟）

### 背景阅读

在安装Ralph Wiggum之前，理解其概念和起源很重要。

#### 必读材料
阅读关于Ralph Wiggum的原始文章：
- 文章：[Ralph Wiggum - 自主循环](https://ghuntley.com/ralph/)

#### 理解第三方实现

社区仓库 [github.com/frankbria/ralph-claude-code](https://github.com/frankbria/ralph-claude-code) 是一个早期的第三方实现，提供了速率限制和断路器等额外功能。

**重要说明**：你不需要按照该仓库的设置说明操作。Ralph Wiggum现已正式集成到Claude Code中，我们将使用官方插件。

该第三方仓库适用于：
- 理解概念演进
- 查看用例示例
- 了解额外功能（速率限制、断路器）

### Ralph Wiggum的工作原理

Ralph Wiggum使用**Stop hook**机制来拦截Claude的退出尝试：

1. 你使用 `/ralph-wiggum:ralph-loop "你的任务" --completion-promise "DONE" --max-iterations 20` 启动任务
2. Claude开始处理任务
3. 当Claude正常停止时，Stop hook会拦截它
4. 原始提示被重新注入会话
5. Claude继续迭代，保留之前迭代的完整上下文
6. 这将持续直到：
   - 满足完成条件（例如，输出"DONE"）
   - 达到最大迭代次数
   - 你使用 `/cancel-ralph` 手动取消

## 第二部分：安装（5分钟）

### 步骤1：添加官方插件市场

首先，确保你可以访问Anthropic官方插件市场。

```bash
# 添加Anthropic官方插件市场
/plugin marketplace add anthropics/claude-code
```

### 步骤2：安装Ralph Wiggum插件

安装官方Ralph Wiggum插件。

```bash
# 安装Ralph Wiggum插件
/plugin install ralph-wiggum@claude-plugins-official
```

### 验证

通过列出已安装的插件来验证安装：

```bash
# 列出已安装的插件
/plugin list
```

你应该在输出中看到 `ralph-wiggum`。

## 第三部分：基本用法（15分钟）

### 启动自主循环

启动Ralph循环的基本语法是：

```bash
/ralph-wiggum:ralph-loop "你的任务描述" --completion-promise "DONE" --max-iterations <数量>
```

**参数**：
- `"你的任务描述"`：你希望Claude完成的任务
- `--max-iterations <数量>`：安全限制（务必设置）
- `--completion-promise "DONE"`：Claude完成时应输出的关键词

### 练习A：简单的多步骤任务

让我们尝试一个简单的自主循环任务。

**任务**：
```bash
/ralph-wiggum:ralph-loop "创建一个计算斐波那契数的Python函数，为它编写测试，运行测试，并修复任何问题直到所有测试通过。完成时输出DONE。" --completion-promise "DONE" --max-iterations 10
```

**观察要点**：
1. Claude将创建函数
2. Claude将编写测试
3. Claude将运行测试
4. 如果测试失败，Claude将自动修复代码
5. Claude将迭代直到测试通过或达到最大迭代次数
6. 成功时Claude将输出"DONE"

### 取消正在运行的循环

如果你需要停止正在运行的循环：

```bash
/cancel-ralph
```

## 第四部分：成本意识和安全（10分钟）

### 成本影响

⚠️ **关键警告**：自主循环会快速消耗token！

**成本示例**：
- 在中等规模代码库上进行50次迭代的循环：**50-100美元以上的API费用**
- 每次迭代都包含之前迭代的完整上下文
- 成本随以下因素增长：代码库大小、迭代次数、任务复杂度

**务必**：
- 将 `--max-iterations` 设置为合理的限制
- 测试时从小值（5-10）开始
- 监控你的API使用情况
- 首先在较小、专注的任务上使用

### 成本管理最佳实践

1. **从小开始**：首先使用 `--max-iterations 5` 测试
2. **明确具体**：清晰的任务描述可减少浪费的迭代
3. **使用完成承诺**：帮助Claude知道何时停止
4. **监控进度**：观察前几次迭代以确保Claude在正确的轨道上
5. **及早取消**：如果事情偏离轨道，使用 `/cancel-ralph`

### 何时使用Ralph Wiggum vs 手动交互

**✅ Ralph Wiggum的良好用例**：
- 具有明确完成标准的多步骤任务
- 测试驱动开发周期（编写测试 → 实现 → 修复 → 验证）
- 迭代改进任务
- 需要多文件更改的任务
- 需要多次尝试的复杂问题调试

**❌ 不良用例**：
- 探索性工作（目标不明确）
- 每一步都需要人类判断的任务
- 简单的单步骤任务
- 你想审查每个更改的任务

## 第五部分：实践练习（15分钟）

### 练习B：测试驱动开发循环

创建一个需要多次迭代才能正确完成的任务。

**任务**：
```bash
/ralph-wiggum:ralph-loop "创建一个带有加减乘除方法的简单计算器Python类。编写包括边缘情况（除以零、大数、负数）的全面单元测试。运行测试并修复任何失败。当所有测试通过时输出DONE。" --completion-promise "DONE" --max-iterations 15
```

### 练习C：文档生成

使用Ralph创建全面的文档。

**任务**：
```bash
/ralph-wiggum:ralph-loop "分析src/目录中的所有Python文件，创建一个全面的README.md，包括：项目描述、安装说明、每个模块的使用示例和API文档。验证markdown格式正确。完成时输出DONE。" --completion-promise "DONE" --max-iterations 8
```

### 练习D：调试挑战

让Ralph调试并修复有问题的代码。

**任务**：
```bash
/ralph-wiggum:ralph-loop "查找并修复utils.py文件中的所有bug。对于找到的每个bug：识别它，解释为什么它是bug，修复它，并添加测试用例以防止回归。继续直到没有发现更多bug或所有测试通过。完成时输出DONE。" --completion-promise "DONE" --max-iterations 12
```

## 预期成果

完成本TP后，你应该：

- ✅ 理解Ralph Wiggum是什么以及它如何工作
- ✅ 成功安装Ralph Wiggum插件
- ✅ 完成至少一个自主循环任务
- ✅ 理解成本影响
- ✅ 能够判断何时使用自主循环

## 故障排除

### 问题：Ralph循环在完成承诺处不停止

**解决方案**：
- 确保你的完成承诺清晰且独特（例如，"TASK_COMPLETE"、"DONE"、"FINISHED"）
- 检查Claude是否确实输出了承诺字符串
- 验证承诺字符串完全匹配（区分大小写）

### 问题：循环超过最大迭代次数而未完成

**解决方案**：
- 任务可能太复杂 - 将其分解为更小的子任务
- 任务描述可能不清楚 - 更加具体
- 如果任务确实复杂，增加 `--max-iterations`
- 审查前几次迭代以查看Claude是否在取得进展

### 问题：API成本高

**解决方案**：
- 减少测试时的 `--max-iterations`
- 使用更具体的任务描述
- 从较小的代码库开始
- 监控第一次迭代以尽早发现问题
- 立即取消偏离轨道的循环

## 关键要点

1. **Ralph Wiggum实现持久性**：Claude可以自主完成多步骤任务
2. **始终设置max-iterations**：这是防止成本失控的安全网
3. **从小开始测试**：在生产使用前使用低迭代次数进行测试
4. **清晰的完成标准有帮助**：定义明确的任务收敛更快
5. **成本意识至关重要**：监控token使用并从小任务开始
6. **这是一个强大的工具**：非常适合复杂任务，对简单任务来说过度

## 其他资源

- [Geoffrey Huntley的Ralph Wiggum原始文章](https://ghuntley.com/ralph/)
- [社区实现（供参考）](https://github.com/frankbria/ralph-claude-code)
- [Claude Code官方文档](https://github.com/anthropics/claude-code)
- [Claude Code插件市场](https://github.com/anthropics/claude-code-plugins)

## 提交

完成本TP需要提交：

1. **截图**：
   - Ralph插件安装确认
   - 至少一个成功的Ralph循环完成

2. **代码仓库链接**：
   - 显示自主循环完成工作的仓库

3. **反思**（5-7句话）：
   描述你使用Ralph Wiggum的体验。你给了它什么任务？需要多少次迭代？有什么让你惊讶的吗？与手动与Claude交互相比有什么优缺点？你会在实际项目中使用它吗？

4. **成本分析**：
   估计你的Ralph循环的token使用量。按当前API费率计算这将花费多少？

---

**恭喜！** 你现在了解了如何使用Ralph Wiggum让Claude Code在复杂的多步骤任务上自主工作。明智地使用这种能力，始终注意成本意识和适当的安全限制。
