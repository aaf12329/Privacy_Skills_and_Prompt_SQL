# 🏗️ My_Agent 项目代码架构标准

**Deepseek_port_new（My_Agent）项目专属规范** · v1.0 · 2026-09-30

> 本文件是 [代码与提交规范](代码与提交规范.md) 的**项目实例**：把通用模板落到
> `Desktop/Deepseek_port_new`（GitHub: aaf12329/My_Agent）这一个仓库上，
> 记录它在真实开发中固化的架构铁律、消息契约与踩坑教训。

**图例**：🔴 红线，不可违反　🟡 约定，默认遵守　🟢 建议，可灵活

---

## 01 · 分层与解耦铁律

```
入口层(壳)      main.py(控制台) / GUI.py(图形) / agent_loop.py(循环)
                  │  ← 全项目唯一有权"横向调用"的层
功能层(tool/)    tools.py      自检/三类CRUD/通用I/O/输入(Code_Send)
                  embedding.py  向量化/语义检索/领域路由
                  Model_Function.py  DeepSeek/GLM/GPT 三家适配
                  Agent_tool.py      工具适配层(声明/沙箱/审批/分发)
                  Compress_mudel.py  记忆压缩
                  Store.py      纯路径地址簿
```

- 🔴 **除 Agent_tool.py（工具适配层）外，tool/ 内模块之间零 import**——
  Agent_tool 是全项目唯一特批的横向聚合文件，其余模块要协作只能经入口层编排。
- 🔴 **所有文件位置一律从 Store 拿**（路径常量地址簿），严禁自己 `os.path.join` 拼路径。
- 🟡 Store 只被读、不调用任何人；新增产物路径（如索引文件）先登记进 Store。

## 02 · 磁盘 I/O 唯一入口

- 🔴 文本读写统一走 `tools.file_read_write`（自带编码回退 utf-8→gbk→gb2312→latin-1）；
  二进制用 `mode='read_bin'`；**不开第三个 I/O 口子**。
- 🔴 结构化数据（聊天记录 json）走 `_read_json/_write_json`，与文本口子分开。
- 🟡 坑：Windows Python 看不见 Git Bash 的 `/tmp`（路径映射不同），跨工具传临时文件用 Windows 路径。

## 03 · 模型层返回契约

三家模型（DeepSeek/GLM/GPT）适配层统一返回 dict，调用方按此解包：

```python
{"content":   str,        # 回答文本(模型要调工具时为空串)
 "reasoning": str,        # 思考过程(开 thinking 才有)
 "usage":     usage|None, # token 账单(含缓存命中数)
 "tool_calls": list}      # 工具调用请求(流式分片累积而成,无则 [])
```

- 🟡 `arguments` 从 API 拿到时是 **JSON 字符串**，不是对象——先 `json.loads`。
- 🟡 `usage.completion_tokens` **已包含** reasoning_tokens，统计成本别二次相加。

## 04 · Agent 消息契约（违反任何一条都会 400）

1. 🔴 assistant 消息必须**原样回存**（含 tool_calls 字段）——缺了模型就"忘了"自己调过工具
2. 🔴 每个 tool_call 必须紧跟一条 `{"role":"tool","tool_call_id":id,"content":文本}`
3. 🔴 并行多个 tool_calls 必须**全部执行、全部回复**
4. 🟡 `reasoning_content`：deepseek/glm 随 assistant 回传（缺失可能 400），**gpt 不传**
5. 🟡 流式 tool_calls 分片：`index` 分槽、id/name 只在首片（有值才写）、arguments 用 `+=` 累加

## 05 · 数据格式（人机一致）

- 🔴 记忆库 `memory.md`：一条记忆一行 `- [时间] 内容`，人可直接手改，程序只认行首 `- [` 的行
  （解析规则在 tools 与 embedding 两处同步维护——改格式两边一起改）
- 🔴 聊天记录 `chat_history.json`：统一 list，`[{"role","content","time"}]`
- 🟡 增删改查的序号一律 **从 1 开始**（"第 1 条"），人机一致
- 🟡 工具往返不进聊天记录——持久化只存 user 输入 + 最终回答主干

## 06 · 错误处理哲学

- 🔴 工具/子系统的异常**转成"给模型看的修正提示"文本**（带可用取值列表、正确示例），
  不是抛给人看的报错——这是 ReAct 自我修正的命脉
- 🔴 只有**暂时性错误**才重试（429/超时/5xx，指数退避+抖动）；401/400 立刻炸出来暴露问题
- 🟡 单轮失败不退程序——回到输入循环继续（`Deepseek_Core` 之外的每层都兜住）

## 07 · 安全三闸门

| 闸门 | 实现 |
|---|---|
| 路径沙箱 | realpath 解析 + `commonpath` 限定项目根 + 敏感文件黑名单（.env / id_rsa） |
| 危险审批 | 三态 `approval='ask'/'auto'/'never'`；GUI 后台线程禁 `input()`，必须传 `'auto'` 或回调 |
| 密钥管理 | 🔴 key 只进 `.env`，严禁硬编码（教训：老项目 ds.py 明文 key 差点随分享泄露） |

## 08 · 自测规范（每模块自带）

- 🟡 每个模块文件底部带 `if __name__ == "__main__":` 自测块
- 🔴 自测把 Store 路径**重定向到临时目录**，绝不碰真实数据
- 🔴 涉网络/涉 API 的自测用**假函数替换**（假模型、假压缩），零花费
- 🟡 自测可直接 monkeypatch 注册表里的函数引用——注意 `_REGISTRY["x"]["run"]` 持有引用，
  替换模块全局变量骗不过 dispatch（踩过的坑）
- 🟡 tkinter 布局验证不只看"进程活着"，用 `winfo_height/width` 量像素

## 09 · 注释与命名

- 🟡 文件头写**函数结构树**（分区导航），函数带一行 docstring，关键行内注释只写"代码看不出来的"
- 🟡 变量名**能不变就不变**（重构向后兼容）；注释用中文
- 🟡 给第三方开源项目加注时，头部标注"结构分析注释 · 非原作者所写"

## 10 · 已固化教训（踩坑存档）

| 坑 | 教训 |
|---|---|
| tkinter pack 顺序 | Canvas 先以 `LEFT+expand` 打包会吃光高度，BOTTOM 条挤成 0——**底部条最先打包** |
| 模型名退役 | `deepseek-v4-flash` 已退役，规范名 `deepseek-flash`；写教程/新代码用新名 |
| GitHub 直连慢 | Release/大文件走 `ghfast.top` 镜像（140KB/s → 3.9MB/s）；clone 走 codeload tarball |
| DeepSeek 无 embedding | 官方只有 `/user/balance`，向量必须自备（bge-small-zh 等，CPU 够用） |
| 缓存命中率 | base prompt 前缀保持字节级稳定才命中缓存；`[usage]` 行的百分比就是成绩单 |

---

<div align="center">

**v1.0 · 2026-09-30** · 随项目演进更新 · 通用底本见 [代码与提交规范](代码与提交规范.md)

</div>
