# Photo Pose Director Replication-First Upgrade Design

## Overview

This document defines the next upgrade for `photo-pose-director`.

The current skill can already analyze reference photography images, provide Chinese pose direction, and generate condensed AI recreation prompts. The goal of this upgrade is to shift the skill from a general analysis tool toward a replication-first execution tool while preserving the existing complete-analysis workflow.

The upgraded skill should still produce a full analysis, but its logic and output order should serve the user's real goal more directly:

- understand what makes the image look the way it does
- identify what must be preserved for a successful recreation
- guide a real model on set using photographer-style direction
- generate AI prompts that preserve the same person, pose, mood, and composition as closely as possible

## Core Product Goal

Optimize the skill for two real workflows:

1. 真人拍摄复刻
2. AI 生图复刻

The upgraded skill should prioritize replication accuracy before beautification.

Internal principle:

`复刻时先求像，优化时再求更美。`

## Why This Upgrade Is Needed

The current version is useful, but still behaves too much like an image analysis assistant. The user's actual need is execution:

- 哪些点必须保留，复刻才像
- 摄影师现场该怎么引导模特
- AI 提示词里哪些信息必须锁住，人物和动作才不会跑

This upgrade should make the skill more practical for both on-set guidance and image-generation recreation.

## Upgraded Default Output Structure

The new default structure should remain a complete analysis, but be reordered to better support replication.

### 1. 复刻关键锚点

This is the new first section.

The skill should extract 3 to 6 must-keep elements from the image. Each anchor should satisfy this rule:

`缺了它，这张图就不像了。`

Examples of anchor types:

- 机位高低
- 视线方向
- 身体朝向
- 腿部线条
- 光线类型
- 情绪基调
- 场景符号

This section should be short, direct, and prioritized.

### 2. 相机复刻方案

This is a new camera-first execution section and should appear before the general shooting analysis.

Its purpose is to help the user recreate the image with a real camera as closely as possible.

This section should always stay close to the original image style instead of falling back to generic safe camera advice.

It should include five parts:

#### 推荐机位

State:

- 高机位 / 平机位 / 低机位
- 镜头与人物的大致距离
- 横拍还是竖拍
- 环境保留比例
- 最接近原图观感的角度

#### 推荐焦段与镜头感

Estimate which focal-length feeling matches the image best, such as:

- 35mm
- 50mm
- 85mm

Do not just list options. Recommend the most likely range and explain why it best matches the image.

#### 推荐拍摄参数

Provide a close-style starting point rather than generic exposure advice.

Typical outputs should include:

- 光圈范围
- 快门范围
- ISO 范围
- 白平衡倾向
- 对焦位置

The goal is not technical certainty, but the most believable starting setup for recreating the same image feel.

#### 布光与光线复刻

Decide what the image most likely uses:

- 纯自然光
- 自然光加反光板
- 持续光模拟自然光
- 闪光灯模拟窗光
- 混合光氛围复刻

Then give the most likely replication setup, not just a broad lighting description.

#### 后期调色方向

This should become a standard section.

Explain:

- 明暗趋势
- 色温趋势
- 对比趋势
- 饱和度趋势
- 肤色处理
- 高光 / 阴影 / 黑位方向
- 是否适合柔焦、雾化、奶油感、胶片感

This should tell the user not only how to shoot the image, but how to finish it.

### 3. 拍摄手法分析

Keep the existing full analysis, but move it after the replication anchors.

This section explains:

- why the shot works
- what camera angle or focal-length feeling matters
- what light behavior matters
- what composition and body logic matter

### 4. 摄影师一句话动作指导

Keep both versions:

- 专业版
- 通俗版

The tone should stay short, speakable, and Chinese-first.

### 5. 摄影师现场口播版

This is a new execution-focused section.

It should output 4 to 6 short live direction lines. Each line should change only one thing at a time.

Examples of the intended style:

- “身体先侧过去一点。”
- “后手撑住，别塌腰。”
- “肩膀放松，别顶。”
- “下巴再收一点。”
- “眼睛看镜头，不要飘。”

This section is designed for real on-set use.

### 6. 动作拆解

Keep the existing structured breakdown, but align it more explicitly with reconstruction:

- how to place the body
- how to create the same shape
- how to avoid losing the same line quality

### 7. 真人拍摄注意事项

This is now separated from AI notes.

It should focus on real shooting failure points such as:

- 耸肩
- 塌腰
- 手指用力过度
- 腿线不顺
- 眼神不到位
- 模特动作做得太满或太僵

### 8. AI 复刻注意事项

This is also separated into its own section.

It should focus on generation failure points such as:

- 脸跑偏
- 年龄漂移
- 种族变化
- 身材失真
- 手脚畸形
- 身体折叠错误
- 光位变化
- 情绪跑偏

### 9. 人物一致性锁定

This is a new section that should appear before the final prompts.

Its purpose is to explicitly state which identity-like visual properties must be preserved in recreation:

- apparent ethnicity
- apparent age range
- face type or facial vibe
- hair length and color
- body build
- makeup strength
- wardrobe category

This section should help both the user and the prompt remain focused on preserving the same person.

### 10. AI 提示词

Keep:

- 忠实复刻版
- 优化升级版

The current prompt style should remain:

- 中文
- 单行
- 精简
- 主提示词和负面提示词合并
- 默认比例 3:4

But the internal structure should now be more disciplined:

- first half = must-lock information
- second half = beautification information

## Camera-Recreation Decision Layer

The upgraded skill should add one more internal judgment before outputting the camera section.

It should classify the image into the most likely real-shoot recreation mode:

- 纯自然光复刻
- 自然光 + 反光板
- 持续光模拟自然光
- 闪光灯模拟窗光
- 混合光氛围复刻

This prevents the skill from always reducing camera advice to “window light” or generic portrait rules.

The chosen mode should control:

- the camera section
- the lighting section
- the suggested starting parameters
- the post-processing direction

## New Internal Decision Layer

The upgraded skill should add a replication-priority classifier before normal analysis.

This classifier should decide what defines the image most strongly.

### Replication Priority Classes

1. 动作主导型
2. 机位主导型
3. 光感主导型
4. 情绪主导型
5. 人物感主导型

Most images may involve more than one, but the skill should determine:

- first priority
- second priority
- supporting factors

This ranking should control what gets emphasized in the output.

### How It Should Affect Output

If the image is:

- 动作主导型: make pose breakdown more detailed
- 机位主导型: emphasize camera angle and anchor section more strongly
- 光感主导型: elevate lighting analysis and prompt lighting terms
- 情绪主导型: emphasize gaze, expression, and emotional tone
- 人物感主导型: strengthen subject-consistency locking

## Replication Anchors Logic

The skill should always generate replication anchors before the explanation section.

Anchor extraction rules:

- output 3 to 6 anchors
- prefer elements that change resemblance the most
- do not output low-value details just because they are visible
- if uncertain, mark the element as image-based inference

Examples:

- “高机位俯拍必须保留”
- “眼神直视镜头是核心”
- “前腿拉长是线条重点”
- “暖色窗边斜光不能丢”
- “人物要保持年轻东亚女生的脸和清瘦体态”

## Photographer Live-Direction Logic

The skill should now support two direction layers:

### Layer 1: One-Line Direction

Use one sentence to summarize the pose direction.

### Layer 2: Live Direction Chain

Use 4 to 6 short instructions in sequence for real set direction.

Rules:

- one physical adjustment per line
- each line must be directly speakable
- avoid abstract praise and interpretation
- prioritize posture, gaze, hands, and tension release

## Subject Consistency Upgrade

This is a core requirement for recreation quality.

The skill should explicitly prioritize subject consistency in faithful recreation mode.

Internal principle:

`人物身份感优先级高于风格美化。`

### Default Subject Locking Dimensions

- 东亚或其他可见种族呈现
- 年龄段
- 脸型气质
- 发型长度与发色
- 身材类型
- 服装类别
- 妆感强弱

The optimized prompt may beautify styling or pose quality, but should not drift away from the subject identity unless the user explicitly requests a change.

## Prompt Strategy Upgrade

The prompts should remain compact and Chinese.

### Required Prompt Format

Single-line format:

`[主体与动作], [场景与光线], 比例：3:4, [风格与镜头], 负面：[...]`

### Required Prompt Logic

First half should prioritize:

- 人物身份锁定
- 服装
- 姿势
- 机位
- 视线
- 核心光线

Second half should add:

- 画面风格
- 气质词
- 质感词

This ordering should reduce drift during generation.

## Full Analysis Philosophy After Upgrade

The skill should remain a complete-analysis tool, not a minimal-output tool.

However, the analysis should now follow this execution logic:

`先抓像 -> 再解释为什么像 -> 再指导怎么摆 -> 再提醒哪里会翻车 -> 再生成复刻提示词`

With the camera module added, the execution flow becomes:

`先抓像 -> 再给相机复刻方案 -> 再解释为什么像 -> 再指导怎么摆 -> 再提醒哪里会翻车 -> 再生成复刻提示词`

This is the key product shift.

## What Should Not Change

The following should remain:

- Chinese-first explanations
- short photographer-style direction
- concise prompt style
- merged negative prompts
- default 3:4 output ratio
- full-scene support for single, pair, and group subjects

## Future Implementation Notes

The skill update should minimally require:

- updating `C:\Users\jcsta\.codex\skills\photo-pose-director\SKILL.md`
- optionally refreshing `C:\Users\jcsta\.codex\skills\photo-pose-director\agents\openai.yaml`

No extra reference files are required yet unless the skill later gains model-specific prompt variants or platform-specific shooting modes.
