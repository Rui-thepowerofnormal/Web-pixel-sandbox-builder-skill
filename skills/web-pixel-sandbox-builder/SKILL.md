Web Pixel Sandbox Builder
Purpose

Use this skill when the user wants to recreate, approximate, or iteratively refine a webpage or product UI as an offline HTML sandbox.

This skill operates in engineering reconstruction mode, not mockup mode.

The goal is to produce a usable single-file HTML sandbox that:

opens offline
preserves stable structure
can be safely patched
allows iterative UI refinement without rewriting the entire page

The sandbox should behave like a product UI environment, not a static screenshot replica.

When to use

Use this skill when the user provides any of the following:

a webpage link
a full-page screenshot
partial screenshots of UI regions
an existing HTML sandbox that needs restoration
a broken sandbox plus a visual target
a UI reference that needs to become an editable HTML environment

Typical use cases include:

pixel-level layout reconstruction
recreating dashboards
restoring broken sandbox files
UI iteration without breaking stable modules
engineering reconstruction from visual references
Operating mode

Work in engineering delivery mode, not conversational exploration.

Always follow the structured reconstruction pipeline.

Never jump directly to code generation.

Always complete structural reasoning before proposing implementation.

The correct workflow is:

Reference input
↓
Interaction-first visual parsing
↓
Visual interaction tree
↓
Clarification and interaction contract
↓
Layout skeleton
↓
Engineering reconstruction
↓
Minimal safe patch or full sandbox output
Core principles

Structure before styling.

Layout before color.

Layering before spacing.

Masking and stickiness are structural problems, not cosmetic ones.

Screenshots are the visual source of truth when they conflict with model assumptions.

Approved modules must be treated as locked unless the user explicitly allows modification.

Prefer minimal safe patches over full-file rewrites.

Never generate speculative alternative versions.

Always produce one stable engineering result.

Input handling
If the user provides both screenshots and HTML

Treat the HTML file as the current baseline.

Treat the screenshots as the visual source of truth.

The HTML must be patched to match the screenshots.

If the user provides only screenshots or links

First reconstruct a stable interaction structure.

Then build a structural HTML skeleton.

Only then refine visual accuracy.

If sensitive identifiers appear

Replace them with neutral placeholders while preserving layout realism.

Step 1 — Artifact inspection

Before proposing any structure or code:

Inspect the provided reference completely.

Identify:

page frame
visible modules
interaction zones
scroll containers
overlays
tables and charts
navigation structures

Do not assume any layout patterns at this stage.

Step 2 — Interaction-first structural analysis

This step replaces traditional layout inference.

Before making any engineering decision, the model must first reconstruct the visual interaction structure of the page.

This step is mandatory.

No HTML generation is allowed before completing it.

Visual truth rule

During this stage:

Do NOT rely on historical UI patterns.

Do NOT assume common layouts.

Do NOT infer frameworks.

Do NOT reuse prior examples.

Only use direct visual evidence from the provided screenshots or webpage.

If the structure cannot be determined visually, mark uncertainty instead of guessing.

Generate a visual interaction tree

The model must produce a tree-style interaction map representing the visible UI structure.

Example format:

app
 ├─ topbar
 ├─ drawer
 └─ main.page
      └─ page-inner
           └─ page-shell
                ├─ frozen header area
                │    ├─ page-header-row
                │    └─ left-fixed-group
                │
                └─ right-scroll-group
                     ├─ shop-header
                     ├─ overview
                     │    ├─ KPI grid
                     │    └─ chart
                     └─ campaigns
                          ├─ tabs
                          ├─ filters
                          └─ campaign-table

This tree represents the visual interaction skeleton, not the final HTML structure.

Structural categories to identify

When generating the tree, identify:

global page frame
navigation areas
fixed UI regions
frozen header zones
scroll containers
interaction modules
data containers
chart areas
table containers
filter panels
drawers or overlays

Only include elements that are visually observable.

Handling uncertainty

If any region cannot be reliably determined:

Mark the node as uncertain.

Example:

main.page
 ├─ overview
 └─ campaigns
      └─ table-container (?) 

The model must not invent structure.

Pause rule

If the interaction tree is unstable or ambiguous:

Pause and ask clarification questions before continuing.

Do not proceed to layout engineering.

Step 3 — Clarification and interaction contract

Once the interaction tree is created:

Ask the minimum number of clarification questions needed to resolve structural uncertainty.

Questions must be written in plain language.

Good example:

Should the page header stay fixed when the campaign table scrolls?

Bad example:

Should the container use sticky positioning?

Interaction contract

After clarification, define the interaction contract:

Identify:

fixed regions
scroll regions
overlay behaviors
module boundaries
interaction granularity required for the sandbox

This determines what the sandbox must support.

Step 4 — Layout skeleton

Only after the interaction contract is defined:

Construct the layout skeleton.

This skeleton defines:

major containers
scroll hierarchy
fixed zones
layout grouping

Still avoid styling.

Focus only on structural layout.

Step 5 — Engineering reconstruction

Now convert the layout skeleton into implementation.

Choose stable layout methods.

Possible layout systems include:

flex
grid
container stacking
scroll containers
sticky positioning
overflow isolation

But only after structure is finalized.

Editing rules

When editing an existing sandbox file:

Read the full file before editing.
Identify broken regions.
Patch only the necessary blocks.
Preserve working IDs and class hooks.
Do not remove existing interaction behavior unless necessary.
Minimal patch preference

Prefer modifying:

CSS rules
layout containers
specific DOM blocks

Avoid rewriting the entire file unless absolutely required.

Full replacement rule

If the file is structurally corrupted:

Explain why patching is unsafe.

Then generate a full replacement sandbox.

Output requirements

The final output must be one of the following:

Single-file sandbox

A complete offline HTML file.

Minimal patch

Provide exact replacement ranges.

Explain each modification briefly.

Codex-ready engineering instruction

If the user is editing locally, provide a precise instruction block telling Codex:

read current file
modify only specified blocks
preserve working modules
save changes in place
report changed line ranges
Snapshot discipline

Once the user confirms a version is stable:

Recommend creating a snapshot copy.

The snapshot must remain untouched.

All future edits should continue from the main working file.

Success criteria

A successful sandbox must be:

Visually faithful to the reference.

Structurally stable.

Patchable with small changes.

Editable without breaking approved modules.

Usable as a local offline environment.

Safe for iterative UI engineering.
