# 多 Agent 协作 —— GitHub 项目精选与刷经验路径

> **本文档可移植**：给想在多 Agent 方向"刷经验"的 AI 与人用的项目地图。
> 数据来源：2026-09-29 用 GitHub API 检索 + 仓库页逐一核实（星数/活跃度截至当日）。
> 配套手法见 [GitHub搜索_问题与解决手法](GitHub搜索_问题与解决手法.md)（怎么批量搜、怎么绕限流）。

---

## 一、刚创立但已经起飞的（2026 上半年创建，值得跟读）

| 项目 | 星数 | 创建 | 语言 | 一句话简介 |
|---|---:|---|---|---|
| [omnigent-ai/omnigent](https://github.com/omnigent-ai/omnigent) | 10.3k | 2026-06 | Python | "meta-harness"：YAML 声明 agent，统一调度 Claude Code / Codex / Cursor 等各种 runtime |
| [EverMind-AI/Raven](https://github.com/EverMind-AI/Raven) | 4.4k | 2026-05 | Python | "harness of harnesses"，自进化多 Agent 生态，pre-alpha |
| [agentlas-ai/Agentlas-OS](https://github.com/agentlas-ai/Agentlas-OS) | 1.6k | 2026-06 | Python | 专家 agent 常驻 hub，每个任务临时拉起 orchestrator |
| [LodyAI/Lody](https://github.com/LodyAI/Lody) | 1.1k | 2026-08 | TypeScript | 团队共享 coding agent（手机 + 桌面协同） |

**精读重点**：
- **omnigent**：CONTRIBUTING/DCO/harness 测试台齐全，`examples/` 里 Polly（tech-lead 并行派发
  子代理到 git worktree）、Debby（双头辩论）是 supervisor/sub-agent 范式教材；
  分层治理策略（server 级 → agent 级 → session 级）+ 云端/本地沙箱。
- **Raven**：Curator（逐轮重写 agent 的记忆/规划/能力/行动四模块）+ Evolver（基准对照自进化），
  自带多 Agent 编排 benchmark——适合研究"怎么度量 agent 团队质量"。

## 二、非常早期、几乎没人竞争的（适合动手攒贡献）

| 项目 | 星数 | 说明 |
|---|---:|---|
| [CoordClaw/CoordClaw](https://github.com/CoordClaw/CoordClaw) | 196 | 团队写进两份 markdown（teamsoul/team RULE），agent 靠消息循环开会辩论仲裁；7-agent 126 条消息 1 小时做出网页游戏；**官方邀请社区测 Linux/macOS**——现成贡献入口 |
| [CCDawn/Vibelution](https://github.com/CCDawn/Vibelution) | 83 | 本地多 Agent 平台（学术向），中文文档优先，协作机制写在 ADR |
| [agentsea/nautilo](https://github.com/agentsea/nautilo) | 71 | "AI goes multiplayer"：人类带 agent 进 Room 分工；TS monorepo，欢迎小修复 |
| [hcipengm/cogneva](https://github.com/hcipengm/cogneva) | 30 | Rust 分布式"数字员工"；想同时刷 Rust + 多 Agent 的冷门选择 |

CoordClaw 的三个设计思想值得学：**每轮重置上下文**（记忆外化到持久工作日志，防上下文污染）、
**分歧即信号**（把概率判断升级为可核对的事实再上报）、**分布式注意力**（角色窄而深，互相补盲区）。

## 三、老牌且仍在进行（适合系统刷）

| 项目 | 说明 |
|---|---|
| [camel-ai/camel](https://github.com/camel-ai/camel) | role-playing 多 Agent 框架，学术论文常客 |
| [FoundationAgents/MetaGPT](https://github.com/FoundationAgents/MetaGPT) | "软件公司"角色分工的经典参考设计 |
| [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) | 生产级编排平台，商业公司支持 |
| [microsoft/agent-framework](https://github.com/microsoft/agent-framework) | ⚠️ AutoGen 已并入此框架（Semantic Kernel + AutoGen = MAF），微软系从这里入门 |

## 四、四种协作范式（看懂差异比通读代码收获大）

1. **编排器 + 子代理**（omnigent）：一个 supervisor 拆任务派发，子代理在隔离 worktree 干活；
2. **自然语言组织契约 + 消息循环**（CoordClaw）：组织结构写在 markdown 里，靠消息协议约束行为；
3. **基准驱动自进化**（Raven）：改 agent 策略 → 基准对照 → 只保留变好的改动；
4. **人 + agent 同房间**（nautilo / Vibelution）：人类与 agent 作为平等成员在同一工作区协作。

## 五、附：搜索时刷到的相关项目

- [cobusgreyling/loop-engineering](https://github.com/cobusgreyling/loop-engineering)（★11.3k）— AI coding agent 的"循环工程"实战模式，偏方法论；
- [kirincolor/openmesh](https://github.com/kirincolor/openmesh)（★227）— 仿聊天软件的本地多 Agent 工作区；
- [Ryder-Sun/Meldwork](https://github.com/Ryder-Sun/Meldwork)（★231）— local-first 多 Agent 工作区，scoped 权限 + 证据等待；
- [Sven-Mirana/sublation](https://github.com/Sven-Mirana/sublation)（★279）— 多 Agent Skill 治理、协作面板、影子路由。

---

## 怎么刷比较高效

1. **攒贡献经验**：从第二档入手——兼容性测试、文档翻译、小 bug 修复；issue 少、维护者响应快；
2. **刷架构经验**：精读第一档的 `examples/` 与设计文档（AGENTS.md / ADR）；
3. **横向对比四种范式**（第四节），比通读任何一个框架的代码收获都大；
4. 星数与活跃度会过时——动手前用 [GitHub搜索_问题与解决手法](GitHub搜索_问题与解决手法.md)
   的工作流重新核实一遍（API 或 HTML 页均可）。
