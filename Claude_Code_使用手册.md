# Claude Code 使用手册

> Claude Code 是 Anthropic 官方推出的 AI 编程助手 CLI 工具，支持终端、桌面应用、网页版和 IDE 扩展。

---

## 目录

1. [安装与环境](#1-安装与环境)
2. [基本用法](#2-基本用法)
3. [常用命令](#3-常用命令)
4. [文件操作工具](#4-文件操作工具)
5. [Git 与 GitHub 操作](#5-git-与-github-操作)
6. [任务管理](#6-任务管理)
7. [多代理协作](#7-多代理协作)
8. [ Skills 技能系统](#8-skills-技能系统)
9. [MCP 工具集成](#9-mcp-工具集成)
10. [浏览器自动化](#10-浏览器自动化)
11. [实用技巧](#11-实用技巧)
12. [常见问题](#12-常见问题)

---

## 1. 安装与环境

### 安装方式

```bash
# macOS/Linux
curl -fsSL https://claude.ai/install.sh | sh

# 或通过 npm
npm install -g @anthropic-ai/claude-code
```

### 启动

```bash
# 在项目目录中启动
cd your-project
claude
```

### 环境信息查看

```bash
# 查看当前版本和配置
claude --version
```

---

## 2. 基本用法

### 启动 Claude Code

```bash
claude                    # 正常启动
claude --fast            # 快速模式（更快响应）
claude --model opus      # 指定模型
```

### 会话中基本操作

| 操作 | 说明 |
|------|------|
| 直接输入文本 | 与 Claude 对话，描述你的需求 |
| `! <命令>` | 在会话中执行 shell 命令 |
| `Ctrl+C` | 中断当前操作 |
| `Ctrl+D` | 退出 Claude Code |
| `/help` | 获取帮助 |
| `/clear` | 清除会话 |

### 模式说明

- **默认模式**: 每次操作需用户确认
- **自动模式**: 自动执行安全操作
- **计划模式**: 先规划再执行，适合复杂任务

---

## 3. 常用命令

### Slash 命令

| 命令 | 功能 |
|------|------|
| `/help` | 显示帮助信息 |
| `/clear` | 清除当前会话 |
| `/compact` | 压缩对话历史以节省上下文 |
| `/config` | 配置设置 |
| `/cost` | 查看使用成本 |
| `/doctor` | 诊断常见问题 |
| `/init` | 初始化项目配置 |
| `/login` | 登录账户 |
| `/logout` | 登出账户 |
| `/memory` | 管理持久化记忆 |
| `/permissions` | 管理权限设置 |
| `/review` | 代码审查 |
| `/status` | 查看当前状态 |
| `/terminal-setup` | 设置终端集成 |

### 快速模式

```bash
/fast        # 切换快速模式
# 或启动时使用
claude --fast
```

---

## 4. 文件操作工具

### 读取文件

```
# 让 Claude 读取文件
"读取 src/main.py 文件"
"查看 package.json 的内容"
```

### 编辑文件

```
# 描述你要做的修改
"在 config.js 中添加一个新的环境变量"
"修复 login.js 中的第 42 行错误"
"重构 utils.go 中的 parse 函数"
```

### 创建文件

```
"创建一个 README.md 文件"
"新建 src/components/Button.tsx"
```

### 搜索与查找

```
"搜索所有包含 'useState' 的文件"
"查找项目中的所有 .test.js 文件"
"在 src 目录下查找 TODO 注释"
```

---

## 5. Git 与 GitHub 操作

### Git 操作

```
"查看 git 状态"
"提交当前更改，消息是 'feat: add login'"
"创建新分支 feature/auth"
"查看最近的提交历史"
```

### GitHub 操作

```
"创建一个 PR"
"查看 issue #123"
"列出所有 open 的 PR"
```

### 常用 Git 命令对应

| 需求 | 描述方式 |
|------|----------|
| 查看状态 | "查看 git status" |
| 提交 | "提交这些更改，消息是 xxx" |
| 创建分支 | "创建新分支 xxx" |
| 推送 | "推送到远程" |
| 创建 PR | "创建一个 PR，标题是 xxx" |

---

## 6. 任务管理

### 创建任务

```
"创建一个任务：实现用户登录功能"
"添加任务：修复首页加载慢的问题"
```

### 查看任务

```
"查看当前任务列表"
"我有什么待办事项"
```

### 任务状态

```
"把任务 1 标记为完成"
"开始处理任务 2"
```

---

## 7. 多代理协作

### 创建团队

```
"创建一个团队帮我完成这个功能"
"启动多个代理并行处理"
```

### 分配任务

```
"把这个任务分配给 researcher 代理"
"让 tester 代理运行测试"
```

---

## 8. Skills 技能系统

Skills 是可复用的技能模块，通过 `/skill-name` 调用。

### 内置技能

| 技能 | 功能 |
|------|------|
| `/commit` | 智能提交代码 |
| `/review-pr` | 审查 PR |
| `/loop` | 定时执行任务 |
| `/simplify` | 简化和优化代码 |

### 可用技能示例

| 技能 | 功能 | 触发场景 |
|------|------|----------|
| `yuque` | 语雀文档操作 | 管理语雀知识库 |
| `agent-browser` | 浏览器自动化 | 网页交互、表单填写 |
| `claude-api` | Claude API 开发 | 构建AI应用 |
| `mcp-register` | MCP工具注册 | 注册SOFA接口为MCP |
| `qt-spec-loader` | 技能加载器 | 初始化项目技能 |

### 使用技能

```
/commit                    # 提交代码
/yuque                     # 操作语雀文档
/agent-browser             # 浏览器自动化
```

---

## 9. MCP 工具集成

MCP (Model Context Protocol) 允许 Claude Code 与外部工具集成。

### 已集成工具示例

| 工具 | 功能 |
|------|------|
| `chrome-devtools` | Chrome 开发者工具 |
| `钉钉文档` | 钉钉文档/知识库操作 |
| `语雀` | 语雀文档管理 |

### 使用 MCP 工具

```
"在钉钉文档中搜索 xxx"
"获取语雀文档内容"
"用浏览器打开 xxx 网站并截图"
```

---

## 10. 浏览器自动化

通过 `agent-browser` 技能实现浏览器自动化。

### 常用操作

```
"打开 https://example.com 并截图"
"在网页上填写表单"
"点击登录按钮"
"提取网页中的数据"
```

### 浏览器工具

| 功能 | 说明 |
|------|------|
| `navigate_page` | 导航到URL |
| `click` | 点击元素 |
| `fill` | 填写表单 |
| `take_screenshot` | 截图 |
| `take_snapshot` | 获取页面快照 |
| `hover` | 悬停元素 |
| `press_key` | 按键操作 |

---

## 11. 实用技巧

### 推荐的工作流程

1. **开始新任务时**
   ```
   "帮我理解这个项目的结构"
   "这个文件的作用是什么？"
   ```

2. **编写代码时**
   ```
   "先帮我制定一个实现计划"
   "检查这段代码有没有安全问题"
   ```

3. **调试时**
   ```
   "帮我分析这个错误"
   "这个测试为什么失败？"
   ```

4. **提交代码时**
   ```
   /commit
   "创建一个 PR"
   ```

### 提高效率的技巧

| 技巧 | 说明 |
|------|------|
| 使用 `/fast` | 需要快速响应时开启 |
| 使用 `!` 前缀 | 快速执行 shell 命令 |
| 明确描述需求 | 越具体效果越好 |
| 利用记忆功能 | 让 Claude 记住重要信息 |
| 使用任务列表 | 复杂任务分解管理 |

### 上下文管理

```bash
/compact          # 压缩对话历史
/clear            # 清空会话重新开始
/memory           # 管理持久记忆
```

---

## 12. 常见问题

### Q: 如何切换模型？

```bash
claude --model opus    # 使用 Opus
claude --model sonnet  # 使用 Sonnet
claude --model haiku   # 使用 Haiku
```

### Q: 如何处理权限问题？

```bash
/permissions           # 查看和配置权限
```

### Q: 会话上下文满了怎么办？

```bash
/compact               # 压缩历史
/clear                 # 清空重来
```

### Q: 如何让 Claude 记住项目信息？

创建 `CLAUDE.md` 文件在项目根目录：
```markdown
# 项目说明
这是一个 React 项目...

## 编码规范
- 使用 TypeScript
- 组件使用函数式写法
```

### Q: 如何查看使用成本？

```bash
/cost
```

### Q: SSH 认证显示 "no shell access" 是正常的吗？

是的！GitHub 用 SSH 只做身份验证，不提供终端登录。
看到 `Hi xxx! You've successfully authenticated` 就是成功。

---

## 快速参考卡

### 最常用

| 操作 | 命令/描述 |
|------|----------|
| 启动 | `claude` |
| 快速模式 | `claude --fast` |
| 提交代码 | `/commit` |
| 执行命令 | `! <命令>` |
| 清除会话 | `/clear` |
| 查看状态 | `/status` |

### 文件操作

| 操作 | 描述示例 |
|------|----------|
| 读文件 | "读取 xxx 文件" |
| 编辑 | "修改 xxx，添加..." |
| 创建 | "创建 xxx 文件" |
| 搜索 | "搜索包含 xxx 的文件" |

### Git 操作

| 操作 | 描述示例 |
|------|----------|
| 状态 | "查看 git 状态" |
| 提交 | "提交更改，消息是 xxx" |
| 分支 | "创建新分支 xxx" |
| PR | "创建一个 PR" |

---

## 相关链接

- 官方网站: https://claude.ai/code
- GitHub Issues: https://github.com/anthropics/claude-code/issues
- 文档: https://docs.anthropic.com/claude-code

---

*本手册最后更新: 2026-04-02*