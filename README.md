# Web Pixel Sandbox Builder

Turn a webpage link or screenshot into a usable offline HTML sandbox.

This repository provides a Codex skill designed for **pixel-level UI reconstruction**.

It helps AI agents analyze webpage structure, clarify intent, and generate a stable HTML sandbox that can be edited locally.

---

## What this skill solves

Recreating webpages from screenshots or broken HTML often fails because:

- layout hierarchy is unclear
- sticky / fixed regions are misinterpreted
- overlays and masks break scrolling
- AI rewrites the entire file instead of patching

This skill enforces an engineering workflow:

1. analyze structure before styling  
2. identify sticky / fixed regions  
3. clarify user intent in plain language  
4. patch instead of rewriting  
5. generate a stable offline HTML sandbox  

---

## Example workflow

Input:

- webpage link
- screenshot
- partial UI reference

The skill will:

1. analyze page structure
2. ask minimal clarification questions
3. lock module boundaries
4. generate an offline HTML sandbox
5. allow safe iterative patches

---

## Repository structure
