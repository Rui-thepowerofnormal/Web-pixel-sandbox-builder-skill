---
name: web-pixel-sandbox-builder
description: Turn a webpage link, screenshot, or partial UI reference into a usable offline HTML sandbox through structure-first analysis, intent clarification, and minimal-risk engineering patches.
---

# Web Pixel Sandbox Builder

## Purpose

Use this skill when the user wants to recreate, approximate, or iteratively refine a webpage or product UI as an offline HTML file.

This skill is for engineering-grade UI reconstruction, not casual mockups. The goal is to produce a usable local HTML sandbox that can be opened offline, patched safely, and iterated over without repeatedly rewriting the whole page.

## When to use

Use this skill when the user provides any of the following:

- a webpage link
- a full-page screenshot
- partial screenshots of UI regions
- an existing HTML file that needs restoration or refinement
- a broken sandbox version plus a visual target

Use this skill especially when the task requires:

- pixel-level layout reconstruction
- fixed / sticky region analysis
- overlay / drawer / mask / slab behavior
- internal scrolling tables
- preserving already-approved modules while patching only broken areas
- generating a single-file offline HTML deliverable

## Operating mode

Work in engineering delivery mode, not chatty iteration mode.

Always follow this sequence:

1. Analyze the current artifact and the visual reference completely before proposing code.
2. Identify the full problem set, including structure, layout, masking, scrolling, and interaction relationships.
3. Ask only the minimum necessary clarification questions in plain language.
4. Lock the scope: identify which modules are allowed to change and which are frozen.
5. Prefer the smallest safe patch over full-file rewrites.
6. Output a single final solution, not multiple speculative versions.
7. If a stable version is reached, recommend creating a snapshot copy before further edits.

## Core principles

- Structure before styling.
- Layout before color.
- Layering before spacing.
- Masking and stickiness are structural problems, not cosmetic ones.
- Screenshots are the visual source of truth when they conflict with model assumptions.
- Treat already-approved modules as locked unless the user explicitly allows changes.
- If the task is complex or ambiguous, plan first before editing.
- Do not rewrite the full file unless there is no safe patch path.

## Input handling

If the user provides both screenshots and an existing HTML file:

- treat the HTML file as the current baseline
- treat the screenshots as the visual truth

If the user provides only screenshots or links:

- first generate a stable structural skeleton
- then refine toward visual accuracy

If sensitive names or identifiers appear in the source material:

- replace them with neutral demo placeholders
- preserve layout realism while anonymizing content

## Analysis framework

For every task, identify the following before making changes:

- global page frame and content width
- fixed vs sticky vs scrollable regions
- whether top rows act as true reserved layout space or only visual overlays
- left / right column proportions
- whether tables should expand the page or scroll internally
- whether floating elements belong to the page, a module, or an overlay
- whether a problem is caused by color, spacing, z-index, overflow, position, grid, or DOM hierarchy

Do not assume a universal page module structure. Infer the structure from the provided artifact.

## Clarification rules

Ask only if the answer cannot be safely inferred from the provided references or current file.

When asking, use plain language.

Good example:
- Should the left title and the white module stay fixed together as one block?

Bad example:
- Should the container be sticky or fixed?

Limit clarifications to the fewest questions necessary to unblock engineering decisions.

## Editing rules

When editing an existing file:

- read the full current file first
- identify exact broken regions
- patch only the affected CSS / HTML / JS blocks when possible
- preserve working IDs, class hooks, and existing interactions unless the user allows structural refactoring
- after editing, report exact changed line ranges and a one-sentence summary per changed block

When the file is badly corrupted:
- explain why full replacement is safer than patching
- then generate one full replacement artifact

## Output requirements

The final output should be one of the following:

- a single-file offline HTML document
- a minimal patch with exact replacement ranges
- a Codex-ready engineering prompt that tells Codex exactly what to inspect, modify, preserve, and save

If outputting instructions for Codex, require:

- use current file as source of truth
- read before editing
- write directly into the file
- save in place
- report changed line ranges only

## Snapshot discipline

Once the user confirms a version is good:

- recommend creating a snapshot copy
- continue future edits from the main file, not the snapshot
- keep the snapshot untouched as a restore point

## Success criteria

A successful run of this skill produces a sandbox that is:

- visually faithful to the provided reference
- structurally stable
- editable with small patches
- usable offline
- safe to evolve without repeatedly breaking already-approved modules
