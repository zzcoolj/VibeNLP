# TP3: Claude Code权限和YOLO模式

**时长**: 30分钟
**难度**: 初中级
**前置要求**: 完成TP1，已安装Claude Code

## 学习目标

完成本实践练习后，你将能够：
- 理解Claude Code的权限系统及其存在的原因
- 为不同操作配置权限规则
- 了解allowlist和blocklist方法的区别
- 了解何时以及如何安全使用YOLO模式
- 对安全性与便利性的权衡做出明智决策

## 介绍

Claude Code使用**权限系统**运行，旨在保护你免受意外操作的影响。默认情况下，Claude会在执行潜在危险操作之前请求你的批准，例如：

- 写入或修改文件
- 执行shell命令
- 发起网络请求
- 访问敏感目录

这个权限系统存在是因为AI助手可能会犯错或误解指令。在关键操作中有人工参与提供了安全网。

然而，不断批准每个操作可能会减慢你的工作流程，特别是对于重复性或低风险的任务。这就是**权限配置**和**YOLO模式**发挥作用的地方。

## 第一部分：理解权限系统（10分钟）

### 默认行为

当你启动Claude Code时，它默认以**安全模式**运行。这意味着：

1. **文件操作**：Claude在写入、编辑或删除文件前会询问
2. **Bash命令**：Claude在运行shell命令前会询问
3. **MCP工具**：Claude在使用Model Context Protocol工具前会询问

当Claude想要执行操作时，你会看到如下提示：
```
Claude wants to run: npm install express
Allow? [y/n/a]
```

响应选项：
- `y`（yes）：允许这个特定操作
- `n`（no）：拒绝这个操作
- `a`（always）：在本会话中允许这类操作

### 权限类型

| 权限类型 | 默认 | 风险级别 | 示例 |
|---------|------|---------|------|
| 读取文件 | ✅ 允许 | 低 | 读取源代码、配置 |
| 写入/编辑文件 | ⚠️ 询问 | 中 | 修改代码、创建文件 |
| 删除文件 | ⚠️ 询问 | 高 | 删除文件或目录 |
| Bash命令 | ⚠️ 询问 | 可变 | 运行脚本、安装包 |
| 网络请求 | ⚠️ 询问 | 中 | API调用、网页获取 |
| 系统命令 | ⚠️ 询问 | 高 | 系统配置更改 |

## 第二部分：配置权限（10分钟）

### 查看当前设置

查看当前权限设置：

```bash
# 查看所有设置
/config
```

### Allowlist方法

**allowlist**方法让你预先批准特定命令或模式。这是大多数用户推荐的方法。

**配置示例**：

```bash
# 允许特定的git命令
/allowed-tools Bash(git status)
/allowed-tools Bash(git diff*)
/allowed-tools Bash(git add*)
/allowed-tools Bash(git commit*)

# 允许npm/yarn命令
/allowed-tools Bash(npm install*)
/allowed-tools Bash(npm run*)
/allowed-tools Bash(yarn*)

# 允许Python执行
/allowed-tools Bash(python*)
/allowed-tools Bash(pytest*)
```

**模式语法**：
- `*` 匹配任意字符
- 精确匹配：`git status` 只匹配 `git status`
- 前缀匹配：`git*` 匹配所有以 `git` 开头的内容

### 会话 vs 项目 vs 用户设置

权限可以在三个级别配置：

1. **会话**：仅在当前Claude Code会话中有效（临时）
2. **项目**：保存在项目中的 `.claude/settings.json`（与团队共享）
3. **用户**：保存在 `~/.claude/settings.json`（个人，所有项目）

```bash
# 添加到项目设置
/allowed-tools --project Bash(npm run build)

# 添加到用户设置
/allowed-tools --user Bash(git*)
```

### 练习A：配置你的权限

为典型的Node.js项目设置合理的权限配置。

**步骤**：
1. 在项目目录中打开Claude Code
2. 允许常见的git操作
3. 允许npm/yarn命令
4. 允许测试执行
5. 使用 `/config` 验证

```bash
# 你的配置
/allowed-tools Bash(git status)
/allowed-tools Bash(git diff*)
/allowed-tools Bash(git add*)
/allowed-tools Bash(git commit*)
/allowed-tools Bash(git push*)
/allowed-tools Bash(git pull*)
/allowed-tools Bash(npm*)
/allowed-tools Bash(yarn*)
/allowed-tools Bash(npx jest*)
/allowed-tools Bash(npx prettier*)
/allowed-tools Bash(npx eslint*)
```

## 第三部分：YOLO模式（10分钟）

### 什么是YOLO模式？

**YOLO模式**（You Only Live Once / 只活一次）是终极便利功能，**自动批准所有操作**而不请求权限。启用后，Claude会立即执行任何操作而不提示你。

⚠️ **警告**：YOLO模式强大但可能危险。只有在你完全信任任务和环境时才使用它。

### 启用YOLO模式

有几种方式启用YOLO模式：

**方法1：命令行选项**
```bash
# 以YOLO模式启动Claude Code
claude --dangerously-skip-permissions
```

**方法2：会话中**
```bash
# 为当前会话启用YOLO模式
/dangerously-skip-permissions
```

### 何时使用YOLO模式

**✅ YOLO模式的安全场景**：
- 在一次性开发容器中工作（Docker）
- 在沙箱环境中测试
- 运行已理解的重复性任务
- 错误容易恢复的个人项目
- 在隔离环境中跟随教程
- 与Ralph Wiggum一起用于自主循环（TP2）

**❌ 危险场景 - 绝不使用YOLO模式**：
- 生产环境
- 包含敏感数据的仓库
- 共享的团队仓库（未经团队同意）
- 处理凭证或密钥时
- 不熟悉的代码库
- 未明确定义任务时

### 安全预防措施

如果你决定使用YOLO模式，请遵循这些安全准则：

1. **使用Git**：始终备份未提交的更改或在干净的分支上工作
2. **设置边界**：使用 `--max-turns` 限制操作数量
3. **隔离工作**：尽可能使用容器或虚拟机
4. **事后审查**：始终审查所做的更改
5. **有退出策略**：知道如何停止（Ctrl+C）和恢复（git checkout .）

### 练习B：安全的YOLO实验

在安全环境中练习使用YOLO模式。

**步骤**：

1. 创建新的测试目录：
```bash
mkdir ~/yolo-test && cd ~/yolo-test
git init
echo "# YOLO Test" > README.md
git add . && git commit -m "Initial commit"
```

2. 以YOLO模式启动Claude Code：
```bash
claude --dangerously-skip-permissions
```

3. 给Claude一个多步骤任务：
```
创建一个简单的Python计算器模块，包含加减乘除函数。
然后创建一个测试文件并运行测试。
```

4. 观察Claude如何无提示地执行

5. 审查更改：
```bash
git diff
git status
```

6. 清理：
```bash
cd ~ && rm -rf ~/yolo-test
```

### 将YOLO与Ralph Wiggum结合

YOLO模式通常与Ralph Wiggum（TP2）一起使用，实现完全自主的编码会话：

```bash
# 以YOLO模式启动Claude Code
claude --dangerously-skip-permissions

# 然后使用Ralph Wiggum进行自主循环
/ralph-wiggum:ralph-loop "实现功能X并编写测试" --completion-promise "DONE" --max-iterations 10
```

这种组合允许Claude完全自主工作，迭代直到任务完成。

## 最佳实践总结

### 权限配置

| 场景 | 建议 |
|-----|------|
| 日常开发 | Allowlist常见安全命令 |
| 团队项目 | 使用 `.claude/settings.json` 中的项目级设置 |
| 个人工具 | 使用用户级设置保持一致性 |
| 敏感工作 | 保持默认（询问所有） |
| 学习/教程 | 在隔离环境中使用YOLO模式 |

### 决策流程图

```
这是生产环境吗？
  → 是：永不使用YOLO模式，使用保守的allowlist

这是沙箱/一次性环境吗？
  → 是：YOLO模式可接受

我完全理解Claude将做什么吗？
  → 否：不使用YOLO模式
  → 是：考虑使用YOLO提高效率

我在使用版本控制吗？
  → 否：不使用YOLO模式
  → 是：YOLO更安全（可以恢复）
```

## 预期成果

完成本TP后，你应该：

- ✅ 理解Claude Code的权限系统
- ✅ 为常见操作配置了allowlist
- ✅ 安全地体验了YOLO模式
- ✅ 能够做出明智的安全决策

## 故障排除

### 问题：已允许的命令仍然被询问权限

**解决方案**：
- 检查精确的命令语法是否与你的allowlist模式匹配
- 验证设置已保存（使用 `/config` 检查）
- 记住模式是区分大小写的

### 问题：YOLO模式似乎停止了

**解决方案**：
- YOLO模式默认仅限会话
- 使用 `--dangerously-skip-permissions` 选项重启
- 检查是否遇到硬限制（如网络错误）

### 问题：想要在会话中禁用YOLO模式

**解决方案**：只需不带选项重启Claude Code，或按Ctrl+C退出。

## 其他资源

- [Claude Code文档 - 权限](https://docs.anthropic.com/claude-code/permissions)
- [Claude Code安全最佳实践](https://docs.anthropic.com/claude-code/security)
- [TP2: Ralph Wiggum - 自主循环](./TP2-Ralph-Wiggum-Autonomous-Loops_cn.md)

## 提交

完成本TP需要提交：

1. **截图**：
   - 显示你的allowlist配置的 `/config` 输出

2. **配置文件**：
   - 如果创建了项目级设置，提供你的 `.claude/settings.json`

3. **反思**（3-5句话）：
   你对权限配置的理念是什么？你更喜欢询问所有、创建常用命令的allowlist，还是使用YOLO模式？为什么？什么场景会改变你的方法？

---

**恭喜！** 你现在了解了在使用Claude Code时如何平衡安全性和便利性。记住：能力越大，责任越大。明智地使用YOLO模式！
