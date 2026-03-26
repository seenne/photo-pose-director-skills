---
name: photo-pose-director
description: Use when a user shares a reference photography image and wants to analyze it in Chinese, recreate the same pose or shooting feel, direct a real model on set, or generate AI prompts that stay close to the original person, mood, and composition.
---

# Photo Pose Director

## Overview

Treat the image as a replication target first and an analysis object second. The job is to explain why the photo works, identify what cannot be lost, guide a real model in photographer-style Chinese, and output short Chinese prompts that can recreate the same person, pose, light, and atmosphere.

## Quick Start

1. Decide the job: 真人复刻、AI复刻、双重复刻、优化升级.
2. Rank the image by replication priority: 动作、机位、光感、情绪、人物感.
3. Extract 3 to 6 复刻关键锚点.
4. Build the camera recreation plan.
5. Explain why the image works.
6. Output the full response in this order:
   - 复刻关键锚点
   - 相机复刻方案
   - 拍摄手法分析
   - 摄影师一句话动作指导
   - 摄影师现场口播版
   - 动作拆解
   - 真人拍摄注意事项
   - AI复刻注意事项
   - 人物一致性锁定
   - 忠实复刻版提示词
   - 优化升级版提示词

## Internal Workflow

### 1. Read the goal before reading the style

- Use the image as the main source of truth.
- Use user text only as a modifier: platform, mood, level of optimization, or scene change.
- When the user asks for recreation, preserve resemblance before beautification.
- When the user asks for optimization, keep the original identity and pose logic unless they explicitly ask for a larger change.

Internal principle:

`复刻时先求像，优化时再求更美。`

### 2. Run the replication-priority classifier

Before normal analysis, decide what defines the image most strongly.

Priority classes:

- 动作主导型
- 机位主导型
- 光感主导型
- 情绪主导型
- 人物感主导型

Determine:

- 第一优先
- 第二优先
- 辅助因素

Use that ranking to decide what to emphasize later.

Examples:

- 动作主导型: expand pose breakdown and body mechanics
- 机位主导型: emphasize camera angle and replication anchors
- 光感主导型: emphasize lighting logic and prompt lighting words
- 情绪主导型: emphasize gaze, expression, and distance/intimacy
- 人物感主导型: emphasize subject consistency locking

### 3. Extract replication anchors first

Always output 3 to 6 `复刻关键锚点` before the normal explanation.

A good anchor follows this rule:

`缺了它，这张图就不像了。`

Common anchor types:

- 机位高低
- 视线方向
- 身体朝向
- 腿部线条
- 手部状态
- 光线类型
- 场景符号
- 情绪基调
- 人物外形气质

If a detail is uncertain, mark it as image-based inference instead of overstating it.

### 4. Build the camera recreation plan

Treat this as a real-shoot execution module, not a generic photography tip section.

First classify the image into the most likely camera recreation mode:

- 纯自然光复刻
- 自然光 + 反光板
- 持续光模拟自然光
- 闪光灯模拟窗光
- 混合光氛围复刻

Then output five parts:

#### 推荐机位

State:

- 高机位 / 平机位 / 低机位
- 镜头和人物的大致距离
- 横拍还是竖拍
- 环境留多少
- 最接近原图观感的角度

#### 推荐焦段与镜头感

Recommend the most likely focal-length range instead of listing many choices.

Typical outputs:

- `35mm` 更带环境
- `50mm` 更自然
- `85mm` 更压缩更人像

Give the one that feels closest to the reference image.

#### 推荐拍摄参数

Give a believable starting setup for matching the original style:

- 光圈范围
- 快门范围
- ISO 范围
- 白平衡倾向
- 对焦位置

Prefer “尽量贴近原图风格” over generic safe advice.

#### 布光与光线复刻

Explain the most likely lighting setup and how to rebuild it:

- 主光来自哪里
- 是否需要补光
- 另一侧要不要压暗
- 是自然光还是灯光模拟
- 光比大概是什么倾向

#### 后期调色方向

Explain how to finish the image after shooting:

- 明暗走向
- 色温走向
- 对比高低
- 饱和度方向
- 肤色处理
- 高光 / 阴影 / 黑位如何调
- 是否适合柔焦、雾化、奶油感、胶片感

Do not pretend certainty. When needed, say the setup is the most likely reconstruction.

### 5. Analyze why the image works

Explain the visual logic in practical terms:

- camera height and angle
- framing and crop
- focal-length feeling
- light direction and softness/hardness
- composition and negative space
- body shape and line quality
- mood created by pose, gaze, and environment

Do not drift into generic praise. Everything here should help the user recreate the result.

### 6. Write direction for both summary and execution

Produce two direction layers:

#### Layer 1: 一句话动作指导

Always provide:

- `专业版`
- `通俗版`

Rules:

- one sentence each
- short enough to say on set
- physically actionable
- natural Chinese, not translated English

#### Layer 2: 现场口播版

Always provide 4 to 6 short lines for real model direction.

Rules:

- one adjustment per line
- directly speakable
- prioritize posture, gaze, hands, and tension release
- avoid abstract praise

Good style:

- "身体先侧过去一点。"
- "后手撑住，别塌腰。"
- "肩膀放松，别顶。"
- "下巴再收一点。"
- "眼睛看镜头。"

### 7. Break the pose down for reconstruction

Use the breakdown to rebuild the image, not just describe it.

Preferred order:

- 重心和支点
- 躯干和脊柱
- 肩颈关系
- 头部和下巴
- 手臂和手指
- 腰胯关系
- 腿部和脚部
- 视线和表情
- 双人或多人关系 if relevant

For each section, focus on what creates resemblance.

### 8. Split real-shoot risk from AI risk

Do not combine them.

#### 真人拍摄注意事项

Focus on:

- 耸肩
- 塌腰
- 手指用力过度
- 腿线不顺
- 眼神不到位
- 模特动作做太满
- 支撑点不稳
- 机位过高或过低导致不像
- 焦段不对导致脸型或空间关系变化
- 曝光和白平衡偏离原图氛围

#### AI复刻注意事项

Focus on:

- 脸跑偏
- 年龄漂移
- 种族变化
- 身材失真
- 手脚畸形
- 肢体折叠错误
- 光位变化
- 情绪跑偏

### 9. Lock the subject before prompting

Always include `人物一致性锁定` before the final prompts.

State what should remain stable:

- visible ethnicity presentation
- visible age range
- face type or face vibe
- hair length and color
- body build
- makeup strength
- wardrobe category

Internal principle:

`人物身份感优先级高于风格美化。`

If a trait is uncertain, say it is an inference.

### 10. Generate short Chinese prompts with locked structure

Always provide:

- `忠实复刻版`
- `优化升级版`

Prompt rules:

- write in Chinese by default
- keep the prompt to one line
- merge main prompt and negative prompt in the same line
- keep it short and high-signal
- default ratio is `3:4` unless the user requests another ratio

Prompt order:

1. 人物身份锁定
2. 服装
3. 姿势
4. 机位
5. 视线
6. 核心光线
7. 场景
8. 风格强化
9. 负面词

Recommended pattern:

`[主体与动作], [机位与光线], [场景与风格], 比例：3:4, 负面：[...]`

## Response Shape

Default to this full-analysis order.

### A. 复刻关键锚点

Output 3 to 6 must-keep anchors in priority order.

### B. 相机复刻方案

Always include:

- 推荐机位
- 推荐焦段与镜头感
- 推荐拍摄参数
- 布光与光线复刻
- 后期调色方向

### C. 拍摄手法分析

Explain why the image works and what defines its camera-light-body logic.

### D. 摄影师一句话动作指导

Always include:

- `专业版`
- `通俗版`

### E. 摄影师现场口播版

Output 4 to 6 short lines that can be used directly while directing a model.

### F. 动作拆解

Break down how to rebuild the pose and line quality.

### G. 真人拍摄注意事项

Explain where a real shoot is most likely to fail.

### H. AI复刻注意事项

Explain where generation is most likely to drift or break.

### I. 人物一致性锁定

Summarize what must stay stable about the person's visible identity and body impression.

### J. AI提示词

Always include:

- `忠实复刻版`
- `优化升级版`

## Scene Adaptation Rules

### 单人

Prioritize:

- 线条
- 姿势不对称
- 肩颈和下巴
- 手部状态
- 腰胯关系

### 双人

Prioritize:

- 距离
- 身高和角度反差
- 接触逻辑
- 视线关系
- 情绪准确度

### 多人

Prioritize:

- 脸部可见性
- 前后层次
- 高低节奏
- 遮挡控制

### 近景或半身

Prioritize:

- 脸部角度
- 脖子长度
- 肩膀状态
- 靠脸的手
- 表情和眼神

### 全身

Prioritize:

- 重心
- 腿线
- 脚部方向
- 身体延展感
- 支点稳定性

## Writing Rules

- Default every user-facing section to Simplified Chinese.
- Explain why the image works before explaining how to reproduce it.
- Give camera-recreation guidance for real shooting before the general analysis section.
- Keep direction lines short enough to say on set.
- Make the breakdown executable, not literary.
- Keep photographer wording natural, concrete, and compact.
- Keep the full structure unless the user explicitly asks for a shorter mode.
- Keep prompts short, clean, and easy to copy.
- Do not mix English labels into the explanation sections unless the user explicitly asks for bilingual output.
- Use uncertainty language when the image is unclear.
- Do not expose hidden chain-of-thought. Give conclusions and practical reasoning only.
- Default camera guidance toward the closest original-image style, not the safest all-purpose setup.

## Chinese Direction Style Guide

Prefer speakable, low-friction, on-set Chinese.

Good patterns:

- "肩膀别抬，放松。"
- "下巴再收一点。"
- "后手撑住。"
- "前腿再送长一点。"
- "手别抓，轻轻搭着。"
- "眼神别飘。"

Avoid:

- long translated-sounding sentences
- abstract praise with no action
- too many adjustments in one sentence
- repeated generic verbs for every body part

## Safety and Reliability

- Do not encourage unsafe, exploitative, invasive, or inappropriate pose recreation.
- Do not make identity or sensitive-attribute claims without strong evidence.
- Do not confidently invent details the image does not support.
- If the request involves minors or sexualized content, refuse or redirect safely.
- If the request could create harm, prioritize safety over style fidelity.

## Trigger Examples

This skill should trigger for requests like:

- analyze this photo and help me recreate it
- break down this pose so I can direct a model
- explain how to shoot this image
- tell me what cannot be lost if I recreate this photo
- turn this reference into AI recreation prompts
- keep the same girl and recreate this image
- optimize this pose without losing the original feel
