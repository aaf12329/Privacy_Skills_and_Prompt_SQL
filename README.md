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

**唯一例外**：`00_用户信息_Private/`——创作者私人方向（个人画像与学习笔记），
画像文件顶部带【请过滤本文件】标记；分享本库、批量处理时应跳过它，正式使用前
先删除标记行。目录性质见该目录内 README 的声明。

*Bilingual repo; the only non-generic area is `00_用户信息_Private` (the owner's
private profile, marked 【请过滤本文件】). Full English prose lives in the section
headings and rules below.*

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
├── 00_用户信息_Private/             🔴 创作者私人方向（非通用）
│   ├── README.md                    私人区声明与红线
│   ├── 用户画像_协作偏好.md          个人协作画像（带过滤标记）
│   └── 个人笔记 ×2                  前端整合笔记（三合一）· conda 备忘
├── 01_规范_Standards/               约束所有仓库
│   ├── 代码与提交规范.md             提交 / 仓库 / 删除规则
│   └── 代码架构规范.md               分层解耦 / 地址簿 / 契约 / 自测 / 安全闸门
├── 02_手册_Manuals/                 手册模板
│   └── 项目接手手册_模板与写法.md
└── 03_技法_Playbooks/               跨项目复用方法
    ├── GitHub搜索_问题与解决手法.md
    ├── 学术检索_问题与获取路径.md
    └── 多Agent协作_项目精选.md
```

| 目录 | 放什么 |
|---|---|
| `00_用户信息_Private` | 🔴 创作者私人方向：所有者的画像、个人信息与个人学习笔记（非通用，勿当模板抄）<br>*owner-private area* |
| `01_规范_Standards` | 跨仓库规则、格式与红线（替换占位符后全项目生效）<br>*cross-repo rules & red lines* |
| `02_手册_Manuals` | 接手手册**模板与写法**（新项目复制填空）<br>*handover-manual template* |
| `03_技法_Playbooks` | 与项目无关、可反复使用的方法与踩坑复盘<br>*reusable techniques & post-mortems* |

---

<a id="index"></a>
## 🧭 文档导航 · Document Index

| # | 文档 | 分类 | 一句话简介 | 读者 |
|:-:|---|:-:|---|---|
| 1 | [代码与提交规范](01_规范_Standards/代码与提交规范.md) | 01 | 提交信息格式、Git 分工、仓库卫生红线、删除与回收站（占位符模板） | 所有仓库的所有人与 AI |
| 2 | [代码架构规范](01_规范_Standards/代码架构规范.md) | 01 | 分层解耦铁律、路径地址簿、重复消除规程、返回契约、安全三闸门、自测规范；末节为 LLM/Agent 类项目追加契约 | 写代码的所有人与 AI |
| 3 | [项目接手手册_模板与写法](02_手册_Manuals/项目接手手册_模板与写法.md) | 02 | 怎么写"AI 一读即接手"的项目手册 + 通用坑 + 数据查找路径 | 写/接手项目手册的人类与 AI |
| 4 | [GitHub搜索_问题与解决手法](03_技法_Playbooks/GitHub搜索_问题与解决手法.md) | 03 | 无 python/node 环境下 curl+perl 调研 GitHub；限流与降级 | 在 Windows/Git Bash 调研的 AI |
| 5 | [学术检索_问题与获取路径](03_技法_Playbooks/学术检索_问题与获取路径.md) | 03 | 学术文献检索全流程：Crossref 核实题录、限流降级、机构库挖全文、付费墙合法获取路径 | 需要找论文/拿全文的 AI 与人 |
| 6 | [多Agent协作_项目精选](03_技法_Playbooks/多Agent协作_项目精选.md) | 03 | 多 Agent 方向项目地图：四档精选 + 四种协作范式 + 刷经验路径 | 想入坑多 Agent 的 AI 与人 |
| 7 | [用户画像_协作偏好](00_用户信息_Private/用户画像_协作偏好.md) ⚠️ | 00 | 个人协作画像；**私人方向文件，顶部带过滤标记，非通用** | 与此人协作的 AI |

---

<a id="rules"></a>
## 📏 协作规则 · Ground Rules

> 全文见 [代码与提交规范](01_规范_Standards/代码与提交规范.md)。
> 🔴 红线　🟡 约定

- 🔴 **push 只由仓库所有者本人执行**——AI 做到 commit 为止，需要 push 先征得同意。
  *Owner-only push; AI stops at commit.*
- 🔴 **永不入库**：密钥凭据、虚拟环境、缓存生成物、原始数据文件。
  *Never commit: secrets, venvs, caches/build output, raw data.*
- 🔴 **删除必报备、永不清空回收站**：删项目文件夹之外的任何东西先报备；
  删除一律送回收站，**绝不清空回收站**，项目文件夹之外禁止直接 `rm`。
  *Deleting anything outside a project folder requires reporting first; always
  send deletions to the Recycle Bin — never empty it, never bare `rm` outside
  project folders.*
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

1. 所有者的**私人信息与画像** → `00_用户信息_Private/`（私人方向，非通用）
2. 约束**所有**仓库的规则 → `01_规范_Standards/`
3. 给**某个项目**写的接手手册（由 02 模板填空而成）→ `02_手册_Manuals/`
4. 与项目无关、**可复用**的方法/工具链/复盘 → `03_技法_Playbooks/`

文件名沿用「主题_副题.md」；目录名保持「编号_中文_English」。
*Filenames: `topic_subtitle.md`; folders: `NN_中文_English`.*

---

<a id="ai"></a>
## 🤖 AI 接手须知 · For AI Assistants

**分层参考 · Layered Reference**：先看地图知道"什么放在哪"，做具体事时再按路由去读
对应部分——**不要一开始就通读全库**（省 token，也防规则被稀释）。

**① 全库地图（什么放在哪里）**

| 位置 | 内容 | 性质 |
|---|---|---|
| 本 README | 门面 + 规则摘要 + 本分层参考 | 每次必读 |
| [01 提交规范](01_规范_Standards/代码与提交规范.md) | Git 分工 / 提交信息格式 / 提交前检查清单 / 仓库卫生 / 删除红线 | 每次必读（§02 §04 §07 §10） |
| [01 架构规范](01_规范_Standards/代码架构规范.md) | 分层解耦 / 地址簿 / 重复消除 / 契约 / 自测 / 安全闸门 | 按需（写代码、定结构时） |
| [02 模板](02_手册_Manuals/项目接手手册_模板与写法.md) | 新项目接手手册的模板与写法 | 按需（接手/新建项目时） |
| [00 画像](00_用户信息_Private/用户画像_协作偏好.md) ⚠️ | 个人协作偏好（私人方向，带过滤标记，非通用） | 按需（需了解所有者偏好时） |
| [03 技法](03_技法_Playbooks/GitHub搜索_问题与解决手法.md) | Windows/Git Bash 下 GitHub 调研手法与限流应对；另有学术检索、多 Agent 项目精选 | 按需（做 GitHub/学术调研、入坑多 Agent 时） |

**② 任务路由（做什么 → 读哪里）**

| 我要做的事 | 去读 |
|---|---|
| 开始任何仓库的工作 | 本 README + 01 §02（Git 分工）· §07（红线） |
| 写 commit | 01 §03（信息格式）· §04（提交前检查清单） |
| 大动作：下载 / 删除 / 装环境 / 跨盘 | 01 §07 磁盘报备制度 · §10（删除必报备 + 送回收站） |
| 判断文件能否入库 | 01 §07 仓库卫生（永不入库 / 选择性入库） |
| 写新代码 / 定结构 / 发现重复 | 01 架构规范（分层、地址簿、重复消除规程） |
| LLM / Agent 类的接口与消息契约 | 01 架构规范 §10 |
| 接手或交付一个项目 | 02 模板（复制 §2 骨架填空） |
| 需要了解所有者偏好与沟通方式 | 00 画像（⚠️ 先删标记行再用） |
| 在 Windows/Git Bash 做 GitHub 调研 | 03 技法 |
| 任何规则拿不准 | 回到 01 规范全文 |

**工作循环**：

```text
① 先声明 Declare → ② 执行 Execute → ③ 同步文档 Sync docs
        → ④ git commit（双语 bilingual） → ⑤ 停，等所有者 push Stop, owner pushes
```

提交前过一遍规范的**五项检查清单**（§04）。*Run the §04 checklist every commit.*

**⚠️ 过滤标记**：本库唯一非通用区是 `00_用户信息_Private/`（创作者私人方向）——
分享本库、批量处理、生成公开内容时**跳过该目录**；确需用其中的画像了解所有者
偏好时，**先删除标记行再使用**。*Skip the private area when sharing; delete the
marker line in the profile before use.*

**提交红线补充**：提交信息与提交的文件内容中**过滤所有者身份信息**
（真实姓名、学校/单位、地理位置、健康状况），除非所有者明确要求写入。
*Filter identity info from commits and committed content unless asked otherwise.*

---

<div align="center">

`Privacy_Skills_and_Prompt_SQL` · v2.5 · 2026-10-05

**中文在前 · push 归所有者 🔴**

</div>
