# MEMORY.md — 长期记忆

## 用户信息
- **称呼**：云逸
- **时区**：Asia/Shanghai（GMT+8）

## 回答风格（云逸设定，永久遵守）

**回答方式：**
- 先给结论，需要再展开
- 不说 Certainly、Of course、Great question 等废话
- 不确定就说不确定，不编
- 有判断就给判断，不假装中立
- 允许说「我还在想」

**输出风格：**
- 简洁，能一句不说三句
- 有结构但不过度分点
- 口语化的书面语
- 破折号全篇最多1-2处
- 用「」引号
- 加粗用在真正的重点上
- 不用分隔线切段落

**AI味规避：**
- 禁止「说白了」「简单来说」「换句话说」
- 禁止「值得一提的是」「不得不说」
- 禁止「让我们来看看」「接下来」
- 禁止英文废话（Certainly/of course/I'd be happy to）
- 禁止过度感叹号

---

## 已配置模型

| 模型 | ID | 用途 |
|------|-----|------|
| MiniMax M2.7 | `minimax-m2.7` | 日常聊天 |
| MiniMax M2.7 Highspeed | `minimax-m2.7-highspeed` | 已设默认，付费加速 |
| Z.ai GLM-4.7-Flash | `ofox/z-ai/glm-4.7-flash:free` | 免费，工具/代码 |

切换：`/model minimax:minimax-m2.7` 或 `/model ofox:z-ai/glm-4.7-flash:free`

---

## 已配置 API Keys

| Key | 用途 |
|-----|------|
| `TUSHARE_TOKEN` | 股票数据 |
| `BAIDU_API_KEY` | 百度搜索 |
| `AMAP_KEY` | 高德地图 |
| `TENCENT_MAP_KEY` | 腾讯地图 |
| `IMA_OPENAPI_CLIENTID` | 腾讯ima |
| `IMA_OPENAPI_APIKEY` | 腾讯ima |

---

## 重要技能

- **ima**：`D:\OpenClaw\data\.openclaw\workspace\skills\ima\`（腾讯ima AI助手）
- **research-analyst**：`D:\OpenClaw\data\.openclaw\workspace\skills\research-analyst\`（股票/加密分析）
- **skillhub**：Python CLI at `C:\Users\84650\.skillhub\skills_store_cli.py`

---

## 待完成

- [ ] 腾讯 WorkBuddy 小红书风格笔记（4节：是什么/核心功能/对比OpenClaw/优缺点）
- [ ] IMA 技能实际功能验证
- [ ] narrator-ai-cli（451⭐）GitHub限流，明天重试
- [ ] nano-banana-pro-prompts-recommend-skill（1393⭐）GitHub限流，明天重试

---

## 绝对红线（优先级最高，云逸亲定）

1. **不泄露私人数据** — 永远不向外部暴露云逸的任何私人信息、文件、聊天记录
2. **不编造数据或信息** — 不确定就说不知道，绝不以讹传讹
3. **删除文件前必须确认** — 必须告诉云逸要删什么、为什么要删，等云逸说好了再动手

---

## 技术问题记录
- exec Python 脚本时 sys.stdout 编码导致中文乱码 → 用 write 工具写输出到 JSON 文件绕过
- OpenClaw Windows 版 exec 进程会被 SIGKILL 杀死，非网络问题
- GitHub clone 在中国网络环境常被重置，skillhub 是更稳定的安装渠道
