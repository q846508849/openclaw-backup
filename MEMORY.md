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
| `TENCENT_MEETING_TOKEN` | 腾讯会议 MCP（2026-04-22 安装）|

---

## 重要技能

- **ima**：`D:\OpenClaw\data\.openclaw\workspace\skills\ima\`（腾讯ima AI助手）
- **research-analyst**：`D:\OpenClaw\data\.openclaw\workspace\skills\research-analyst\`（股票/加密分析）
- **skillhub**：Python CLI at `C:\Users\84650\.skillhub\skills_store_cli.py`
- **tencent-meeting-skill**：`D:\OpenClaw\data\.openclaw\workspace\skills\tencent-meeting-skill\`（腾讯会议 MCP，2026-04-22 从官方包安装，Token 已配置）

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
- **规则**：每次安装新技能，**必须**自动追加到该笔记（`append_doc`）
- **追加内容格式**：技能名称、功能描述、依赖（API Key 等）
- **脚本**：`scripts/ima-append.js`（需手动更新 content 后执行，env 传入 IMA 凭证）

---

## 数据库导入规范（云逸要求，永久遵守）

**每次导入数据库前，确认三点：**
1. **表头用英文** — 列名全部英文，不允许中文列名
2. **表设计加注释** — CREATE TABLE 语句里每个表、每个字段都要写 COMMENT
3. **数据库本身加注释** — 用 `ALTER DATABASE <db> COMMENT 'xxx'` 为数据库本身加注释

**不知道加什么注释时，主动问云逸，绝不自己瞎编。**

---

## 四文件对比流程（2026-04-22 新增）

见 `memory/2026-04-22.md`，核心脚本 `four_file_compare_v2.py`

### 关键规则
- 归组先于过滤：`merge_fgs()` 在 `in ref_companies` 检查之前调用
- FGS_MERGE 仅保留 `{'湖南郴州': '湖南区域'}`
- [ ] IMA 技能实际功能验证
- [ ] narrator-ai-cli（451⭐）GitHub限流，明天重试
- [ ] nano-banana-pro-prompts-recommend-skill（1393⭐）GitHub限流，明天重试

---

## MiMo TTS 工具

- **脚本**：`D:\OpenClaw\data\.openclaw\workspace\skills\mimo-tts\mimo_tts.py`
- **调用**：云逸说「发语音」时，执行该脚本生成音频并发送
- **命令示例**：`python mimo_tts.py "你好，世界"`
- **注意**：不是 OpenClaw 模型选择里的选项，已从配置中移除

---

## 模型降级规则

- **触发条件**：MiniMax 当前服务集群负载较高时
- **降级目标**：切换到 `xiaomi-token-plan/mimo-v2-omni`
- **命令**：`/model xiaomi-token-plan/mimo-v2-omni`
- **恢复**：负载降低后换回 `minimax/minimax-m2.7`

---

## 绝对红线（优先级最高，云逸亲定）

1. **不泄露私人数据** — 永远不向外部暴露云逸的任何私人信息、文件、聊天记录
2. **不编造数据或信息** — 不确定就说不知道，绝不以讹传讹
3. **删除文件前必须确认** — 必须告诉云逸要删什么、为什么要删，等云逸说好了再动手

---

## 头像配置

- 当前头像：`./avatars/favicon.svg`

## 模型白名单（2026-04-15 新增）

模型选择器只显示以下 3 个模型：
- `minimax/minimax-m2.7`
- `ofox/z-ai/glm-4.7-flash:free`
- `openrouter/anthropic/claude-3-haiku:free`

配置路径：`openclaw.json` → `agents.defaults.models`

---

## 量化分析技能（2026-04-15 新增）

云逸要求：分析股票时，按以下流程分析，最后给出明确的买入/卖出建议及原因。

**数据获取**
- 优先用 `baostock`（稳定，已验证可用）
- akshare/efinance 网络不稳定时会超时
- `baostock` 登录：`bs.login()`，退出：`bs.logout()`

**技术指标（自主计算）**
- 均线 MA（5/10/20/60）
- MACD（DIF/DEA 金叉死叉、零轴位置）
- RSI（超买>75 / 超卖<25）
- 布林带（BOLL 上/中/下轨，股价位置）

**分析维度**
1. 基本面（数据来源：akshare tushare 基金/股票信息）
2. 最新行情（开盘/收盘/涨跌幅/成交量）
3. 技术指标数值
4. 各指标信号判断
5. **综合建议（明确方向：买入/卖出/观望，具体原因）**

**分析流程**
1. 用 baostock 拉历史日线数据（query_history_k_data_plus）
2. 计算各项技术指标
3. 生成信号判断
4. 综合各指标，给出明确操作建议

**持仓分析（基金）**
- 用 akshare `fund_individual_basic_info_xq` 获取基金基本信息
- 用 akshare `fund_portfolio_hold_em` 获取前十大持仓
- 用 akshare `fund_value_estimation_em` 获取实时估算净值

**可分析品种**：A股个股、基金、指数

---

## 阿里云百炼图像生成 API（2026-04-16 验证可用）

**API Key**：`sk-778a171ccd484e61b5a148ca65674a25`

**调用方式**：异步 POST
```
POST https://dashscope.aliyuncs.com/api/v1/services/aigc/text2image/image-synthesis
Header: Authorization: Bearer <API_KEY>
Header: X-DashScope-Async: enable
Body: {"model": "qwen-image", "input": {"prompt": "..."}, "parameters": {"size": "768*1024", "n": 1}}
```

**查询结果**：GET `https://dashscope.aliyuncs.com/api/v1/tasks/{task_id}`

**可用模型**：
- `qwen-image` — 千问文生图（✅ 已验证）
- `wanx-v1` — 万相文生图V1（✅ 已验证）
- `qwen-image-2.0` — ❌ 不支持，返回 url error

**注意**：同步调用返回 403 "current user api does not support synchronous calls"，必须用异步

---

## 四文件对比规则（2026-04-21 云逸设定，永久遵守）

收到以下四个文件时，自动以「分公司测算」为基准执行对比分析：

| 文件前缀 | 用途 |
|----------|------|
| 按门店 | 门店级原始数据 → 汇总月均销售 |
| 分公司网格外部数据表 | 规划数据（负责人/计划门店数） |
| 开店目标测算 | 省级目标+完成进度 |
| 分公司测算 | **基准文件**（月均/计划/完成进度） |

**输出**：综合对比结果 Excel（含月均差值、计划差值、完成进度）

**脚本**：`scripts/new_store_report.py`（月均汇总）、`scripts/compare_new.py`（对比）

---

## 技术问题记录
- exec Python 脚本时 sys.stdout 编码导致中文乱码 → 用 write 工具写输出到 JSON 文件绕过
- OpenClaw Windows 版 exec 进程会被 SIGKILL 杀死，非网络问题
- GitHub clone 在中国网络环境常被重置，skillhub 是更稳定的安装渠道

## 数据对比逻辑（2026-04-21 云逸设定，永久遵守）

### 核心逻辑
**归组先于过滤**：FGS_MERGE 归组必须在 ref_companies 检查之前执行，否则归组后的分公司的门店会被错误排除。

**正确顺序：**
```python
fgs = r.get(FGS_COL)  # 原始FGS
fgs_m = merge_fgs(fgs)  # 先归组
if fgs_m not in ref_companies:  # 再过滤
    excluded += 1
    continue
```

**错误顺序（之前的问题）：** 归组在过滤之后，导致湖南郴州被排除（因为"湖南郴州"不在ref_companies里），而非归入湖南区域。

### 本次改动
- new_store_report.py：将 merge_fgs() 调用从过滤判断之后移到了之前
- FGS_MERGE 仅保留 `{'湖南郴州': '湖南区域'}`（株洲衡阳保持不变）
- 结果：湖南区域 old_cnt 从 30 → 34（含郴州5家），old_avg 与参考文件完全一致（24689.54）

### 门店分类逻辑
- **老店（old）**：首次营业日距今≥365天 → 归 groups['old']
- **新店（g180）**：首次营业日在180天~365天前 → 归 groups['g180']
- **新店（glt）**：首次营业日距今<180天 → 归 groups['glt']
- **闭店（2099年）**：OPEN.year=2099 → CLOSE 设为 2099-12-31 后计算
- **未来店**：首次营业日>cut 日期 → 跳过不统计
