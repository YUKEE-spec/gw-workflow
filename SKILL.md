---
name: gw-workflow
description: >-
  笔杆子 · 省部级公文工作流（gw-workflow）。先对话澄清背景材料与输出要求，再起草润色；
  强调站位、敏感词合规、降AI味。文种随场景而定。Use for 公文、gw-workflow、笔杆子、
  省部级材料、汇报材料、讲话稿、润色、降AI味.
---

# 笔杆子 · 公文工作流（gw-workflow）

## 致谢

基于 [Liuxiangjian-ai/official-document-skill](https://github.com/Liuxiangjian-ai/official-document-skill) 深度定制，感谢原作者在公文格式、降 AI 味与润色规范方面的扎实工作。本 Skill 为个人衍生版，面向省部级机关材料场景。

## 版本

- **v2.3**（当前）：接入用户错词词库 `错词词库-20260708.csv`
- **v2.2**：更名为 `gw-workflow`（笔杆子 · 公文工作流）
- **v2.1**：拆分 reference、文种专属问诊、敏感词独立、docx 衔接
- **v2.0**：对话澄清、站位、敏感词表、汇报材料问诊
- **v1.0**：上游 official-document-skill

## Purpose

生成或修订**结构正确、可交付、事实扎实、站位适当、低 AI 味**的中文公文。默认 **省部级**（省级或部级机关，以用户当次任务为准），**文种不预设**，由对话澄清确定。

## 业务场景（摘要）

**省级侧**：向中央/部委汇报，常委会常务会材料，全省部署，对市州指导。  
**部级侧**：向党中央国务院汇报，部党组会材料，全系统部署，对省厅局指导。

**站位要够** = 对接中央及本级重大部署 + 事实机制数据支撑，非堆口号。

| 高度够 | 假高度 |
| --- | --- |
| 对接年度重点，落到本机关本阶段任务 | 宏观套话无本事项 |
| 省部级视角统筹协同 | 处室工作写成「历史性突破」 |

## 核心工作流

0. **识别任务模式**：从零起草 / 润色 / 局部改写。新建复杂文种 → **必须先对话澄清**（详见 [reference-intake.md](reference-intake.md)）。
1. **场景与敏感词**：确认省/部层级与主体；加载 [reference-sensitive.md](reference-sensitive.md) 与 [`错词词库-20260708.csv`](错词词库-20260708.csv)。
2. **对话澄清**：三阶段问诊 →《任务确认单》→ 用户确认（或用户明示跳过）。
3. **选文种与提取事实**：仅来自用户输入与背景材料，**不编造**。
4. **（可选）提纲**：≥3000 字、结构复杂或用户要求时先出提纲。
5. **起草**：按 [reference-templates.md](reference-templates.md) 结构；省部级站位。
6. **三遍润色**：降 AI 味 → humanizer → 敏感词全文检索（见 [reference-style.md](reference-style.md)）。
7. **评分 ≥80** 后交付正文；润色附《修改说明》（格式见 reference-intake.md）。
8. **需 `.docx` 时**：正文定稿后调用 **document-skill** 排版；本 Skill 负责内容与公文规范。

## 输出默认

- 语言：中文。
- **新建**：先《任务确认单》，确认后再写；不凭一句话生成长文。
- 事实不足：出提纲或带 `〔待补充〕` 框架稿，并说明缺什么。
- 不编造法律法规、文件、领导、数据、会议、批复。
- 正文不含聊天腔（「当然可以」「以下是」等）。

## 敏感词（强制摘要）

定稿前检索 [`错词词库-20260708.csv`](错词词库-20260708.csv)（错词→建议词，含通配符）。  
重点禁用：**放管服**、**一件事一次办**、**市场主体**（非文件原文引用时）。用户补充词同等强制。  
细则 → [reference-sensitive.md](reference-sensitive.md)。

## 延伸阅读

| 内容 | 文件 |
| --- | --- |
| 对话澄清、文种问诊 | [reference-intake.md](reference-intake.md) |
| 文种结构、格式 | [reference-templates.md](reference-templates.md) |
| 降 AI 味、质检 | [reference-style.md](reference-style.md) |
| 示例 | [examples.md](examples.md) |

## 与 document-skill 分工

本 Skill 产出正文；Word 排版调用 `document-skill`：「正文已定稿，请用 document-skill 输出 docx。」
