# 笔杆子 · 公文写作 Skill

<p align="center">
  <img src="assets/gw-workflow-infographic.png" alt="笔杆子 · 公文写作 Skill 信息图" width="720">
</p>

<p align="center">
  <strong>gw-workflow</strong> — 跨平台 Agent Skill，材料狗专用公文完整工作流<br>
  不光 Prompt 而已，是<strong>先问清、再写稿、再质检</strong><br>
  作者：<strong>小T同学</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Agent-Skill-blue?style=flat-square" alt="Agent Skill">
  <img src="https://img.shields.io/badge/Cursor-✓-lightgrey?style=flat-square" alt="Cursor">
  <img src="https://img.shields.io/badge/Codex-✓-lightgrey?style=flat-square" alt="Codex">
  <img src="https://img.shields.io/badge/WorkBuddy-✓-lightgrey?style=flat-square" alt="WorkBuddy">
  <img src="https://img.shields.io/badge/version-v2.5-red?style=flat-square" alt="v2.5">
  <img src="https://img.shields.io/badge/错词词库-180%2B条-orange?style=flat-square" alt="180+ 错词">
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="MIT">
</p>

---

## 30 秒了解

| | |
| --- | --- |
| **给谁用** | 写汇报、讲话、调研、方案、请示、通知的「笔杆子」 |
| **解决什么** | AI 写公文容易假大空、踩敏感词、像 ChatGPT；或短稿被流程搞复杂 |
| **怎么不同** | **按轻重分流**：短请示可简写；长材料才确认单+逻辑+润色；站位跟汇报对象走 |
| **默认场景** | 机关公文（中央到市县均可，不预设省部级） |
| **运行环境** | 任何支持 [Agent Skills](https://agentskills.io) 规范的客户端 |

---

## 兼容平台

本 Skill 遵循标准 `SKILL.md` 格式，**不绑定单一 IDE**。克隆到对应客户端的 skills 目录即可使用：

| 平台 | 个人级安装路径 | 调用方式 |
| --- | --- | --- |
| **Cursor** | `~/.cursor/skills/gw-workflow` | `/gw-workflow` 或 `@gw-workflow` |
| **Codex** | `~/.codex/skills/gw-workflow` | 对话中提及「gw-workflow / 笔杆子 / 公文」触发 |
| **WorkBuddy** | `~/.workbuddy/skills/gw-workflow` 或 `~/.codebuddy/skills/gw-workflow` | 按 trigger 自动激活，或直接 @skill |
| **通用** | `~/.agents/skills/gw-workflow` | 其他兼容 Agent Skills 的客户端 |

也可通过 Skills CLI 安装（若已接入 [skills.sh](https://skills.sh) 生态）：

```bash
npx skills add YUKEE-spec/gw-workflow -g -y
```

> 项目级安装：将本目录放入各平台的项目 skills 路径（如 `.cursor/skills/`、`.codebuddy/skills/`），团队可共享。

---

## 核心工作流

```
轻量：要点齐 → 确认主送/事项 → 起草 → 敏感词
标准/加重：澄清（对象层级）→（确认单）→（提纲）→ 起草 → 按需润色 → 交付
```

| 步骤 | 做什么 | 为什么 |
| ---: | --- | --- |
| 0 | 判轻量 / 标准 / 加重 | 800 字请示不走长流程 |
| 1 | 加载错词词库 | 定稿合规 |
| 2 | 按需问诊；对齐**汇报对象级别** | 站位匹配，不默认高规格 |
| 3 | 只从材料提取事实 | **不编造** |
| 4 | 加重才出逻辑提纲 | 先通篇后咬字 |
| 5 | 按文种起草；落实类且需要时定锚 | 短稿少空话 |
| 6 | 润色深度随档位 | 逻辑优先可追溯 |
| 7 | 需要时输出 docx | 内容与版式分工 |

---

## 亮点功能

### 1. 先问清对象，再决定问多少

短请示少问快写；长材料才出《任务确认单》。站位跟**汇报/主送对象级别**走，你要什么级别模型就写什么级别。

### 2. 180+ 条错词词库

内置 [`错词词库-20260708.csv`](错词词库-20260708.csv)，错词 → 建议词，支持通配符（`*` / `?`）。

覆盖：公平竞争表述、过时政策品牌、党史党建规范、涉台涉疆、形式主义减负、口语化用语等。

> 重点禁用示例：`放管服` · `一件事一次办` · `市场主体`（非文件原文引用时）

### 3. 逻辑通读 + 降 AI 味（长稿）

加重稿先过逻辑再抠文风；落实类按对象需要定锚。轻量稿以敏感词与空话清理为主。

### 4. Word 输出（可选）

正文定稿后，在 Cursor 等环境可衔接 **document-skill** 排版；其他平台可用 `python-docx` 或手动粘贴到 Word。

| gw-workflow | 排版 / docx |
| --- | --- |
| 对话澄清、逻辑、定锚、错词、正文 | Word 版式、三线表等 |

---

## 快速开始

### 方式一：git clone（推荐）

```bash
git clone https://github.com/YUKEE-spec/gw-workflow.git ~/.cursor/skills/gw-workflow   # Cursor
git clone https://github.com/YUKEE-spec/gw-workflow.git ~/.codex/skills/gw-workflow     # Codex
git clone https://github.com/YUKEE-spec/gw-workflow.git ~/.workbuddy/skills/gw-workflow # WorkBuddy
```

任选其一即可；多平台共用时可 clone 到 `~/.agents/skills/gw-workflow`。

安装后重启客户端或新开 Agent 对话。

### 方式二：Skills CLI

```bash
npx skills add YUKEE-spec/gw-workflow -g -y
```

### 调用示例

```text
/gw-workflow 起草一份向省委常委会汇报的 XX 工作材料，背景材料如下：……
```

```text
用 gw-workflow 润色下面这段，注意错词词库和降 AI 味：……
```

（Codex / WorkBuddy 无 slash 命令时，直接在对话中 @skill 或说明「按 gw-workflow 流程处理」。）

---

## 适用文种

汇报材料 · 讲话稿 · 调研报告 · 工作方案 · 通知 · 请示 · 局部润色

文种不预设，由对话澄清确定；各文种有专属问诊清单（见 `reference-intake.md`）。

---

## 文件结构

```
gw-workflow/
├── assets/
│   ├── gw-workflow-infographic.png   # GitHub 横版信息图（16:9）
├── SKILL.md                          # Agent 首读（核心流程）
├── 错词词库-20260708.csv             # 错词→建议词主表（可替换更新）
├── reference-intake.md               # 对话澄清、文种问诊
├── reference-logic.md                # 篇章逻辑、段落功能、逻辑通读
├── reference-sensitive.md            # 敏感词与引用纪律
├── reference-templates.md            # 文种结构、政治开篇定锚
├── reference-style.md                # 四遍润色、评分、检查清单
├── examples.md                       # 轻量/标准/加重示例
├── tests.md                          # 回归测试用例
└── LICENSE
```

---

## 版本

| 版本 | 说明 |
| --- | --- |
| **v2.5.1** | 改稿可在 Word 批注/修订交付（衔接 document-skill） |
| v2.5 | 去掉处处省部级预设；按汇报对象调站位；短稿轻量路径 |
| v2.4.2 | 结构范文 B（南方AI产业实地调研报告） |
| v2.4.1 | 结构范文 A（世AI大会主旨讲话） |
| v2.4 | 篇章逻辑；政治开篇定锚；四遍润色 |
| v2.3 | 错词词库（180+ 条） |
| v2.2 | 更名为 `gw-workflow` |
| v2.1 | 拆分 reference；文种问诊 |
| v2.0 | 对话澄清、站位、敏感词 |
| v1.0 | 上游 [official-document-skill](https://github.com/Liuxiangjian-ai/official-document-skill) |

---

## 致谢 Acknowledgments

**作者：小T同学**

## skillhub评分
<img width="2158" height="1258" alt="b7ad5aa06f62e5b3e77b8f7819ed63c5" src="https://github.com/user-attachments/assets/71e00952-c232-4d39-b9e7-5d4abff75f15" />
