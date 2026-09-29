<div align="center">

# 🗂️ Privacy_Skills_and_Prompt_SQL

**AI 协作知识库 · AI Collaboration Knowledge Base**

[![Docs](https://img.shields.io/badge/docs-3-2E86AB?style=flat-square)](#index)
[![Language](https://img.shields.io/badge/language-中文_·_EN-C73E1D?style=flat-square)](#about)
[![Commit](https://img.shields.io/badge/commit-双语_Bilingual-4CAF50?style=flat-square)](#rules)
[![Push](https://img.shields.io/badge/push-仅限所有者_owner_only-D32F2F?style=flat-square)](#rules)

*给人类看的门面，给 AI 看的规矩。*
*A front door for humans, ground rules for AI.*

</div>

---

<a id="about"></a>
## 📌 关于本仓库 · About

**中文**
本仓库沉淀 AI 协作过程中产生的三类知识：约束所有仓库的**规范**、可复制填空的
**接手手册模板**、可跨项目复用的**技法复盘**。全部内容已通用化——不含任何个人
信息与私有项目细节，任何人（或 AI）克隆后即可直接当作自己 Agent 的参考手册。

**唯一例外**：`02_手册_Manuals/用户画像_协作偏好.md`——个人协作偏好画像，
**顶部带【请过滤本文件】标记**。分享本库、批量处理、生成公开内容时应跳过该文件；
正式使用该画像前，先删除其标记行。详见下方「协作规则」与「AI 接手须知」。

**English**
This repository curates three kinds of knowledge produced while working with AI
assistants: **standards** that bind every repository, a fill-in-the-blank
**handover-manual template**, and reusable **playbooks**. Everything here is
fully generic — no personal info, no private project details — so anyone (human
or AI) can clone it and hand it straight to their own agent as a reference.

**One exception**: `02_手册_Manuals/用户画像_协作偏好.md` — a personal
collaboration profile carrying a **“filter this file out” marker** at the top.
Skip it when sharing this library, bulk-processing, or generating public content;
delete the marker line before actually using the profile. See *Ground Rules* and
*For AI Assistants* below.

---

<a id="quickstart"></a>
## 🚀 快速上手 · Quick Start

**中文**
1. `git clone` 本仓库到任意位置（工作区内、桌面均可）；
2. 在你的 coding agent（Claude Code / ZCode / Cursor / Copilot…）的指令文件
   （`AGENTS.md` / `CLAUDE.md` / 系统提示）里加一句：
   **"开始任何仓库的工作前，先读 Privacy_Skills_and_Prompt_SQL 的 README"**；
3. 把 [01 规范](01_规范_Standards/代码与提交规范.md) 里的 `<占位符>` 替换成
   你自己的署名/仓库清单，规范即对你生效；
4. 新项目要交给 AI？复制 [02 接手手册](02_手册_Manuals/项目接手手册_模板与写法.md)
   的 §2 骨架填空，实例抄 §3、§4。

**English**
1. `git clone` this repo anywhere inside your workspace;
2. Add one line to your coding agent's instruction file (`AGENTS.md`,
   `CLAUDE.md`, system prompt): **"Before working on any repo, read the
   README of Privacy_Skills_and_Prompt_SQL"**;
3. Replace the `<placeholders>` in [01 Standards](01_规范_Standards/代码与提交规范.md)
   with your own identity and repo inventory — the rules now bind you;
4. Handing a new project to an AI? Copy the §2 skeleton from
   [02 Handover Manual](02_手册_Manuals/项目接手手册_模板与写法.md),
   then lift examples from §3 and §4.

---

<a id="layout"></a>
## 🗺️ 目录结构 · Layout

```text
Privacy_Skills_and_Prompt_SQL/
├── README.md                        ← 你在这里 · You are here
├── 01_规范_Standards/               约束所有仓库 · binds all repos
│   └── 代码与提交规范.md
├── 02_手册_Manuals/                 项目接手手册模板 · handover-manual template
│   ├── 项目接手手册_模板与写法.md
│   └── 用户画像_协作偏好.md          ⚠️ 非通用文件（带过滤标记）
└── 03_技法_Playbooks/               跨项目复用方法 · reusable techniques
    └── GitHub搜索_问题与解决手法.md
```

| 目录 Folder | 放什么 · What belongs here |
|---|---|
| `01_规范_Standards` | 跨仓库的规则、格式与红线，替换占位符后对所有项目生效 · Cross-repo rules, formats and red lines; effective after replacing placeholders |
| `02_手册_Manuals` | 项目接手手册的**模板与写法**（新项目复制填空） · The **template & guide** for per-project handover manuals (copy & fill for new projects) |
| `03_技法_Playbooks` | 与具体项目无关、可反复使用的方法与踩坑复盘 · Project-agnostic, reusable techniques and post-mortems |

---

<a id="index"></a>
## 🧭 文档导航 · Document Index

| # | 文档 Document | 分类 Category | 一句话简介 In one line | 读者 Audience |
|:-:|---|:-:|---|:-:|
| 1 | [代码与提交规范](01_规范_Standards/代码与提交规范.md) | 01 规范 | 提交信息四种格式、Git 分工两方案、仓库卫生红线（占位符模板） <br> Four commit formats, two Git division schemes, repo hygiene red lines (placeholder template) | 所有仓库的所有人与 AI <br> Owner & AI, all repos |
| 2 | [项目接手手册_模板与写法](02_手册_Manuals/项目接手手册_模板与写法.md) | 02 手册 | 怎么写"AI 一读即接手"的项目手册 + 12 条通用坑 + 数据查找路径 <br> How to write a manual an AI can take over from + 12 universal pitfalls + data-source paths | 要写或接手项目手册的人类与 AI <br> Humans & AI writing or inheriting a project manual |
| 3 | [GitHub搜索_问题与解决手法](03_技法_Playbooks/GitHub搜索_问题与解决手法.md) | 03 技法 | 无 python/node 环境下用 curl+perl 调研 GitHub；API 限流与降级 <br> GitHub research with curl+perl where python/node fail; rate limits & fallbacks | 在 Windows/Git Bash 做调研的 AI <br> AI researching on Windows/Git Bash |
| 4 | [用户画像_协作偏好](02_手册_Manuals/用户画像_协作偏好.md) ⚠️ | 02 手册 | 个人协作画像：技术背景、沟通偏好、回应指引；**顶部带过滤标记，非通用文件** <br> Personal collaboration profile; **filter marker on top, non-generic** | 与此人协作的 AI <br> AI collaborating with the owner |

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
- 🟡 **提交中过滤身份信息**：真实姓名、学校/单位、地理位置、健康状况等，
  **提交信息与提交的文件内容都算**——除非所有者明确要求写入。
  **Filter identity info out of commits** (messages *and* file contents):
  real name, school/employer, location, health status — unless the owner asks otherwise.
- 🟡 **过滤标记约定**：带【请过滤本文件】标记的文件（见 02 用户画像）不属于通用内容——
  分享、批量处理时应跳过；**正式使用时先删除标记行**。
  **Filter-marker convention**: files marked 【请过滤本文件】 are not generic content —
  skip them when sharing or bulk-processing; **delete the marker line before real use**.
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
2. 给**某个项目**写的接手手册（复制 02 模板填空而成）→ `02_手册_Manuals/`
   A handover manual for **one** project (filled from the 02 template) → `02`
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
        → ④ git commit（双语 bilingual） → ⑤ 停，等所有者 push Stop, owner pushes
```

提交前过一遍规范文档第 04 节的五项检查清单。
Run the 5-item pre-commit checklist (§04 of the Conventions) every time.

**⚠️ 过滤标记 · Filter marker**：本库唯一非通用文件是
`02_手册_Manuals/用户画像_协作偏好.md`，顶部带 **【请过滤本文件】** 标记——
分享本库、批量处理、生成公开内容时**跳过该文件**；确需用它来了解所有者偏好时，
**先删除标记行再使用**。
The only non-generic file here is `02_手册_Manuals/用户画像_协作偏好.md`, marked
**【请过滤本文件】** at the top — **skip it** when sharing the library,
bulk-processing, or producing public content; when you actually need it to
understand the owner's preferences, **delete the marker line first**.

**提交红线补充 · Commit red line**：提交信息与提交的文件内容中**过滤所有者身份信息**
（真实姓名、学校/单位、地理位置、健康状况），除非所有者明确要求写入。
Also **filter identity info** (real name, school/employer, location, health)
out of commit messages *and* committed file contents, unless the owner asks otherwise.

---

<div align="center">

`Privacy_Skills_and_Prompt_SQL` · 知识库 v2.0 · 2026-09-29

**中文在前 · 双语同行 · push 归所有者 🔴**
*Chinese first · bilingual throughout · push belongs to the owner 🔴*

</div>
