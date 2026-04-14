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

## 备份操作（云逸设定，永久遵守）

每次说「备份」时，执行以下两步：

**① GitHub 推送**（MEMORY.md + memory/）
```bash
cd D:\OpenClaw\data\.openclaw\workspace
git add MEMORY.md memory/
git commit -m "backup YYYY-MM-DD"
git push origin main
```

**② openclaw.json 本地备份**
```powershell
copy "D:\OpenClaw\data\.openclaw\openclaw.json" "C:\openclaw-config-backup-YYYY-MM-DD.json"
```

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

## GitHub 备份仓库

- 仓库：https://github.com/q846508849/openclaw-backup
- 包含：MEMORY.md、memory/
- **API Key 不推送 GitHub**

---

## 数据库账号密码（永久记录，勿再询问）

### MySQL（本地）
- **Host**：`127.0.0.1`
- **User**：`root`
- **Password**：`qq846508849`
- **Port**：`3306`
- 已导入门店档案：`store_db.store_archive`（9991行，24列）

### PostgreSQL（远程）
- **Host**：`172.168.15.226`
- **User**：`q846508849`
- **Password**：`qq846508849`
- **Port**：`5432`

---

## 记忆压缩规则（2026-04-10 生效）

- 执行 COMPACTION 时禁止输出任何系统消息
- 静默后台处理，不回复任何内容
- 仅异常时告警

## HEARTBEAT 规则（2026-04-10 生效）

- 收到心跳时后台巡检，**禁止在聊天界面输出任何内容**（包括 HEARTBEAT_OK）
- 仅严重异常（任务失败/服务故障）才输出告警消息
- 正常心跳场景静默，不回复任何内容

## IMA 技能清单（永久规则）

- **笔记 ID**：`7448214722580499`
- **规则**：每次安装新技能，自动按类别整理后用 `append_doc` 追加到该笔记
- **追加内容格式**：技能名称、功能描述、依赖（API Key 等）

---

## 数据库导入规范（云逸要求，永久遵守）

**每次导入数据库前，确认三点：**
1. **表头用英文** — 列名全部英文，不允许中文列名
2. **表设计加注释** — CREATE TABLE 语句里每个表、每个字段都要写 COMMENT
3. **数据库本身加注释** — 用 `ALTER DATABASE <db> COMMENT 'xxx'` 为数据库本身加注释

**不知道加什么注释时，主动问云逸，绝不自己瞎编。**

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
