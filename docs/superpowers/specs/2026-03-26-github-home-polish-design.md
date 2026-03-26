# GitHub Home Polish Design

## Overview

This document defines a focused polish pass for the GitHub repository homepage of `photo-pose-director-skills`.

The repository already contains working skill packs, platform packs, examples, release assets, and visual branding materials. The current README is informative, but it still reads more like a complete documentation page than a concise, product-grade repository homepage.

The goal of this design is to make the repository feel:

- 简洁
- 大方
- 高端
- 更像产品官网

while still preserving the practical clarity that a GitHub visitor expects.

## User Goal

When a new visitor lands on the repository homepage, the page should help them:

1. 在 5 到 10 秒内理解这个项目的价值
2. 感受到项目完成度和专业度
3. 愿意继续了解、下载、安装，甚至 star 或分享

This homepage should not try to explain everything up front. It should behave like a product landing page that quickly creates trust and momentum.

## Primary Product Positioning

The repository should present `Photo Pose Director Skills` as:

`从参考图到可执行复刻方案。`

This positioning is stronger and more product-like than a broad “photography analysis tool” framing, because it communicates an end-to-end workflow:

- analyze the reference image
- extract replication anchors
- guide a real model
- recreate the shot with camera advice
- generate AI prompts for recreation

## Design Direction

The approved direction is:

`产品首页 + 安装中枢`

This means the README homepage should balance two needs:

- Product-homepage feel:
  - strong hero
  - short copy
  - controlled visual rhythm
  - clear value summary
- Installation hub clarity:
  - obvious platform entry points
  - examples and releases close to the surface
  - minimal friction to get started

This is the best fit for the current repository because it improves first impression without hiding the practical entry points.

## Information Architecture

The homepage should be restructured into the following sections.

### 1. Hero

The hero should contain:

- the repository cover image
- a short one-line positioning statement
- a short supporting sentence
- platform badges for `Codex`, `OpenClaw`, `ChatGPT`, and `Gemini`

Purpose:

- establish product identity immediately
- reduce the feeling of “long documentation page”
- make the project feel intentional and finished

### 2. Core Value

This section should summarize the product into three compact points:

- 分析参考图
- 指导真人拍摄
- 生成 AI 复刻提示词

Purpose:

- explain the value without overwhelming the reader
- make the repository legible to both photography users and AI users

### 3. Why It Feels Professional

This section should highlight a few differentiated capabilities rather than a long feature list.

Recommended points:

- 复刻关键锚点
- 相机机位与参数建议
- 摄影师现场口播指导
- 人物一致性锁定

Purpose:

- establish credibility quickly
- show that this project goes beyond generic image analysis

### 4. Quick Start

This section should act as the installation hub.

It should present four clear platform entry points:

- Codex
- OpenClaw
- ChatGPT
- Gemini

Each entry should feel lightweight and actionable rather than overexplained.

Purpose:

- help the user start quickly
- reduce scanning effort
- make the repository more conversion-oriented

### 5. Examples and Releases

This section should surface proof of completeness.

It should include:

- the real-shoot recreation examples
- the latest release / downloadable packages

Purpose:

- show that the project is already usable
- increase confidence and willingness to star

### 6. Docs and Design Sources

This final section should preserve access to:

- specs
- implementation plan
- examples directory

Purpose:

- keep depth available for advanced users
- avoid cluttering the top of the homepage

## Copy Style

The copy should be written in a restrained product style.

Rules:

- use shorter sections
- prefer one strong sentence over long explanation
- avoid repeating the same promise in multiple places
- avoid sounding like ad copy
- avoid sounding like a dense technical manual

Target feeling:

`克制、清楚、可信、像成品。`

## Visual Tone

The visual language should stay aligned with the existing cover and social preview assets:

- warm neutral tones
- soft but premium photography mood
- minimal clutter
- strong hierarchy through spacing rather than decoration

The README itself should not become visually noisy. The assets should carry atmosphere; the text should carry clarity.

## Non-Goals

This polish pass should not:

- rewrite the entire repository documentation set
- add new product functionality
- overload the homepage with too many screenshots
- turn the README into a marketing-heavy landing page

## Success Criteria

This work is successful when:

1. the top of the README reads like a product homepage rather than a long manual
2. a first-time visitor can understand the value quickly
3. installation paths for all four platforms are easier to find
4. examples and release assets are visible enough to build trust
5. the repository feels more polished and star-worthy without becoming noisy
