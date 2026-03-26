# Photo Pose Director Design

## Overview

`photo-pose-director` is a high-flexibility skill for analyzing a reference photography image and turning it into actionable posing direction, shooting interpretation, and AI image-generation prompts.

The skill should support:

- image-only input
- text-only intent refinement
- image + text combined workflows
- single-person, two-person, and multi-person scenes
- close-up, half-body, and full-body framing
- standing, sitting, crouching, leaning, walking, lying, and mixed poses
- both faithful recreation and optimized reinterpretation

The output should feel like a photographer-director rather than a generic image captioner. The skill must translate visual information into executable pose guidance and reusable prompt structures.

## Goals

- Analyze the shooting method behind a reference photo
- Explain why the pose and composition work visually
- Give one-line posing guidance in a photographer's voice
- Provide both professional and plain-language direction
- Break the pose into actionable body-part instructions
- Flag mistakes, risks, and common failure points
- Generate detailed AI prompts for both faithful recreation and optimized improvement

## Non-Goals

- Blindly describe every visible object in the image
- Make unsupported claims about identity, intent, or backstory
- Output only aesthetic adjectives without concrete pose logic
- Treat all images with a rigid fixed template
- Recreate unsafe, exploitative, or inappropriate content without safeguards

## Inputs

### Required

- One reference photography image

### Optional

- User intent or style goal
- Constraints such as:
  - subject gender presentation
  - subject count
  - wardrobe
  - location preference
  - platform use case
  - camera or lens preference
  - whether the result is meant for AI image generation
- Output preferences such as:
  - more professional
  - more beginner-friendly
  - focus on pose
  - focus on lighting
  - one-line guidance only

## Output Strategy

The skill should use a fixed high-level workflow but dynamically expand or compress sections depending on the image complexity and user goal.

This should be a modular output system, not a rigid template system.

### Core Output Modules

1. Shooting method analysis
2. One-line photographer instruction
3. Pose breakdown
4. Notes and cautions
5. AI generation prompts
6. Optional enhancement suggestions

### Dynamic Expansion Rules

- Single-person images should emphasize line, weight distribution, torso angle, and gesture nuance
- Two-person images should emphasize relational geometry, eye direction, spacing, and contact logic
- Multi-person images should emphasize arrangement, depth layering, rhythm, overlap, and visibility
- Tight portraits should emphasize head angle, neck extension, shoulder height, hand placement, and gaze
- Full-body images should emphasize stance, hip-to-chest relationship, leg lines, grounding, and balance
- Recreation-focused requests should prioritize accuracy
- Optimization-focused requests should prioritize improvement while preserving core visual logic

## Internal Workflow

The skill should follow this internal sequence before composing the response.

### 1. Determine the User Task

Classify the request as one or more of:

- pose study
- shoot recreation
- pose optimization
- AI prompt recreation
- AI prompt enhancement

If user text exists, merge it with the image analysis before generating output.

### 2. Classify Scene and Subject Structure

Identify:

- subject count: single, pair, group
- framing: close-up, half-body, full-body
- posture: standing, sitting, crouching, leaning, walking, lying, dynamic
- environment: studio, interior, street, night, natural light, window light, editorial, lifestyle
- emotional mode: distant, intimate, relaxed, assertive, soft, fashion-forward, documentary, cinematic

### 3. Extract the Pose Skeleton

Translate the visual pose into executable structure:

- weight placement
- base of support
- torso angle and twist
- shoulder height relationship
- chest-to-pelvis orientation
- arm purpose: support, decoration, frame, concealment, lead-in
- hand logic and finger tension
- hip angle and line
- leg function: load-bearing, relaxed, crossed, extended, staggered
- foot direction and grounding
- head tilt, chin projection, neck length
- gaze target and emotional read
- subject-to-subject relationship when more than one person is present

### 4. Translate into Photographer Direction

Convert visual analysis into direct, speakable guidance.

This must produce:

- one professional photographer-style instruction
- one plain-language instruction

Both should be short, specific, and usable in a live shoot.

### 5. Expand into Pose Breakdown

Decompose the instruction into 4 to 8 practical actions when appropriate.

Preferred breakdown order:

- weight and balance
- torso and spine
- shoulders and neck
- head and chin
- arms and hands
- hips and waist
- legs and feet
- gaze and facial expression
- interaction logic for pairs or groups

### 6. Run Correction and Risk Pass

Flag issues such as:

- stiff hands
- flat shoulders
- collapsed waist
- awkward limb compression
- poor visibility in group formations
- forced intimacy in paired poses
- contradictory eye lines
- hand, foot, and contact failures that AI models often distort

If the original image itself is weak in a specific area, the skill may say so and improve it in the optimized version.

### 7. Generate Dual Prompt Tracks

Produce two AI prompt tracks:

- Faithful Recreation
- Optimized Upgrade

Both should include:

- main prompt
- composition and framing cues
- lens and camera feel
- lighting cues
- pose and body-relationship cues
- mood and styling cues
- negative prompt guidance
- optional generation parameter suggestions when useful

## Final Response Shape

The response should usually follow this shape, while remaining adaptive.

### A. Shooting Method Analysis

Explain:

- the visual core of the image
- camera angle
- framing
- composition strategy
- focal-length feeling
- light direction and softness/hardness
- mood and pose logic

### B. One-Line Photographer Direction

Provide:

- Professional version
- Plain-language version

### C. Pose Breakdown

Break down the pose from large structure to small details.

Default order:

- center of gravity
- torso direction
- shoulders and head
- arms and hands
- waist and hips
- legs and feet
- gaze and expression
- partner or group interaction logic if relevant

### D. Notes and Cautions

Include:

- likely mistakes
- what makes the pose fail
- what to avoid in replication
- what to correct for better lines or believability

### E. AI Generation Prompts

Provide two full prompt sets:

#### Faithful Recreation Prompt

Match the original pose, composition, and atmosphere as closely as possible.

#### Optimized Upgrade Prompt

Preserve the core pose concept while improving:

- body lines
- emotional clarity
- visual hierarchy
- commercial/editorial strength
- realism or image-model reliability

### F. Optional Enhancement Suggestions

Show only when valuable:

- better wardrobe direction
- better scene substitution
- more flattering lens choices
- stronger micro-adjustments
- how to adapt the pose for short video or a second frame

## Response Principles

- Explain why the pose works before explaining how to perform it
- Keep one-line direction short enough to say out loud during a shoot
- Make the breakdown physically actionable
- Avoid empty style language without pose logic
- Clearly mark inference when image information is incomplete
- Allow the optimized version to improve flawed source material
- Favor practical usefulness over exhaustive description

## Style and Tone

The skill should sound like a photographer who understands direction, body language, and image-making.

### Analysis Tone

- professional
- visually literate
- concise
- confident without overstating certainty

### Direction Tone

- direct
- shoot-ready
- easy to execute
- available in both expert and beginner-friendly language

### Prompt Tone

- structured
- detailed
- model-friendly
- grounded in composition, pose, and light rather than vague adjectives

## Trigger Guidance

This skill should trigger for requests like:

- analyze this photography pose
- break down this model pose
- explain how this photo was shot
- give me one-line posing direction from this image
- turn this pose into AI prompts
- recreate this image pose and improve it
- analyze this couple pose
- analyze this group pose

## Safety and Reliability Rules

- Do not encourage unsafe, exploitative, invasive, or inappropriate pose recreation
- Do not confidently describe unclear body details as facts
- Do not infer identity or sensitive attributes without strong evidence
- Mark uncertain sections as image-based inference
- Do not produce prompts that are only mood words with no pose structure

## Recommended Skill Name

`photo-pose-director`

Why:

- broad enough to cover analysis, direction, recreation, and optimization
- specific enough to be searchable
- more durable than a name focused only on “breakdown” or only on “replication”

## Future Implementation Notes

The eventual skill should likely include:

- a concise `SKILL.md`
- optional reference examples for:
  - single-person poses
  - pair poses
  - group poses
  - portrait framing
  - full-body framing
- optional prompt-format examples for common image models

The implementation should preserve high flexibility and avoid forcing identical section lengths across all images.

## Open Questions Resolved in This Design

- Input mode: image and optional text, both supported
- Output style: professional and plain-language versions, both supported
- Scene coverage: single, pair, group, and multiple posture types supported
- Prompt strategy: faithful recreation and optimized upgrade, both supported
- Template philosophy: modular and high-flexibility, not rigid
