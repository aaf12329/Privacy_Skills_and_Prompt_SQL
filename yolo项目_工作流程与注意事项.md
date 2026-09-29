# AI 工作手册 / AI Operating Manual —— 眼控轮椅 YOLO 项目

> **本文档写给在本项目工作的 AI 助手**（ZCode 或后续任何 AI）。
> 目标：任何 AI 读完即可按同样的流程与规矩接手工作，不重新探索、不重复踩坑、
> 不越权。人类所有者：Guards（GitHub: aaf12329）。
> 更新：2026-09-29

---

## 0. 项目事实（不要重新探索，直接采信）

| 项 | 值 |
|---|---|
| 仓库 | `C:\Users\Guards\Desktop\yolo_model`（GitHub: aaf12329/Yolo_model，私有） |
| 服务对象 | `C:\Users\Guards\Desktop\EyeWheelchairProject`（**只读**，除非人类明确要求） |
| conda 环境 | `C:\Users\Guards\.conda\envs\yolo`（Python 3.10，PyTorch cu128，ultralytics，mediapipe）——不在 D:\Anaconda\envs |
| GPU | RTX 5060 Ti（sm_120，必须 cu128+ 构建）；**本机无摄像头** |
| 交付权重 | `models/eye_yolo26n.pt`（2 类 94.33%）、`models/gaze_yolo26s.pt`（3 类 95.62%，主控）、`models/gaze5_yolo26s.pt`（5 类 80.9%，含左右） |
| 详细文档 | 仓库 README.md（总览）、COMMANDS.md（指令）、docs/（教程/复盘/解读/采集/接入/数据源）、log.md（磁盘台账） |

## 1. 核心工作循环 ★（每个任务都必须完整走一遍）

```
① 先说明  →  ② 执行  →  ③ 同步文档  →  ④ git commit  →  ⑤ 停（等人类 push）
```

1. **先说明你要干什么**：动手前用一段话讲清目标、要改/建哪些文件、
   是否触发磁盘条款（见 §4）。禁止不打招呼就开始大动作。
2. **执行**：过程中发现新情况（报错、方案要改、要下载大文件）随时插播说明。
3. **同步文档**：按 §6 的提交前检查清单更新 README / .gitignore / COMMANDS.md /
   docs/ / log.md——代码先行、文档滞后是本项目发生过的最大返工来源。
4. **git commit**：注释**中英双语**（`中文 / English`），一个逻辑单元一次提交。
5. **停**：**push 只由人类执行**。ZCode 需要 push 时必须先征得同意；
   人类没说就永远停在 commit。

## 2. 数据查找路径（需要新数据时按此顺序找）

1. **Hugging Face API 搜索**（可编程、免费、无账号）：
   `curl "https://huggingface.co/api/datasets?search=关键词&limit=20"`
   用 downloads 字段初筛热度，`gated` 字段排查是否要授权
2. **官方实验室页**：论文里的 "available at" 链接最权威；注意链接会搬家
3. **Dataverse 归档**（如 darus.uni-stuttgart.de）：API 列文件
   `/api/datasets/:persistentId/?persistentId=doi:...`，
   下载 `/api/access/datafile/:id` —— **HEAD 会 403，必须用 GET**
4. **Wayback Machine**：老页面死链挖原始直链，再回新服务器试探
5. **Kaggle / Roboflow Universe**：需免费账号/API key，最后手段

**新数据接入 SOP**（每次都走，顺序不能乱）：
① 下载前按 §4 报备 → ② 校验（zip 完整性/条目数）→ ③ **符号与坐标约定抽样
目视验证**（文档会写错，本项目 V/H 两度反直觉）→ ④ 转成 YOLO 格式
（按受试者划分防泄漏）→ ⑤ 训练 + 配置驱动评估 → ⑥ 文档与 log.md 登记。

**已接入数据集**（直链与许可详见 `docs/dataset_sources.md` 与 `data/README.md`）：
MRL Eye（84,898 特写，睁/闭）、Columbia Gaze（5,880 全帧，5 方向）、
MPIIGaze（213k 笔记本摄像头眼部图+3D 向量，2.16GB，引用 Zhang et al. 2015）、
GazeCapture HF 镜像（19,990 手机帧+屏幕坐标，1.34GB，研究用途）。

## 3. 硬盘使用规则 ★

- **需要报备的操作**：单次写入 ≥1GB（下载/解压/训练输出）、项目目录之外的任何
  写入或移动、≥1GB 删除、conda 等环境安装。**报备 = 对话里先说明，再执行。**
- **每个大动作前后查 C 盘剩余**（C 盘是系统盘），报备时带数字，执行后复测记差额。
- **解压后 >10GB 的数据集放 `D:\yolo_datasets\<名字>\`**（连压缩包）；
  C 盘 `datasets/` 只放 10GB 以下的。D 盘根目录文件夹可自行新建。
- 所有变更**登记 `log.md`**（时间/盘/路径/大小/操作/用途/状态）。
- gitignore 白名单写法：先 `*.pt` 再 `!models/*.pt`（**后行覆盖前行，顺序不能颠倒**，
  曾因此漏提交权重）。

## 4. 训练与评估 SOP

- 训练入口统一 `scripts/train_eye.py`（`--data/--name/--model/--fliplr/--imgsz`）；
  评估统一 `scripts/eval_eye_accuracy.py`（配置驱动，读 yaml + YOLO txt 标签）
- **含左/右方向的模型必须 `--fliplr 0`**（翻转增强会污染左右标签）；
  需要翻转增强时用离线"翻转+标签互换"副本
- **推理/实测输入必须是未镜像帧**（镜像翻转左右语义）；镜像只用于显示层
- 早停 patience=10，**best.pt 取 mAP 峰值轮不是最后一轮**；每次训练都触发早停
  = 已收敛，加时长无益
- 新环境先跑 `scripts/smoke_test_yolo26.py`（样图会自动合成，clone 即用）
- 类别不均衡：center 类靠翻转副本/自采数据补；纯复制标签不复制图片是 bug

## 5. Git 与文档同步规则

- 提交前检查清单（5 项，每次 commit 前逐项过）：
  ① README 架构树/进度表反映改动了吗 ② 新文件类型/目录 → .gitignore 了吗
  ③ 新指令/脚本 → COMMANDS.md 了吗 ④ 磁盘条款触发 → log.md 了吗
  ⑤ 新结果/图表 → docs/ 归档了吗
- 交付权重放 `models/`（随 git 分发）；训练产物 `runs/`、数据 `datasets/`、
  视频 `gaze_captures/`、`phone_videos/*.mp4` 永不入库

## 6. 已知坑速查表（一行一条，动手前扫一眼）

| 坑 | 一句话对策 |
|---|---|
| 镜像帧送模型 | 左右语义反转——模型吃原始帧，镜像仅显示 |
| fliplr 开着训左右类 | 左右标签互相污染——必须 0，用离线翻转互换 |
| 符号信文档 | Columbia V/H 都反直觉过——抽样看图 |
| 同人跨训练/验证集 | 数据泄漏——按受试者划分 |
| 评估标签写字面量 | 从 yaml names/YOLO txt 读（"open"≠"open_eye" 事故） |
| 过采样只复制标签 | 图片必须连带复制 |
| Windows glob 大小写 | *.mp4/*.MP4 重复匹配——normcase 去重 |
| 眼睑参考系测竖直注视 | 睑珠联动无区分度——用眼角连线+同人排序 QC |
| RTX 50 系装默认 torch | sm_120 必须 cu128 官方源 |
| 管道吞报错（exit 0） | 后台命令少用管道收尾，或跑完验证产物存在 |
| 改了 EyeWheelchairProject | 禁区：那边保持原样，实验全部在本仓库 |

## 接手先看
先去读readme与git commit更新一下信息如果没有更新信息就先叫人来pull试一试
