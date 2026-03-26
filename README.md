# Photo Pose Director Skills

一个专门用于“摄影参考图分析与复刻执行”的技能仓库，支持两类使用场景：

- 真人拍摄复刻
- AI 生图复刻

它不是泛泛的图片分析工具，而是把一张参考图拆成真正可执行的复刻方案，包括：

- 复刻关键锚点
- 相机复刻方案
- 拍摄手法分析
- 摄影师一句话动作指导
- 摄影师现场口播版
- 动作拆解
- 真人拍摄注意事项
- AI 复刻注意事项
- 人物一致性锁定
- 精简中文提示词

## 仓库内容

本仓库同时包含两个版本：

- `Codex` 版技能
- `OpenClaw` 版技能
- `ChatGPT` 安装包
- `Gemini` 安装包

以及完整的设计文档和实现规划，方便继续迭代。

## 特点

- 默认中文输出
- 默认完整分析版
- 默认提示词为精简中文单行
- 默认比例为 `3:4`
- 优先保留原图人物的一致性
- 相机复刻建议优先贴近原图风格，而不是只给通用保险参数
- 支持机位、焦段、曝光、布光和后期调色建议

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
├─ platform-packs/
│  ├─ chatgpt/
│  └─ gemini/
├─ .gitignore
├─ LICENSE
└─ README.md
```

## 安装

### Codex

把这个目录复制到你的 Codex 技能目录：

`skills/codex/photo-pose-director`

通常目标位置是：

`~/.codex/skills/photo-pose-director`

### OpenClaw

把这个目录复制到 OpenClaw 技能目录：

`skills/openclaw/photo_pose_director`

可放在下面任一位置：

- 工作区：`<workspace>/skills/photo_pose_director`
- 全局：`~/.openclaw/skills/photo_pose_director`

### ChatGPT

使用：

- `platform-packs/chatgpt/custom-gpt/` 创建自定义 GPT
- `platform-packs/chatgpt/instructions/` 配置 Custom Instructions

### Gemini

使用：

- `platform-packs/gemini/gem/` 创建 Gemini Gem
- `platform-packs/gemini/instructions/` 做长期系统指令使用

## 推荐用法

### Codex 调用示例

```text
Use $photo-pose-director to analyze this reference image in Chinese, identify the replication anchors, give camera position and settings, direct the model on set, suggest color grading, keep the subject consistent, and generate short recreation and upgrade prompts.
```

### OpenClaw 调用示例

```text
分析这张参考图，告诉我复刻关键锚点、相机拍摄方案、动作指导、后期调色方向和 AI 复刻提示词。
```

### ChatGPT / Gemini 推荐请求方式

```text
分析这张参考图，重点告诉我怎么复刻：先给复刻关键锚点，再给相机机位、焦段、参数、布光、后期、动作指导和 AI 复刻提示词。
```

## 示例图用法

### 示例 1：真人拍摄复刻

适合这种请求：

```text
分析这张参考图，重点告诉我怎么拿相机复刻，给我机位、焦段、参数、布光、后期和现场指导口令。
```

你会得到：

- 这张图最不能丢的 3 到 6 个复刻关键锚点
- 推荐机位和镜头距离
- 推荐焦段与拍摄参数
- 布光与光线复刻方式
- 后期调色方向
- 摄影师一句话动作指导
- 摄影师现场口播版

### 示例 2：AI 生图复刻

适合这种请求：

```text
分析这张图并给我忠实复刻版和优化升级版提示词，保持人物年龄、种族、发型和身材接近原图。
```

你会得到：

- 人物一致性锁定
- AI 复刻注意事项
- 忠实复刻版中文单行提示词
- 优化升级版中文单行提示词

### 示例 3：边拍边指导模特

适合这种请求：

```text
把这张参考图拆成摄影师在现场能直接说的话，我要照着指导模特。
```

你会得到：

- 专业版一句话动作指导
- 通俗版一句话动作指导
- 4 到 6 句现场口播版
- 动作拆解

## 示例目录

仓库里已经提供第一批真人拍摄复刻示例，见：

- [真人拍摄复刻示例目录](examples/real-shoot-recreation/README.md)
- [室内柔光私房](examples/real-shoot-recreation/indoor-soft-private-portrait.md)
- [窗边自然光人像](examples/real-shoot-recreation/window-light-portrait.md)
- [户外街拍氛围人像](examples/real-shoot-recreation/outdoor-street-portrait.md)
- [情绪化坐姿半躺构图](examples/real-shoot-recreation/moody-seated-recline.md)

## 默认输出逻辑

当前技能默认按这个顺序输出：

1. 复刻关键锚点
2. 相机复刻方案
3. 拍摄手法分析
4. 摄影师一句话动作指导
5. 摄影师现场口播版
6. 动作拆解
7. 真人拍摄注意事项
8. AI 复刻注意事项
9. 人物一致性锁定
10. 忠实复刻版提示词
11. 优化升级版提示词

## 设计文档

完整设计与演进过程保留在：

- [初版设计](docs/superpowers/specs/2026-03-26-photo-pose-director-design.md)
- [复刻优先升级设计](docs/superpowers/specs/2026-03-26-photo-pose-director-replication-first-upgrade-design.md)
- [实现计划](docs/superpowers/plans/2026-03-26-photo-pose-director.md)

## 适合谁用

这个技能特别适合：

- 摄影师
- 人像爱好者
- 私房 / 写真人像创作者
- 用参考图做动作拆解的人
- 想把真人拍摄逻辑迁移到 AI 生图的人

## 许可证

本项目采用 [MIT License](LICENSE)。
