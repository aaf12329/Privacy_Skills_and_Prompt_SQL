<div align="center">

# 🗂️ Privacy_Skills_and_Prompt_SQL

**AI 协作知识库 · AI Collaboration Knowledge Base**

[![Commit](https://img.shields.io/badge/commit-双语_Bilingual-4CAF50?style=flat-square)](#rules)
[![Push](https://img.shields.io/badge/push-仅限所有者_owner_only-D32F2F?style=flat-square)](#rules)
[![Filter](https://img.shields.io/badge/画像文件-带过滤标记-orange?style=flat-square)](#ai)

*给人类看的门面，给 AI 看的规矩。*

</div>

---

<a id="about"></a>
## 📌 关于本仓库 · About

本仓库沉淀 AI 协作中产生的三类知识：约束所有仓库的**规范**、可复制填空的
**接手手册模板**、可跨项目复用的**技法复盘**。内容已通用化——不含个人信息与
私有项目细节，任何人（或 AI）克隆后即可直接当作自己 Agent 的参考手册。

**唯一例外**：`02_手册_Manuals/用户画像_协作偏好.md`——个人协作偏好画像，
顶部带【请过滤本文件】标记；分享本库、批量处理时应跳过它，正式使用前先删除标记行。

*Bilingual repo; the only non-generic file is the personal profile in `02`, marked
【请过滤本文件】. Full English prose lives in the section headings and rules below.*

---

<a id="quickstart"></a>
## 🚀 快速上手 · Quick Start

1. `git clone` 本仓库到任意位置；
2. 在你的 coding agent（Claude Code / ZCode / Cursor / Copilot…）的指令文件
   （`AGENTS.md` / `CLAUDE.md` / 系统提示）里加一句：
   **"开始任何仓库的工作前，先读 Privacy_Skills_and_Prompt_SQL 的 README"**；
3. 把 [01 规范](01_规范_Standards/代码与提交规范.md) 里的 `<占位符>` 替换成
   你自己的署名/仓库清单，规范即对你生效；
4. 新项目要交给 AI？复制 [02 接手手册](02_手册_Manuals/项目接手手册_模板与写法.md)
   的 §2 骨架填空，实例抄 §3、§4。

*Clone → point your agent's instruction file at this README → fill the
`<placeholders>` in 01 → copy the 02 skeleton for new projects.*

---

<a id="layout"></a>
## 🗺️ 目录结构 · Layout

```text
Privacy_Skills_and_Prompt_SQL/
├── README.md                        ← 你在这里
├── 01_规范_Standards/               约束所有仓库
│   └── 代码与提交规范.md
├── 02_手册_Manuals/                 手册模板与个人画像
│   ├── 项目接手手册_模板与写法.md
│   └── 用户画像_协作偏好.md          ⚠️ 非通用文件（带过滤标记）
└── 03_技法_Playbooks/               跨项目复用方法
    └── GitHub搜索_问题与解决手法.md
```

| 目录 | 放什么 |
|---|---|
| `01_规范_Standards` | 跨仓库规则、格式与红线（替换占位符后全项目生效）<br>*cross-repo rules & red lines* |
| `02_手册_Manuals` | 接手手册**模板与写法**（新项目复制填空）<br>*handover-manual template* |
| `03_技法_Playbooks` | 与项目无关、可反复使用的方法与踩坑复盘<br>*reusable techniques & post-mortems* |

---

<a id="index"></a>
## 🧭 文档导航 · Document Index

| # | 文档 | 分类 | 一句话简介 | 读者 |
|:-:|---|:-:|---|---|
| 1 | [代码与提交规范](01_规范_Standards/代码与提交规范.md) | 01 | 提交信息格式、Git 分工、仓库卫生红线（占位符模板） | 所有仓库的所有人与 AI |
| 2 | [项目接手手册_模板与写法](02_手册_Manuals/项目接手手册_模板与写法.md) | 02 | 怎么写"AI 一读即接手"的项目手册 + 通用坑 + 数据查找路径 | 写/接手项目手册的人类与 AI |
| 3 | [GitHub搜索_问题与解决手法](03_技法_Playbooks/GitHub搜索_问题与解决手法.md) | 03 | 无 python/node 环境下 curl+perl 调研 GitHub；限流与降级 | 在 Windows/Git Bash 调研的 AI |
| 4 | [用户画像_协作偏好](02_手册_Manuals/用户画像_协作偏好.md) ⚠️ | 02 | 个人协作画像；**顶部带过滤标记，非通用文件** | 与此人协作的 AI |

---

<a id="rules"></a>
## 📏 协作规则 · Ground Rules

> 全文见 [代码与提交规范](01_规范_Standards/代码与提交规范.md)。
> 🔴 红线　🟡 约定

- 🔴 **push 只由仓库所有者本人执行**——AI 做到 commit 为止，需要 push 先征得同意。
  *Owner-only push; AI stops at commit.*
- 🔴 **永不入库**：密钥凭据、虚拟环境、缓存生成物、原始数据文件。
  *Never commit: secrets, venvs, caches/build output, raw data.*
- 🔴 **提交中过滤身份信息**：真实姓名、学校/单位、地理位置、健康状况等——
  提交信息与提交的文件内容都算；除非所有者明确要求写入。
  *Filter identity info (name/school/location/health) from commit messages and
  committed content, unless the owner asks otherwise.*
- 🟡 **过滤标记约定**：带【请过滤本文件】标记的文件不属于通用内容——分享、批量
  处理时跳过；**正式使用时先删除标记行**。
  *Files marked 【请过滤本文件】 are non-generic: skip when sharing, delete the
  marker line before real use.*
- 🟡 **提交信息中英双语、中文在前**，一个逻辑单元一次提交，向格式 B（段落式）靠拢。
  *Bilingual commits (Chinese first), one logical unit each, converging on Format B.*
- 🟡 **先声明、再动手**：做什么、为什么、动哪些文件，说清楚再执行。
  *Declare before doing: what, why, which files.*
- 🟡 **README 是项目状态的唯一权威来源**：功能、结构、结果有变，文档同步更新。
  *README is the single source of truth; sync docs on every change.*

---

<a id="filing"></a>
## ➕ 新增文档如何归类 · Filing

1. 约束**所有**仓库的规则 → `01_规范_Standards/`
2. 给**某个项目**写的接手手册（由 02 模板填空而成）→ `02_手册_Manuals/`
3. 与项目无关、**可复用**的方法/工具链/复盘 → `03_技法_Playbooks/`

文件名沿用「主题_副题.md」；目录名保持「编号_中文_English」。
*Filenames: `topic_subtitle.md`; folders: `NN_中文_English`.*

---

<a id="ai"></a>
## 🤖 AI 接手须知 · For AI Assistants

**阅读分层**（省 token，也防规则被稀释）：

| 层级 | 内容 | 何时读 |
|---|---|---|
| 每次必读 | 本 README + [01 规范](01_规范_Standards/代码与提交规范.md) 的红线部分 | 开始任何仓库工作前 |
| 按需查阅 | `03_技法` 的复盘与脚本、`02` 模板的示例章节 | 遇到对应问题时 |

**工作循环**：

```text
① 先声明 Declare → ② 执行 Execute → ③ 同步文档 Sync docs
        → ④ git commit（双语 bilingual） → ⑤ 停，等所有者 push Stop, owner pushes
```

提交前过一遍规范的**五项检查清单**（§04）。*Run the §04 checklist every commit.*

**⚠️ 过滤标记**：本库唯一非通用文件是 `02_手册_Manuals/用户画像_协作偏好.md`——
分享本库、批量处理、生成公开内容时**跳过该文件**；确需用它了解所有者偏好时，
**先删除标记行再使用**。*Skip the marked profile when sharing; delete its marker
line before use.*

**提交红线补充**：提交信息与提交的文件内容中**过滤所有者身份信息**
（真实姓名、学校/单位、地理位置、健康状况），除非所有者明确要求写入。
*Filter identity info from commits and committed content unless asked otherwise.*

---

<div align="center">

`Privacy_Skills_and_Prompt_SQL` · v2.1 · 2026-09-29

**中文在前 · push 归所有者 🔴**

</div>
