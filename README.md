# 2026版 Token173 API 中转站_Claude 转发API_Claude api key购买_低价稳定Claude API_国内直连Claude_Token173聚合中转API

<img width="1024" height="1536" alt="1c462f17-b75a-4282-8009-5b56da56a6f3(1)" src="https://github.com/user-attachments/assets/4c6d778b-413a-4d7c-a26a-ef32f65f262c" />


Token173聚合中转API是一个高效的Claude API、Open AI、Midjourney API代理、Claude代理、Suno代理等供应商
我们致力于提供优质的 API 接入服务，让您可以轻松集成先进的AI模型至您的产品和服务。通过 API 综合管理平台，无缝整合OpenAl最尖端的人工智能模型。借助我们可靠且易于使用的API解决方案，升级您的产品与服务。


聚合中国和全球300+多模态大模型，文生文、文生图、文生视频、文生音频。Token173中转API汇聚了国内外300+多模态大型人工智能模型，全面支持文生文、文生图、文生视频、文生音频等多种模态API。这些模型基于深度学习技术，具备强大的自然语言处理、图像识别、视频分析和音频合成能力，让您的AI应用如虎添翼。核心优势包括海量模型资源、多样化生成能力、智能优化算法和简单易用等。应用场景广泛，包括营销推广、内容创作、教育培训和娱乐互动等。

支持几乎所有Anthropic AI大模型

*   Model List:
*   claude-4.8
*   claude-4.7
*   claude-4.6
*   claude-4.5
*   claude-4.0
*   claude-4.1 claude-opus-4-1-20250805
*   claude-4 claude-sonnet-4-20250514
*   claude-4 claude-opus-4-20250514
*   claude-3.7 claude-3-7-sonnet
*   claude-3.5 claude-3-5-sonnet
*   claude-3 claude-3-opus-20240229
*   claude-3 claude-3-haiku-20240307
*   claude-3 claude-3-haiku
*   ...


![Claude API 中转站]()


## 为什么选择【Token173聚合中转API】（token173.net）？

在众多中转服务中，Token173聚合中转API（token173.net）凭借稳定性、易用性与性价比脱颖而出：

• 多模型支持：支持国内外主流大模型，满足不同场景的需求。

• 高可用性：全球加速+负载均衡，保证请求稳定性与低延迟。

• 统一调用规范：开发者只需学习一次，即可调用所有支持的AI接口。

• 灵活计费：按量计费、套餐灵活，避免资金分散在多个平台。

 • 开发者友好：提供完善的文档、调用示例与调试工具，接入成本低。

 ## 官方链接
    •	官网：https://token173.net
	•	教程文档 & 示例代码：https://docs.token173.net
	•	参考资料：https://docs.token173.net/docs/introduction


# Token173中转API实现任意模型Claude Compatible接入！
---

随着 Claude Code 在开发者中的普及，越来越多的用户希望能在只支持 Claude 接口的应用中调用更多模型。Token173中转API 率先实现了"任意模型 Claude Compatible"，极大推动了 AI 生态的开放和互联！

* * *

## 🧠 Claude 格式 vs OpenAI 格式对比
---

### 🎯 请求路径区别

| 接口类型 | 示例请求路径 |
| --- | --- |
| OpenAI 格式 | `token173.net/v1/chat/completions` |
| Claude 格式 | `token173.net/v1/messages` |

### 🧾 请求体格式差异

**OpenAI 格式请求示例**：

```json
{
    "model": "gpt-4.1",
    "messages": [
        {
            "role": "user",
            "content": "Hello!"
        }
    ]
}

```

**Claude 格式请求示例**：

```json
{
    "model": "claude-3-5-sonnet-20240620",
    "max_tokens": 1024,
    "messages": [
        {
            "role": "user",
            "content": "Hello, world"
        }
    ]
}
```

**关键差异**：

*   **参数结构**：Claude 请求中必须显式指定 `max_tokens`；OpenAI 中为可选。

*   **字段命名**：如 `messages` 等字段虽然类似，但默认行为及语义略有差异。

* * *

## 📦 响应格式差异对比
---

### OpenAI 返回示例

```json
{
    "choices": [
        {
            "finish_reason": "stop",
            "index": 0,
            "logprobs": null,
            "message": {
                "annotations": [],
                "content": "Hello! How can I assist you today? 😊",
                "refusal": null,
                "role": "assistant"
            }
        }
    ],
    "created": 1753384149,
    "id": "chatcmpl-BwvbRo5aJ8TXqFwmmOXsE7eicJig3",
    "model": "gpt-4.1",
    "object": "chat.completion",
    "system_fingerprint": "fp_07e970ab25"
}
```

### Claude 返回示例

```json
{
    "id": "msg_01NufbyqybJo5fVtRkH1VPzk",
    "type": "message",
    "role": "assistant",
    "model": "claude-3-5-sonnet-20240620",
    "content": [
        {
            "type": "text",
            "text": "Hello! How can I assist you today? Is there anything specific you'd like to talk about or any questions you have?"
        }
    ],
    "stop_reason": "end_turn"
}
```

**主要结构差异**：

| 项目 | OpenAI | Claude |
| --- | --- | --- |
| 回复结构 | 使用 `choices` 数组 | 顶层 `content` 数组 |
| 内容位置 | `choices[0].message.content` | `content[0].text` |
| 元信息 | 包括 `created`, `id`, `model` 等 | 命名结构不同但信息类似 |
| 停止标识 | `finish_reason` | `stop_reason` |

* * *

## 🚧 接口不兼容性的挑战
---

虽然两者都使用 JSON 结构，但在：

*   **流式响应**

*   **函数调用**

*   **系统提示词的结构**

*   **返回格式嵌套层级**

等方面存在较大差异，导致 OpenAI 与 Claude 的 API 完全不兼容。

* * *

## 🚀 Token173中转API：让任意模型秒变 Claude Compatible！
---

为解决这一痛点，Token173中转API 推出了革命性的 API 中转兼容方案：

*   ✅ **兼容 Claude Code 接口标准**

*   ✅ **支持平台自营全部模型**

*   ✅ **支持接入自定义第三方模型**

*   ✅ **统一封装为 Claude 格式，自动协议转换**

### 🌐 一站式模型整合平台

开发者可将任何模型（无论底层是否兼容 Claude 格式）通过Token173中转API 的"自定义 API 功能"接入平台。Token173中转API将自动完成协议适配，统一转化为 Claude Compatible 接口，无需手动修改代码。

* * *



# 「2026最新推荐」Claude Code国内使用_保姆级新手安装使用教程_Token173中转API Claude Code代理API_最强AI编程工具

## 什么是 Claude Code

Claude Code 是 Anthropic 推出的一个 agentic 编码工具 (agentic coding tool)，可以在命令行（terminal）中运行，或者集成在一些支持终端的 IDE 中，借助 Claude 的语言模型能力来辅助写代码、重构、调试、维护、理解代码库等。

![Claude Code国内使用]()

### **Claude Code特点**

	•	能理解整个代码库的上下文，不只是单个文件；

	•	支持自然语言命令 —— 用 "说"的方式让它做事情，比如 "帮我重构这个函数"、"让这个模块更高效"、"在这个地方加测试" 等；

	•	可以执行命令／运行 shell 或 bash 命令并把输出作为上下文之一；

	•	支持项目记忆（persistent project context），比如通过 CLAUDE.md 文件提供项目的风格、结构、常用脚本等，这样 Claude 在后续操作里就能"记得"这些规则。


### **🚀 主要功能**

*   **智能代码生成** - 快速生成高质量代码

*   **代码分析** - 深度理解和分析代码结构

*   **调试助手** - 智能发现和修复代码问题

*   **文档生成** - 自动生成代码文档

*   **命令行集成** - 无缝集成到开发流程

## ⭐**Token173中转API专属功能**

Token173中转API（token173.net）所有LLM 模型均支持在 Claude code 中使用

如果 Claude code 无法修改调用模型，可参考教程令牌中，设置模型转发


![Claude Code国内使用]()

## **📦 安装步骤**

### Mac & Liunx 配置方式

#### **1. 安装 Node.js**

确保系统已安装 Node.js 18+ 版本

##### **安装 Homebrew (mac推荐)**

如果尚未安装 Homebrew：
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
#### **2. 安装 Node.js**

使用 Homebrew：
```
brew install node
```
#### **2. 安装 Claude Code**
```
npm install -g @anthropic-ai/claude-code
```
#### **3. 配置 API 密钥**

##### **获取 Auth Token (参考添加令牌文档**

###### **方法一：使用 Bash（推荐）**
```
echo 'export ANTHROPIC_AUTH_TOKEN="sk-xxx"' >> ~/.bash_profile echo 'export ANTHROPIC_BASE_URL="https://token173.net"' >> ~/.bash_profile source ~/.bash_profile
```
###### **方法二：使用 Zsh（如果使用 Oh My Zsh）**
```
echo 'export ANTHROPIC_AUTH_TOKEN="sk-xxx"' >> ~/.zshrc echo 'export ANTHROPIC_BASE_URL="https://token173.net"' >> ~/.zshrc source ~/.zshrc
```
**注意：** 永久设置后需要重启终端才能生效。

#### **4. 启动使用 Claude Code**
```
# 进入项目目录
cd your-project-folder

# 启动 Claude Code
claude
```
**首次启动后需要先进行主题的选择等操作：**

*   • 选择喜欢的主题（回车）

*   • 确认安全须知（回车）

*   • 使用默认 Terminal 配置（回车）

*   • 信任工作目录（回车）

*   • 开始编程！🚀

### Windows配置方式

1、**管理员权限**启动cmd

#### **1. 安装 Node.js**

访问  Node.JS 官网，点击最新版本，选择对应的操作系统和版本下载即可

下载后双击安装，之后一直点击下一步。安装完成后，打开 CMD 窗口，执行命令验证安装：
```
node -v
```
2、设置 npm 配置,告诉 npm 在安装包时忽略执行包中的脚本（如 preinstall、postinstall 等）,设置完重新启动CMD
```
setx NPM_CONFIG_IGNORE_SCRIPTS true
```
3、安装 Claude Code
```
npm install -g @anthropic-ai/claude-code
```
4、配置 SHELL 环境变量

###### **方法一：图形化配置（推荐，永久生效）**

a. 右键点击 "此电脑" → 选择 "属性"

b. 点击 "高级系统设置"

c. 在 "系统属性" 窗口中点击 "环境变量"

重要：在 "系统变量" 部分点击 "新建"（多人共享电脑可选择 "用户变量"）

d. 添加以下两个变量：

变量名：ANTHROPIC_AUTH_TOKEN，变量值：sk-xxx

变量名：ANTHROPIC_BASE_URL，变量值：https://token173.net

e. 点击 "确定" 保存

###### **方法二：PowerShell（永久设置）**


```PowerShell
[Environment]::SetEnvironmentVariable("ANTHROPIC_AUTH_TOKEN", "sk-xxx", "User")
[Environment]::SetEnvironmentVariable("ANTHROPIC_BASE_URL", "https://token173.net", "User")
```
###### **方法三：命令提示符（永久设置）**

CMD
```
setx ANTHROPIC_AUTH_TOKEN "sk-xxx"
setx ANTHROPIC_BASE_URL "https://token173.net"
```
**注意：** 永久设置后需要重启终端才能生效。推荐使用永久配置方式。

###### **方法四：通过**settings.json 设置

找到 settings.json 文件，如果没有请创建
```
C:\Users\{user}\.claude\settings.json
```
设置 API 信息，保存
```
{
    "env": {
      "ANTHROPIC_MODEL": "claude-sonnet-4-20250514",
      "ANTHROPIC_SMALL_FAST_MODEL": "claude-sonnet-4-20250514",
      "ANTHROPIC_BASE_URL": "https://token173.net",
      "ANTHROPIC_AUTH_TOKEN": "sk-AG2"
    }
  }
```
```
setx SHELL "C:\Program Files\Git\bin\bash.exe" #这里要换成你的路径， 
# 如果不知道，可以执行 where git 找一下 
```



5、添加 npm 环境变量

```
C:\Users\y.xie\.npm-global # 添加Windows环境变量，同样要设置为你的路径，在npm安装包里面
# 如果不知道，可以执行 npm config get prefix 找一下

```

将其添加到 Windows 的环境变量（PATH），关闭并重新打开你的终端窗口（CMD / PowerShell / Git Bash），使设置生效。

6、设置API配置

7、重启开发环境

8、enjoy!!

```
# 进入项目目录
cd your-project-folder

# 启动 Claude Code
claude
```

### **🎯 常用命令**

*   `claude` - 启动交互模式

*   `claude "task"` - 运行一次性任务

*   `claude commit` - 创建 Git 提交

*   `/help` - 显示可用命令

*   `/clear` - 清除对话历史

*   `/review` - 请求代码审查

### **💡 使用示例**

```
# 代码生成
> 请帮我写一个 Python 函数，用于计算斐波那契数列

# 代码审查
claude "review this code for potential bugs"

# 自动提交
claude commit

```

### **切换模型**

使用 Claude Code 命令：
```
/model [model id]
```
默认模型为`Sonnet 4`，你可以用效果更好的`Opus 4`：

**opus**
```
/model opus
```
或者，换成其他 claude 模型：

**sonnet 3.7**

**sonnet 3.5**
```
/model claude-3-7-sonnet-20250219
```
**Kimi K2 支持**启动 Claude Code 之后，只需要运行指令
```
/model moonshotai/kimi-k2-instruct
```
其他 LLM 模型均支持使用，比如 Openai、Gemini、Qwen、Doubao

### **⚠️ 重要提示**

1.   **API 密钥配置**：请将 `sk-your-api-key` 替换为您在本站 生成的实际 API 密钥

2.   **令牌分组**：在本站 创建令牌时，建议选择 "企业分组 官转分组"

3.   **网络连接**：确保网络连接稳定，工具需要与 API 服务器通信

4.   **项目目录**：建议在具体项目目录下使用，以获得更好的上下文理解

### **🔧 高级功能**

*   **IDE 集成** - 支持 Cursor 等 IDE 集成

*   **MCP 服务器** - 扩展 Agent 能力

*   **CI/CD 集成** - 自动化代码审查流程

*   **团队规范** - 通过CLAUDE.md文件定义团队规范

## Claude Code 能做什么：功能列表

下面是 Claude Code 在实际开发中能帮你做的事情，列出来比较全，也分几类：

| 类别 | 功能 |
|---|---|
|代码生成 | 新建模块/组件/API/数据库模型 |
|重构优化 | 改变量名、优化性能、清理废代码 |
|调试修复 | 定位 bug、写单元测试、解决依赖冲突 |
|文档注释 | 自动生成 docstring / README / 使用指南 |
|跨语言转换 | Python ↔ JS / Go / Java 等 |
|代码审查 | 检查安全性、性能、风格一致性 |
|脚本任务 | 执行测试、构建、生成脚手架、CI/CD 配置 |
|理解项目 | 帮助快速熟悉陌生/遗留代码库 |


---

# Claude Code 实用教程：高效开发技巧与最佳实践

## 一、快速项目初始化与脚手架生成

### 1.1 创建全栈应用脚手架

#### 使用场景
需要快速搭建一个包含前后端的完整项目结构，包括配置文件、Docker支持、测试框架等。

#### 操作步骤

```bash
# 在终端中打开目标目录，然后启动 Claude
claude
```

#### Prompt 示例

```
请帮我创建一个全栈应用的项目结构，要求：
1. 后端：Node.js + Express + TypeScript + Prisma ORM
2. 前端：React + TypeScript + Vite + TailwindCSS
3. 包含 Docker Compose 配置（前端、后端、PostgreSQL、Redis）
4. 包含 ESLint、Prettier 配置
5. 包含 GitHub Actions CI/CD 配置
6. 包含完整的 README.md

项目名称：task-manager
请生成完整的目录结构和所有必要的配置文件。
```

#### 预期输出结构

```
task-manager/
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── middlewares/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── utils/
│   │   └── index.ts
│   ├── prisma/
│   │   └── schema.prisma
│   ├── tests/
│   ├── .env.example
│   ├── Dockerfile
│   ├── package.json
│   └── tsconfig.json
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── utils/
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── Dockerfile
│   ├── package.json
│   ├── vite.config.ts
│   └── tsconfig.json
├── docker-compose.yml
├── .github/
│   └── workflows/
│       └── ci.yml
├── .gitignore
└── README.md
```

### 1.2 生成 API 端点与文档

#### Prompt 示例

```
基于以下数据模型，生成完整的 RESTful API：

模型：
- User (id, email, name, role, createdAt, updatedAt)
- Task (id, title, description, status, priority, assigneeId, createdAt, updatedAt)
- Comment (id, taskId, userId, content, createdAt)

要求：
1. 为每个模型生成完整的 CRUD 端点
2. 包含身份验证中间件（JWT）
3. 包含输入验证（使用 Joi 或 Zod）
4. 包含分页、排序、过滤功能
5. 生成 OpenAPI/Swagger 文档
6. 包含示例请求和响应

输出格式：完整的 routes 文件和 controller 文件
```

---

## 二、智能代码重构与优化

### 2.1 性能优化分析

#### 使用场景
发现代码性能问题，需要 Claude 分析并提供优化方案。

#### Prompt 示例

```
分析以下 React 组件的性能问题并提供优化方案：

[粘贴你的代码]

请从以下角度分析：
1. 不必要的重渲染
2. 内存泄漏风险
3. 大列表渲染优化
4. 异步操作优化
5. Bundle size 优化

输出：
- 问题清单（按严重程度排序）
- 每个问题的具体优化方案
- 优化后的完整代码
- 性能提升预期
```

### 2.2 代码现代化升级

#### Prompt 示例

```
将以下 JavaScript 代码升级为现代 TypeScript，要求：
1. 添加完整的类型定义
2. 使用 ES6+ 特性（async/await、解构、模板字符串等）
3. 改进错误处理
4. 添加 JSDoc 注释
5. 遵循 TypeScript 最佳实践

[粘贴旧代码]

额外要求：
- 保持向后兼容
- 列出所有破坏性变更
- 提供迁移指南
```

---

## 三、测试代码生成与覆盖率提升

### 3.1 生成完整测试套件

#### Prompt 示例

```
为以下模块生成完整的测试套件：

[粘贴你的代码模块]

测试要求：
1. 单元测试（Jest/Vitest）
2. 集成测试
3. 边界条件测试
4. 错误场景测试
5. Mock 外部依赖
6. 测试覆盖率目标：>90%

输出：
- 完整的测试文件
- 测试用例说明表格
- Mock 数据生成函数
- 测试运行配置
```

### 3.2 E2E 测试脚本生成

#### Prompt 示例

```
基于以下用户流程生成 Playwright E2E 测试：

用户流程：
1. 用户访问登录页
2. 输入邮箱和密码
3. 点击登录
4. 跳转到仪表板
5. 创建新任务
6. 编辑任务状态
7. 删除任务
8. 登出

要求：
- 使用 Page Object Model
- 包含断言验证
- 处理异步操作
- 添加截图功能
- 支持多浏览器测试
```

---

## 四、数据库操作与迁移

### 4.1 数据库 Schema 设计与优化

#### Prompt 示例

```
设计一个电商系统的数据库 schema，要求：

业务需求：
- 用户管理（多角色）
- 商品管理（多分类、多规格）
- 订单系统（状态流转）
- 库存管理（实时更新）
- 支付记录
- 评价系统

技术要求：
1. 使用 PostgreSQL
2. 考虑索引优化
3. 考虑数据分区
4. 包含触发器和存储过程
5. 生成 Prisma schema
6. 生成 SQL 迁移脚本
7. 包含种子数据脚本

输出格式：
- ER 图描述
- SQL DDL 语句
- Prisma schema
- 索引优化建议
```

### 4.2 数据迁移脚本生成

#### Prompt 示例

```
生成数据迁移脚本，将 MongoDB 数据迁移到 PostgreSQL：

MongoDB 集合结构：
{
  users: { _id, email, profile: { name, avatar }, posts: [postIds] },
  posts: { _id, userId, title, content, tags: [], comments: [{}] }
}

目标 PostgreSQL 结构：
- users 表
- profiles 表（1对1）
- posts 表
- tags 表
- post_tags 关联表
- comments 表

要求：
1. 处理数据类型转换
2. 处理关联关系
3. 包含回滚脚本
4. 批量处理大数据量
5. 错误处理和日志
6. 进度显示
```

---

## 五、API 集成与调试

### 5.1 生成 API 客户端

#### Prompt 示例

```
基于以下 OpenAPI 规范生成 TypeScript API 客户端：

[粘贴 OpenAPI JSON/YAML]

要求：
1. 完整的类型定义
2. 支持请求拦截器
3. 自动重试机制
4. 错误处理封装
5. 支持取消请求
6. 缓存机制
7. 生成使用示例

技术栈：Axios + TypeScript
```

### 5.2 Mock Server 生成

#### Prompt 示例

```
基于以下 API 规范创建 Mock Server：

API 列表：
- GET /api/users（分页）
- GET /api/users/:id
- POST /api/users
- PUT /api/users/:id
- DELETE /api/users/:id
- GET /api/users/:id/posts

要求：
1. 使用 Express + Faker.js
2. 支持动态数据生成
3. 模拟延迟和错误
4. 支持 WebSocket
5. 数据持久化（JSON 文件）
6. 支持场景切换
7. 包含 Docker 配置
```

---

## 六、调试与问题定位

### 6.1 错误分析与修复

#### Prompt 示例

```
分析以下错误并提供解决方案：

错误信息：
[粘贴完整的错误堆栈]

相关代码：
[粘贴相关代码片段]

环境信息：
- Node.js version: 18.x
- Framework: Next.js 14
- Database: PostgreSQL 15

要求：
1. 解释错误原因
2. 提供多种解决方案
3. 推荐最佳方案
4. 提供修复后的代码
5. 如何避免类似问题
```

### 6.2 性能问题诊断

#### Prompt 示例

```
诊断以下性能问题：

症状：
- API 响应时间从 100ms 增加到 2s
- 数据库查询缓慢
- 内存使用持续增长

提供的信息：
[慢查询日志]
[相关代码]
[性能监控数据]

请提供：
1. 问题根因分析
2. 优化方案（短期/长期）
3. 具体代码修改
4. 性能监控建议
5. 预防措施
```

---

## 七、文档生成与维护

### 7.1 生成项目文档

#### Prompt 示例

```
为项目生成完整文档：

项目结构：
[粘贴项目树形结构]

要求生成：
1. README.md（项目介绍、快速开始、架构说明）
2. API 文档（端点说明、请求示例、响应格式）
3. 部署文档（环境要求、部署步骤、配置说明）
4. 开发指南（代码规范、提交规范、分支策略）
5. 故障排查指南

格式要求：
- Markdown 格式
- 包含目录
- 包含示例代码
- 包含架构图（Mermaid）
```

### 7.2 代码注释生成

#### Prompt 示例

```
为以下代码添加详细注释：

[粘贴代码]

注释要求：
1. JSDoc/TSDoc 格式
2. 函数说明（目的、参数、返回值、异常）
3. 复杂逻辑说明
4. 算法时间/空间复杂度
5. 使用示例
6. 注意事项
7. TODO 和 FIXME 标记
```

---

## 八、CI/CD 配置生成

### 8.1 GitHub Actions 工作流

#### Prompt 示例

```
生成 GitHub Actions CI/CD 配置：

项目信息：
- 前端：React + TypeScript
- 后端：Node.js + TypeScript
- 数据库：PostgreSQL
- 部署目标：AWS ECS

要求：
1. PR 检查（lint、test、build）
2. 主分支自动部署到 staging
3. Tag 触发生产部署
4. 包含密钥管理
5. 并行执行优化
6. 缓存优化
7. 通知机制（Slack）

生成：
- .github/workflows/ci.yml
- .github/workflows/deploy.yml
- 部署脚本
```

---

## 九、代码审查与安全扫描

### 9.1 安全漏洞扫描

#### Prompt 示例

```
对以下代码进行安全审查：

[粘贴代码]

检查项：
1. SQL 注入
2. XSS 攻击
3. CSRF 攻击
4. 敏感信息泄露
5. 不安全的依赖
6. 权限验证漏洞
7. 加密问题
8. 输入验证

输出：
- 漏洞列表（按严重等级）
- 修复方案
- 修复后的代码
- 安全最佳实践建议
```





# 这里是使用教程  

### 新用户注册赠送 0.2 刀额度，前往令牌页复制令牌，在聊天页设置中填入即可体验！



### 目录

```
· 分组区别
· 网站使用教程
  · GPT接入教程
  · Midjourney 接入教程
· 常见项目配置方式
· 常见问题
```

<br/>


## 分组区别




## 网站使用教程

🔥 均为高速回复渠道非低价普通渠道

💰 为方便计费，一个账号通用所有模型，兑换比例固定为 2 元兑换 1美金
其中GPT-4全模型（含32K、Dalle3）后台为官方计费倍率 2 倍，相当于4元兑换1美金（约等于官方的2.4折） 

后台日志计费规则解析：假如提示是2000，补全是1000，使用的gpt-4，则您后台的扣费公式=(2000/1000)x0.03（提问价格）+(1000/1000)x0.06（回答价格）=$0.12   


### GPT接入教程

1. 注册账号，免费体验，注册即送0.2美金额度，1刀起充
2. 前往[令牌页](/token)，添加令牌
3. 修改应用 BASE_URL为中转接口调用地址： https://token173.net  设置 API Key 为添加的令牌

不同的客户端需要填写不同的BASE_URL, 请尝试如下地址  
https://token173.net  
https://token173.net/v1  
https://token173.net/v1/chat/completions  

模型名在[首页](/) -> 支持模型中的第一列 模型 中   
可在[聊天页](/chat) 进行测试或使用

<br/>

### Midjourney 接入教程

Midiourney-Proxy主机：https://token173.net

Midiourney-Proxy Secret ：自己后台生成的令牌

同时支持 Mid journey proxy Plus 以及 Mid journey proxy 接口协议



以下参数均可在令牌设置中进行设置  
切换 MJ mode: 

1. 通过 URL 路径切换   
默认 /mj 是 fast mode   
/mj-fast/mj 是 fast mode   
/mj-turbo/mj 是 turbo mode   
/mj-relax/mj 是 relax mode   
例如： https://token173.net/
2. prompt 中通过 mj 参数指定： --relax\--fast\--turbo

切换 MJ 返回的图片地址：
1. 通过 URL 路径切换   
默认 /mj 是管理员设置默认方式    
/mj-{mode}-relay/mj 是使用服务转发地址，图片国内访问较快   
/mj-{mode}-origin/mj 是使用discord 原地址，图片国外访问很快   
/mj-{mode}-proxy/mj 是使用管理员设置的代理地址，图片国内访问较快  
例如： https://token173.net/



<br/>

类型1端点：

1. 类型 1 端点包括：Imagine/Variation/Outpaint/Pan/Blend/Inpaint/Upscale 2x/Upscale 4x/PicReader/Reroll
   1. ```
      中文释义：绘图/变换/变焦/焦点移动/混图/局部重绘/放大2倍/放大4倍/图生文后生成图片/重新生成
      ```
2. 类型 2 端点包括：Upscale/Describe/PicReaderRetry/FaceSwap/Shorten
   1. ```
      中文释义：放大/图生文/图生文重新生成/换脸/prompt分析
      ```
3. 类型 3 端点包括：Fetch/ListByIDs/Modal/Seed
   1. ```
      中文释义：获取单个任务进度/批量获取任务/确认提交弹窗任务/获取Seed
      ```

<br/>



## 常见项目配置方式

### **python openai官方库（使用AutoGPT，langchain等）**

示例代码请参考[demo.py](https://token173.net/demo.py)

***方法一***

```python
import openai
openai.api_base = "https://token173.net/v1"
```

***方法二（方法一不起作用用这个）***

修改环境变量OPENAI_API_BASE，各个系统怎么改环境变量请自行搜索，修改环境变量后不起作用请重启系统。

```sh
OPENAI_API_BASE=https://token173.net/v1
```


### **开源gpt_academic**

找到`config.py`文件中的`API_URL_REDIRECT`配置并修改为以下内容：

```python
API_URL_REDIRECT = {"https://api.openai.com/v1/chat/completions": "https://token173.net/v1/chat/completions"}
```


### **ChatBox(推荐使用)**

ChatGPT开源桌面应用，支持全部桌面平台。

下载链接：https://github.com/Bin-Huang/chatbox/releases

使用方法：如图在设置中填入购买的密钥，并将代理设置为`https://token173.net`即可


