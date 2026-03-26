# GitHub Home Polish Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Rework the repository homepage so the top of the README feels like a concise product homepage plus installation hub, helping new visitors understand value quickly and perceive the project as polished and star-worthy.

**Architecture:** Keep the existing repository structure, cover art, release assets, and examples intact, but rewrite the README information architecture and copy. The work should focus on reshaping the homepage flow into a product-style hero, condensed value sections, platform quick start, and trust-building proof points without turning the page into marketing fluff.

**Tech Stack:** Markdown, GitHub README rendering, existing repository assets, GitHub release links

---

## File Structure

- Modify: `C:\Users\jcsta\Desktop\动作拆解app\README.md`
  - Restructure the homepage into the approved sections and rewrite copy in a shorter, more product-like style.
- Reference: `C:\Users\jcsta\Desktop\动作拆解app\assets\github-cover.png`
  - Preserve the current cover image as the visual hero asset.
- Reference: `C:\Users\jcsta\Desktop\动作拆解app\assets\social-preview.png`
  - Keep the social preview asset aligned with the README tone; no content changes expected.
- Reference: `C:\Users\jcsta\Desktop\动作拆解app\docs\superpowers\specs\2026-03-26-github-home-polish-design.md`
  - Follow the approved information architecture and tone guidance.

### Task 1: Rewrite the README homepage structure

**Files:**
- Modify: `C:\Users\jcsta\Desktop\动作拆解app\README.md`
- Reference: `C:\Users\jcsta\Desktop\动作拆解app\docs\superpowers\specs\2026-03-26-github-home-polish-design.md`

- [ ] **Step 1: Review the current README and approved design spec**

Read:
- `Get-Content -Encoding UTF8 README.md`
- `Get-Content -Encoding UTF8 docs\superpowers\specs\2026-03-26-github-home-polish-design.md`

Expected:
- Confirm which existing sections should be removed, merged, or reordered.

- [ ] **Step 2: Rewrite the top of the README into the approved homepage flow**

Update `README.md` so the primary order becomes:
- Hero
- Core Value
- Why It Feels Professional
- Quick Start
- Examples and Releases
- Docs and Design Sources

Implementation notes:
- Keep the cover image near the top.
- Replace long explanatory paragraphs with short positioning copy.
- Surface `Codex`, `OpenClaw`, `ChatGPT`, and `Gemini` early.
- Keep links to examples and release assets close to the surface.
- Preserve enough depth for advanced users, but move it later in the page.

- [ ] **Step 3: Ensure the homepage copy feels restrained and product-like**

Review the rewritten README and remove:
- repeated claims
- overly long bullet lists
- tutorial-style wording near the top
- anything that feels like documentation before value

Expected:
- The top half of the README should read like a product landing page, not a full manual.

- [ ] **Step 4: Verify Markdown readability and link visibility**

Run:
- `Get-Content -Encoding UTF8 README.md | Select-Object -First 120`

Expected:
- Section order matches the approved design.
- The top-level value proposition is clear within the first screenful of text.
- Platform entry points, examples, and release references are easy to find.

- [ ] **Step 5: Commit the README polish**

Run:
- `git add README.md`
- `git commit -m "docs: polish GitHub homepage README"`

Expected:
- A focused commit that only contains the homepage polish work.

### Task 2: Verify repository state after polish

**Files:**
- Modify: none
- Verify: `C:\Users\jcsta\Desktop\动作拆解app\README.md`

- [ ] **Step 1: Check git status**

Run:
- `git status --short`

Expected:
- Clean working tree after the README commit.

- [ ] **Step 2: Confirm the latest release remains the surfaced installation target**

Run:
- `gh release view v1.1.0 --json url,tagName,name`

Expected:
- `v1.1.0` is still the latest intended release to reference from the README.

- [ ] **Step 3: Push the README polish commit**

Run:
- `git push origin main`

Expected:
- Homepage changes are available on GitHub.
