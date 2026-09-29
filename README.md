<div align="center">

# 🗂️ Privacy_Skills_and_Prompt_SQL

**AI 协作知识库 · AI Collaboration Knowledge Base**

[![Docs](https://img.shields.io/badge/docs-3-2E86AB?style=flat-square)](#index)
[![Language](https://img.shields.io/badge/language-中文_·_EN-C73E1D?style=flat-square)](#about)
[![Commit](https://img.shields.io/badge/commit-双语_Bilingual-4CAF50?style=flat-square)](#rules)
[![Push](https://img.shields.io/badge/push-仅限本人_owner_only-D32F2F?style=flat-square)](#rules)

*给人类看的门面，给 AI 看的规矩。*
*A front door for humans, ground rules for AI.*

</div>

---

<a id="about"></a>
## 📌 关于本仓库 · About

**中文**
本仓库沉淀 AI 协作过程中产生的三类知识：约束所有仓库的**规范**、单个项目的
**接手手册**、可跨项目复用的**技法复盘**。目标与各手册一致——任何人（或 AI）
读完这一页，就知道该读哪份文档、按什么规矩干活。

**English**
This repository curates three kinds of knowledge produced while working with AI
assistants: **standards** that bind every repository, per-project **operating
manuals**, and reusable **playbooks**. The goal matches every manual here —
anyone (human or AI) should finish this page knowing which document to read
and under which rules to work.

---

<a id="layout"></a>
## 🗺️ 目录结构 · Layout

```text
Privacy_Skills_and_Prompt_SQL/
├── README.md                        ← 你在这里 · You are here
├── 01_规范_Standards/               约束所有仓库 · binds all repos
│   └── 代码与提交规范.md
├── 02_手册_Manuals/                 项目级接手手册 · per-project manuals
│   └── yolo项目_工作流程与注意事项.md
└── 03_技法_Playbooks/               跨项目复用方法 · reusable techniques
    └── GitHub搜索_问题与解决手法.md
```

| 目录 Folder | 放什么 · What belongs here |
|---|---|
| `01_规范_Standards` | 跨仓库的规则、格式与红线，对所有项目生效 · Cross-repo rules, formats and red lines |
| `02_手册_Manuals` | 单个项目的完整接手手册，AI 读完即可接手 · A complete handover manual for one project |
| `03_技法_Playbooks` | 与具体项目无关、可反复使用的方法与踩坑复盘 · Project-agnostic, reusable techniques and post-mortems |

---

<a id="index"></a>
## 🧭 文档导航 · Document Index

| # | 文档 Document | 分类 Category | 一句话简介 In one line | 读者 Audience |
|:-:|---|:-:|---|:-:|
| 1 | [代码与提交规范](01_规范_Standards/代码与提交规范.md) | 01 规范 | 8 个仓库的提交格式、Git 分工、仓库卫生红线 <br> Commit formats, Git division of labor, repo hygiene | 所有仓库的所有人与 AI <br> Owner & AI, all repos |
| 2 | [yolo项目_工作流程与注意事项](02_手册_Manuals/yolo项目_工作流程与注意事项.md) | 02 手册 | 眼控轮椅 YOLO 项目：数据、训练、磁盘、已知坑 <br> Eye-wheelchair YOLO: data, training, disk, known pitfalls | 在 Yolo_model 工作的 AI <br> AI working on Yolo_model |
| 3 | [GitHub搜索_问题与解决手法](03_技法_Playbooks/GitHub搜索_问题与解决手法.md) | 03 技法 | 无 python/node 环境下用 curl+perl 调研 GitHub <br> GitHub research with curl+perl where python/node fail | 在本机做调研的 AI <br> AI doing research on this machine |

---

<a id="rules"></a>
## 📏 协作规则 · Ground Rules

> 全文见 [代码与提交规范](01_规范_Standards/代码与提交规范.md) ·
> Full text in *Code & Commit Conventions*.
> 🔴 红线 · red line　🟡 约定 · convention

- 🔴 **push 只由仓库所有者本人执行**——AI 做到 commit 为止，需要 push 先征得同意。
  **Push is executed by the owner only** — AI stops at commit and must ask first.
- 🔴 **永不入库**：密钥凭据、虚拟环境、缓存生成物、原始数据文件。
  **Never commit**: secrets, virtualenvs, caches & build output, raw data files.
- 🟡 **提交信息中英双语、中文在前**，一个逻辑单元一次提交，新提交向格式 B（段落式）靠拢。
  **Commit messages are bilingual with Chinese first**, one logical unit per commit,
  converging on Format B (paragraph style).
- 🟡 **先声明、再动手**：做什么、为什么、动哪些文件，说清楚再执行。
  **Declare before doing**: state what, why, and which files before acting.
- 🟡 **README 是项目状态的唯一权威来源**：功能、结构、结果有变，文档同步更新。
  **The README is the single source of truth**: sync docs whenever code,
  structure or results change.

---

<a id="filing"></a>
## ➕ 新增文档如何归类 · Filing New Documents

1. 约束**所有**仓库的规则 → `01_规范_Standards/`
   Rules binding **all** repositories → `01`
2. 只关于**某一个项目**、让 AI 能直接接手的完整手册 → `02_手册_Manuals/`
   A full handover manual for **one** project → `02`
3. 与项目无关、**可复用**的方法、工具链、踩坑复盘 → `03_技法_Playbooks/`
   Project-agnostic **reusable** techniques, toolchains, post-mortems → `03`

文件名沿用「主题_副题.md」的中文命名习惯；目录名保持「编号_中文_English」。
Filenames keep the Chinese `topic_subtitle.md` habit; folders keep
`NN_中文_English`.

---

<a id="ai"></a>
## 🤖 AI 接手须知 · For AI Assistants

**阅读顺序 Reading order**：本 README →
[代码与提交规范](01_规范_Standards/代码与提交规范.md) →
对应项目手册（如有） · this README → *Conventions* → the project manual, if any.

**工作循环 Work loop**：

```text
① 先声明 Declare → ② 执行 Execute → ③ 同步文档 Sync docs
        → ④ git commit（双语 bilingual） → ⑤ 停，等人类 push Stop, owner pushes
```

提交前过一遍规范文档第 04 节的五项检查清单。
Run the 5-item pre-commit checklist (§04 of the Conventions) every time.

---

<div align="center">

`aaf12329` · 知识库 v1.0 · 2026-09-29

**中文在前 · 双语同行 · push 归本人 🔴**
*Chinese first · bilingual throughout · push belongs to the owner 🔴*

</div>
