# Photo Pose Director Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a reusable Codex skill named `photo-pose-director` that analyzes a photography reference image, produces photographer-style pose direction, breaks the pose down into actionable instructions, and outputs AI prompt sets for recreation and optimization.

**Architecture:** Keep the skill implementation lean and mostly self-contained inside `SKILL.md`, with UI-facing metadata in `agents/openai.yaml`. Store the approved design in the workspace and install the actual skill under the user's Codex skills directory so it is immediately usable.

**Tech Stack:** Markdown, YAML, Python validation scripts bundled with the system skill creator

---

### Task 1: Initialize the skill scaffold

**Files:**
- Create: `C:\Users\jcsta\.codex\skills\photo-pose-director\SKILL.md`
- Create: `C:\Users\jcsta\.codex\skills\photo-pose-director\agents\openai.yaml`

- [ ] **Step 1: Initialize the new skill directory**

Run: `python C:\Users\jcsta\.codex\skills\.system\skill-creator\scripts\init_skill.py photo-pose-director --path C:\Users\jcsta\.codex\skills --interface display_name="Photo Pose Director" --interface short_description="Analyze reference poses and generate photographer-ready guidance." --interface default_prompt="Use $photo-pose-director to analyze this reference image, direct the pose, and generate recreation and upgrade prompts."`

Expected: skill folder, starter `SKILL.md`, and `agents/openai.yaml` are created.

- [ ] **Step 2: Confirm the scaffold exists**

Run: `Get-ChildItem -Recurse C:\Users\jcsta\.codex\skills\photo-pose-director`

Expected: `SKILL.md` and `agents\openai.yaml` are present.

### Task 2: Replace scaffold content with the approved workflow

**Files:**
- Modify: `C:\Users\jcsta\.codex\skills\photo-pose-director\SKILL.md`

- [ ] **Step 1: Write the final frontmatter and overview**

Include the approved skill name, trigger-rich description, and a concise overview.

- [ ] **Step 2: Add the execution workflow**

Document task classification, scene classification, pose skeleton extraction, photographer direction, pose breakdown, correction pass, and dual-prompt generation.

- [ ] **Step 3: Add response rules and safety boundaries**

Document dynamic output behavior, uncertainty handling, and inappropriate-content guardrails.

### Task 3: Verify skill metadata

**Files:**
- Modify: `C:\Users\jcsta\.codex\skills\photo-pose-director\agents\openai.yaml`

- [ ] **Step 1: Confirm UI metadata matches the skill**

Keep `display_name`, `short_description`, and `default_prompt` aligned with the implemented skill behavior.

### Task 4: Validate the skill structure

**Files:**
- Validate: `C:\Users\jcsta\.codex\skills\photo-pose-director`

- [ ] **Step 1: Run structural validation**

Run: `python C:\Users\jcsta\.codex\skills\.system\skill-creator\scripts\quick_validate.py C:\Users\jcsta\.codex\skills\photo-pose-director`

Expected: `Skill is valid!`

- [ ] **Step 2: Spot-check the final files**

Run: `Get-Content -Raw C:\Users\jcsta\.codex\skills\photo-pose-director\SKILL.md`

Expected: the skill reads as a concise, reusable guide rather than a design spec.
