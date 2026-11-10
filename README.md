# Claude 中转站推荐：国内直连 Claude API，Claude Code 改两个变量就能跑

Anthropic 官方 API 对国内用户是硬门槛：注册要海外手机号，付款只认境外信用卡，国内 IP 直接访问 `api.anthropic.com` 基本是 403 或超时。就算靠代理注册成功，IP 一飘、用量一异常，账号说封就封，充进去的钱拿不回来。

Token173（https://token173.net）做的是把官方额度批量买下来、架国内节点、按 Anthropic 协议对外提供入口。你要做的只有一件事：把 `base_url` 和 Key 换掉，其余代码不动。

## 能调的 Claude 模型

| 模型 ID | 常用场景 |
|---|---|
| `claude-opus-5-5` | 复杂重构、跨文件改代码、长文档推理 |
| `claude-sonnet-5-5` | 日常主力，速度和质量折中 |
| `claude-haiku-5-5` | 分类、抽取、批量清洗，便宜跑量 |
| `claude-fable-5`、`claude-fable-5-1` | 创意写作、文案改写 |
| `claude-opus-4-8` | 上一代，老项目不用改模型名 |

同一个 Key 还能顺带调 `gpt-6-astra`、`gemini-3.8-flash`、`grok-4.7`，做横向对比时不用再准备第二套凭据。

## Claude Code 接入

```bash
export ANTHROPIC_BASE_URL="https://token173.net"
export ANTHROPIC_API_KEY="sk-你的令牌"
```

改完重启终端，跑一句 `claude --version` 确认起来了，再让它读一个文件试试。地址末尾**不要加 `/v1`**，这是报 404 最常见的原因。

要写进 shell 配置的话：

```bash
echo 'export ANTHROPIC_BASE_URL="https://token173.net"' >> ~/.zshrc
echo 'export ANTHROPIC_API_KEY="sk-你的令牌"' >> ~/.zshrc
source ~/.zshrc
```

## SDK 调用

```python
import anthropic

client = anthropic.Anthropic(
    api_key="sk-你的令牌",
    base_url="https://token173.net",
)

msg = client.messages.create(
    model="claude-sonnet-5-5",
    max_tokens=1024,
    messages=[{"role": "user", "content": "这个函数有什么性能问题？"}],
)
print(msg.content[0].text)
```

Node.js 同理，`new Anthropic({ apiKey, baseURL })` 两个参数换掉即可。

## Cursor / Cline / Cherry Studio

| 工具 | 填什么 |
|---|---|
| Cursor | Settings → Models → 勾 Override Anthropic Base URL，填 `https://token173.net`，Key 填令牌 |
| Cline | API Provider 选 Anthropic，Base URL 填 `https://token173.net` |
| Cherry Studio | 供应商选 Anthropic，API 地址 `https://token173.net`，模型名手填 `claude-opus-5-5` |
| LobeChat | 同上，自定义 Anthropic 端点 |
| OneAPI / NewAPI | 作为 Anthropic 类型渠道接入 |

## 价格

- 2 元 = 1 美元额度，一个账号所有模型通用
- 注册送 0.2 美元，先测再用
- 按 token 计费，后台日志逐笔可查，失败请求不扣费

按这个比例算，Claude 系列的实际成本大概在官方价的三折上下，属于国内中转的常规区间。

## 用之前值得知道的几件事

**模型有没有被换掉。** 回包里 `model` 字段写的就是实际跑的模型。接进去第一件事：发一条请求，看返回的 model 是不是你要的那个。有些便宜站会拿 `haiku` 冒充 `opus`，这个字段对不上就是对的。

**充值别一次上大额。** 先用 10 块钱跑一周，确认延迟和成功率能接受，再加。中转行业跑路的小站不少，这是行业常识不是针对谁。

**敏感内容别直接过。** 请求会经过中转服务器，内部源码、客户资料这类东西，先评估再说。

## 常见问题

**Q：Claude Code 提示连不上或 401？**
依次查三件事：环境变量有没有生效（新开一个终端 `echo $ANTHROPIC_BASE_URL`）、Key 是不是复制全了（前后有空格会失败）、后台令牌有没有绑分组。

**Q：能不能和官方 Key 混着用？**
不建议。一个工具里两套凭据容易搞混，真要备份就建两个令牌，用哪个切哪个。

**Q：并发有上限吗？**
按账号算，日常开发用不满。要跑大批量任务先在后台看下当前分组的并发说明。

**Q：支持 Claude Code 的哪些功能？**
流式返回、工具调用、长上下文都走官方协议，能正常用。遇到某个特性不行的，大概率是客户端版本问题，先把客户端升到最新。

## 相关

- 接入文档全集：https://docs.token173.net
- GPT 专题：[gpt-api](https://github.com/Token173/gpt-api)
- Gemini 专题：[gemini-api](https://github.com/Token173/gemini-api)
- 多模型对比：[2026-Token173-Claude-ChatGPT-Grok-Gemini-AI-API](https://github.com/Token173/2026-Token173-Claude-ChatGPT-Grok-Gemini-AI-API)
