# 🧠 Long-Term Memory — AI 记忆中间件

[![ClawHub](https://img.shields.io/badge/ClawHub-memory--for--openclaw-blue)](https://clawhub.ai/skills/memory-for-openclaw)

为 AI Agent 提供 **持久化、跨会话的长期记忆** 能力，解决大模型「过目就忘」的痛点。自动捕获关键事实、决策、用户偏好和项目上下文，支持语义搜索和向量检索，让 AI 真正记住你。

---

## 🚀 版本与定价

### 社区版（开源免费）

当前版本为 **开源社区版**，适合个人开发者本地自部署。

✅ 所有功能无限制使用  
✅ 无记忆条数限制  
✅ 无需注册、无需付费  

👉 [ClawHub 安装](https://clawhub.ai/skills/memory-for-openclaw)

```bash
clawhub install memory-for-openclaw
```

---

### 💼 企业版 / 技术支持服务

本地部署遇到困难？需要定制化配置？我来帮你搞定。

| 服务项目 | 价格 | 说明 |
|:---|---:|:---|
| **远程部署** | **¥199/次** | 远程帮你搭好完整环境，跑通持久化记忆 |
| **定制开发** | 另议 | 根据需求定制功能、对接现有系统 |
| **技术咨询** | 另议 | 架构设计、方案评审、性能优化 |

> 📞 **联系我们**：微信 **18923788188**（王工）

---

### ☁️ MaaS 云服务（2026年6月公测预告）

即插即用的云端记忆服务，无需部署，开箱即用。

| 套餐 | 价格 | 容量 | 功能 |
|:---|---:|---|---|
| **公测版** | **免费** | 前100条免费 | 云端API、基础记忆存储 |
| **Starter** | **¥49/月** | 1万条记忆，3个项目 | 标签分类、项目隔离 |
| **Pro** | **¥199/月** | 10万条记忆，无限项目 | 向量检索、语义搜索 |
| **Enterprise** | 定制报价 | 无限容量 | 私有部署、SLA保障、专属存储、审计日志 |

> ⏰ **公测时间**：2026年6月  
> 🔗 **支付方式**：支付宝（微信：18923788188 王工）

---

## 📦 安装

### 通过 ClawHub 安装（推荐）

```bash
clawhub install memory-for-openclaw
```

### 直接克隆

```bash
git clone https://github.com/szwangw/long-term-memory.git
cd long-term-memory
pip install -r scripts/requirements.txt
python scripts/setup.py
```

---

## 🔧 使用方法

```bash
# 保存一条记忆
python scripts/memory_engine.py remember "决定: 使用FastAPI框架" --tags decision,tech --importance 8 --project saas

# 搜索记忆
python scripts/memory_engine.py search "技术方案" --tags tech --min-imp 5

# 启动新会话（返回 session_id + 上下文）
python scripts/memory_engine.py session-start

# 结束会话并总结
python scripts/memory_engine.py session-end <session_id> --summary "完成了架构设计"

# 自动捕获（扫描文本中的决策、事实、偏好）
python scripts/memory_engine.py auto "我们决定采用SQLite作为数据库，技术栈为FastAPI..."

# 统计
python scripts/memory_engine.py stats
```

---

## 🏗 记忆结构

| 字段 | 说明 |
|------|------|
| content | 记忆内容 |
| tags[] | 标签（如 `decision`, `tech`, `user`, `project:X`） |
| importance | 重要程度 1-10（8+=关键事实，6-7=有用上下文，1-5=普通） |
| source | 来源（agent/手动/自动） |
| session | 会话ID |
| project | 所属项目 |
| timestamps | 创建/更新时间 |

---

## 📁 数据存储位置

```
~/.openclaw/workspace/long-term-memory/
├── memory.db          # SQLite 数据库
├── config.json        # 配置文件
└── current_context.md # 最近构建的上下文（调试用）
```

---

## 🔄 自动化捕获

引擎会自动从文本中检测重要内容：

| 触发关键词 | 标签 | 默认重要性 |
|:---|---|:---:|
| 决定, 选择, 采用, 改为, 升级, 弃用 | `decision` | 7 |
| 项目名, 产品名, 公司, 版本, 价格 | `fact` | 6 |
| 喜欢, 偏好, 习惯, 不要, 推荐 | `preference` | 6 |
| 技术栈, 框架, 语言, 数据库, API, 部署 | `tech` | 5 |
| 问题, bug, 报错, 异常, 失败 | `problem` | 5 |

---

## 📋 项目结构

```
├── README.md                  # 本文件
├── SKILL.md                   # ClawHub 技能描述
├── scripts/
│   ├── memory_engine.py       # 记忆引擎核心
│   ├── setup.py               # 一次性环境设置
│   └── requirements.txt       # Python 依赖
├── tests/
│   ├── test_engine.py         # 单元测试
│   └── final_test.py          # 集成测试
└── docs/
    └── (更多文档待更新)
```

---

## 📞 联系方式

- **微信**：18923788188（王工）
- **GitHub**：[szwangw/long-term-memory](https://github.com/szwangw/long-term-memory)
- **ClawHub**：[memory-for-openclaw](https://clawhub.ai/skills/memory-for-openclaw)

---

## 📄 开源协议

MIT-0 — 免费使用、修改和再分发，无需署名。
