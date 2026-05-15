# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

Static GitHub Pages **project page** for the paper *Poke-RL-0: Iterative Real-World Post-Training of Flow-Based VLAs with Trust-Region Flow Matching Optimization (TRFO)*. The page is the public landing for the work — paper teaser, method overview, system diagrams, task videos, and results.

There is no build system, no framework, no package manager. The site is plain `index.html` + assets, served directly by GitHub Pages from the repository root. To preview locally, open `index.html` in a browser or run `python3 -m http.server` in the repo root.

## Source material for page content

The authoritative source for all on-page copy (abstract, method description, task list, numbers) lives in `paper/` (gitignored — local only):

- `introduction.tex` — pitch, contribution framing, headline result.
- `method.tex` — three pillars to surface visually: (1) sparse-reward distributional **value expert**, (2) **TRFO** objective (positive-advantage attract / negative-advantage repulse, trust-region bounded by frozen reference), (3) **Temporal Inter-chunk Blending** at deployment, all wrapped in the iterative collect→label→train loop.
- `experiment.tex` — four eval tasks: **Laundry** (T-shirt folding, items/h), **Zip Tie**, **Paper Box**, **Sachet**. Some numbers are still `\todo{}` placeholders — leave a clear hook in the page (don't fabricate numbers).
- `result_fig{1,2,3}.pdf` — figures to lift into the page (export to SVG/PNG when used; do not embed PDFs directly).

Videos for each task are **planned but not yet produced** — scaffold the page with placeholder slots (e.g. captioned empty `<video>` tags or poster-only frames) so they can be dropped in later without layout reflow.

## Design direction

Reference aesthetic: pi.website, Figure's Helix page, Apple product pages. The user's exact phrasing: *"页面像一张排好版的纸"* (the page should feel like a typeset sheet of paper) — simple, but every detail premium. Concretely:

- Generous whitespace, restrained palette, a single confident typographic system. No stock-template gradients, no generic SaaS hero.
- The **system/method diagram is the centerpiece** — treat it like Figure's Helix System-1/System-2 schematic: labeled boxes, dashed signal paths, frequency annotations, subtle motion. It should communicate the iterative loop (deploy → collect rollouts + corrections → value-expert label → TRFO update → redeploy) at a glance.
- Animations should feel mechanical and precise, not decorative. Prefer CSS/SVG over heavy JS libraries.

When making frontend changes, invoke the `frontend-design` skill — that is the user's installed plugin for this kind of work.

## Conventions

- `paper/` is gitignored; never commit anything from it (figures must be re-exported into a tracked assets dir before committing).
- Keep the page a **single self-contained `index.html`** for as long as possible — only split into multiple files when complexity actually demands it.
