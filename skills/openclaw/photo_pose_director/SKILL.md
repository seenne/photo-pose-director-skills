---
name: photo_pose_director
description: Analyze a reference photography image in Chinese, identify replication anchors, provide camera settings and model direction for real-shoot recreation, and generate short recreation prompts that stay close to the original person, pose, light, and mood.
metadata: {"openclaw":{"skillKey":"photo_pose_director","homepage":"https://docs.openclaw.ai/tools/creating-skills"}}
---

# Photo Pose Director

Use this skill when the user wants to analyze a reference photo, recreate it with a real camera, direct a model to match the pose, or generate AI prompts that stay close to the original person and image feeling.

## Core Goal

Treat the image as a replication target first and an analysis object second.

Always optimize for:

- what must be preserved for the image to still look like the reference
- how to guide a real model on set
- how to recreate the same camera feel, light, and grade
- how to keep the generated or photographed person close to the original subject

Internal principle:

`复刻时先求像，优化时再求更美。`

## Default Output Order

Always prefer this order unless the user asks for a shorter mode:

1. 复刻关键锚点
2. 相机复刻方案
3. 拍摄手法分析
4. 摄影师一句话动作指导
5. 摄影师现场口播版
6. 动作拆解
7. 真人拍摄注意事项
8. AI复刻注意事项
9. 人物一致性锁定
10. 忠实复刻版提示词
11. 优化升级版提示词

## Workflow

### 1. Judge the replication priority first

Before writing, decide what defines the image most strongly:

- 动作主导型
- 机位主导型
- 光感主导型
- 情绪主导型
- 人物感主导型

Rank:

- 第一优先
- 第二优先
- 辅助因素

Use that ranking to decide what to emphasize.

### 2. Extract replication anchors

Always output 3 to 6 `复刻关键锚点`.

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

### 3. Build the camera recreation plan

This section must help the user actually shoot the image.

Always include:

- `推荐机位`
- `推荐焦段与镜头感`
- `推荐拍摄参数`
- `布光与光线复刻`
- `后期调色方向`

Rules:

- Prefer the setup that feels closest to the reference image, not the safest generic setup.
- If unsure, say it is the most likely reconstruction.
- Default to camera-first guidance, not phone-first guidance.

#### 推荐机位

State:

- 高机位 / 平机位 / 低机位
- 镜头与人物的大致距离
- 横拍还是竖拍
- 环境保留多少
- 最接近原图的角度

#### 推荐焦段与镜头感

Recommend the closest focal-length feeling, such as `35mm` / `50mm` / `85mm`, and explain why.

#### 推荐拍摄参数

Provide a believable starting range:

- 光圈
- 快门
- ISO
- 白平衡
- 对焦位置

#### 布光与光线复刻

Decide the most likely mode:

- 纯自然光复刻
- 自然光 + 反光板
- 持续光模拟自然光
- 闪光灯模拟窗光
- 混合光氛围复刻

Then explain how to rebuild that light.

#### 后期调色方向

Explain:

- 明暗走向
- 色温走向
- 对比趋势
- 饱和度趋势
- 肤色处理
- 高光 / 阴影 / 黑位方向
- 是否适合柔焦、雾化、奶油感、胶片感

### 4. Analyze why the image works

Explain the visual logic in practical terms:

- 机位和取景
- 焦段观感
- 构图和留白
- 光线方向和软硬
- 身体线条
- 视线和情绪
- 场景如何帮助气氛成立

Do not drift into empty praise.

### 5. Give direction in two layers

#### 摄影师一句话动作指导

Always provide:

- `专业版`
- `通俗版`

Rules:

- one sentence each
- short enough to say on set
- physically actionable
- natural Chinese, not translated English

#### 摄影师现场口播版

Always provide 4 to 6 short lines.

Rules:

- one adjustment per line
- directly speakable
- prioritize posture, gaze, hands, tension release, and support points

Good style:

- "身体先侧过去一点。"
- "后手撑住，别塌腰。"
- "肩膀放松，别顶。"
- "下巴再收一点。"
- "眼睛看镜头。"

### 6. Break the pose down for reconstruction

Break the body down in this order when relevant:

- 重心和支点
- 躯干和脊柱
- 肩颈关系
- 头部和下巴
- 手臂和手指
- 腰胯关系
- 腿部和脚部
- 视线和表情
- 双人或多人关系

Focus on what creates resemblance.

### 7. Separate real-shoot and AI risks

#### 真人拍摄注意事项

Focus on real shooting failures:

- 耸肩
- 塌腰
- 手指用力过度
- 腿线不顺
- 眼神不到位
- 模特动作做太满
- 支撑点不稳
- 机位不对
- 焦段不对
- 曝光和白平衡偏掉

#### AI复刻注意事项

Focus on generation failures:

- 脸跑偏
- 年龄漂移
- 种族变化
- 身材失真
- 手脚畸形
- 肢体折叠错误
- 光位变化
- 情绪跑偏

### 8. Lock subject consistency before prompting

Always include `人物一致性锁定`.

State what should remain stable:

- visible ethnicity presentation
- visible age range
- face type or facial vibe
- hair length and color
- body build
- makeup strength
- wardrobe category

Internal principle:

`人物身份感优先级高于风格美化。`

### 9. Generate short Chinese prompts

Always provide:

- `忠实复刻版`
- `优化升级版`

Prompt rules:

- write in Chinese
- keep it to one line
- merge the main prompt and negative prompt in the same line
- keep it short and high-signal
- default ratio is `3:4` unless the user asks for another ratio

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

## Writing Rules

- Default every user-facing section to Simplified Chinese.
- Keep the full structure unless the user explicitly asks for a shorter mode.
- Explain why the image works before explaining how to reproduce it.
- Give camera-recreation guidance before the general analysis section.
- Keep photographer wording natural, concrete, and compact.
- Keep prompts short, clean, and easy to copy.
- Do not mix English labels into the explanation sections unless the user explicitly asks for bilingual output.
- Use uncertainty language when the image is unclear.
- Do not expose hidden chain-of-thought. Give conclusions and practical reasoning only.

## Trigger Examples

This skill should trigger for requests like:

- analyze this photo and help me recreate it
- break down this pose so I can direct a model
- tell me what cannot be lost if I recreate this image
- explain how to shoot this image with a camera
- give me camera settings and color grading for this reference
- keep the same girl and recreate this image
- turn this reference into AI recreation prompts
