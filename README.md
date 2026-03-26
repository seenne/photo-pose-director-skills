# Photo Pose Director Skills

一个面向“摄影图片分析与复刻执行”的技能仓库，包含：

- Codex 版技能
- OpenClaw 版技能
- 设计文档与实现规划

这个项目的目标不是泛泛做图像分析，而是围绕下面两类真实工作流：

1. 看图分析并复刻真人拍摄
2. 看图分析并复刻 AI 生图

技能会优先输出：

- 复刻关键锚点
- 相机复刻方案
- 拍摄手法分析
- 摄影师动作指导
- 现场口播版指令
- 动作拆解
- 真人拍摄注意事项
- AI 复刻注意事项
- 人物一致性锁定
- 精简中文提示词

## 仓库结构

```text
.
├─ docs/
│  └─ superpowers/
│     ├─ plans/
│     └─ specs/
├─ skills/
│  ├─ codex/
│  │  └─ photo-pose-director/
│  │     ├─ SKILL.md
│  │     └─ agents/
│  │        └─ openai.yaml
│  └─ openclaw/
│     └─ photo_pose_director/
│        └─ SKILL.md
└─ README.md
```

## 功能定位

这个技能专门用于处理参考摄影图，帮助你：

- 判断一张图“像不像”的关键锚点
- 给出尽量贴近原图风格的相机机位、焦段、参数和布光方案
- 生成摄影师现场可以直接说的动作指导
- 输出适合 AI 复刻的精简中文提示词
- 尽量锁定人物的种族、年龄感、脸型气质、发型、身材和服装类型

## 安装

### Codex

把下面这个目录放到你的 Codex 技能目录中：

`skills/codex/photo-pose-director`

通常目标位置是：

`~/.codex/skills/photo-pose-director`

### OpenClaw

把下面这个目录放到 OpenClaw 的技能目录中：

`skills/openclaw/photo_pose_director`

你可以放在两种位置之一：

- 工作区：`<workspace>/skills/photo_pose_director`
- 全局：`~/.openclaw/skills/photo_pose_director`

OpenClaw 会按技能目录扫描并加载 `SKILL.md`。

## 推荐用法

### Codex

```text
Use $photo-pose-director to analyze this reference image in Chinese, identify the replication anchors, give camera position and settings, direct the model on set, suggest color grading, keep the subject consistent, and generate short recreation and upgrade prompts.
```

### OpenClaw

把技能装好后，直接提出类似请求：

```text
分析这张参考图，告诉我复刻关键锚点、相机拍摄方案、动作指导和 AI 复刻提示词。
```

## 设计文档

设计和迭代过程保留在：

- [初版设计](docs/superpowers/specs/2026-03-26-photo-pose-director-design.md)
- [复刻优先升级设计](docs/superpowers/specs/2026-03-26-photo-pose-director-replication-first-upgrade-design.md)
- [实现计划](docs/superpowers/plans/2026-03-26-photo-pose-director.md)

## 当前默认规则

- 默认中文输出
- 默认完整分析版
- 默认提示词为精简中文单行
- 默认比例为 `3:4`
- 复刻优先于美化
- 相机拍摄建议优先贴近原图风格，而不是只给保险参数

## 说明

仓库中的 `skills/photo_pose_director.zip` 属于打包产物，不作为源码维护对象。
