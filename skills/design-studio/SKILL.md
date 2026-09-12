---
name: design-studio
description: Use when the user wants a whole website, landing page, app screen or interface designed, redesigned or refined to a premium, high-polish bar, or asks to use Impeccable together with the taste skills and Emil Kowalski's motion skills. Not for a single narrow tweak, which Impeccable handles alone.
---

# Design Studio

## Overview

`impeccable` leads every job. The taste skills and Emil Kowalski's skills are specialists called at fixed points. Load each skill at the step named below; never load them all up front.

Repo process (branching, plans, verification gates) still applies. If `superpowers:brainstorming` runs first, keep it to scope and constraints and pass its answers to impeccable, so impeccable does not ask them again.

Impeccable's modes, by what the visitor does: Persuade (landing, marketing, pricing), Operate (app UI, dashboards, tools), Read (docs, articles), Experience (portfolios, showcases).

## Who wins a conflict

The higher rule wins. Report each conflict you resolved in one line at the end.

1. The user's explicit brief.
2. Project rules: CLAUDE.md files, PRODUCT.md, DESIGN.md, design tokens, shared components, existing interaction contracts.
3. `impeccable`: mode, direction contract, craft floor, finish.
4. Emil's skills, for motion detail.
5. Taste skills, for anti-slop checks and a named style.

When the brief asks for something a written project rule forbids (for example, DESIGN.md says a page never moves), ask the user before overriding that rule.

## Start

1. Invoke `impeccable` with the user's request. Its setup and routing decide the mode, and whether this is new work (a new surface or a replacement world) or a refinement of the incumbent look.
2. State the flow in one line: A for new work, B for refinement, C for motion only.

### A. New work or redesign

1. Follow impeccable in this order: direction, then any style pack, then `brandkit` if a logo is in scope (stop while the user picks a mark), then comps (stop while the user picks one), then the build.
2. Before you carry out the section "7. Inspect and finish" in impeccable's `reference/new-work.md`, do these, so its finish review and DESIGN.md include them:
   - Taste check: `design-taste-frontend` for new work, `redesign-existing-projects` for a redesign. Use it as a checklist against the build, never as the builder. Fix the hits that keep the direction contract.
   - The motion steps below.
3. Then carry out section 7 as written, including the `impeccable-finish-reviewer` and `impeccable-documenter` agents. Add no extra polish loops. If DESIGN.md also governs surfaces outside this job, tell the documenter to change only this surface's section.

### B. Refine an existing surface

1. Run impeccable's `critique` command on the target.
2. Persuade or Experience surface only: `redesign-existing-projects` as a second audit lens. Findings only.
3. Fix each finding with the impeccable command that owns it (`layout`, `typeset`, `colorize`, `clarify`, `harden`, and so on).
4. The motion steps below.
5. Impeccable's `audit` command, then its `polish` command, once each.
6. If the work added a reusable token or motion pattern, edit the matching DESIGN.md section. Never regenerate the file.

### C. Motion only

- One piece of motion: `animate`, then the motion review.
- Whole codebase: `improve-animations` (it writes plans), then `animate` per plan item, then the motion review.

### Motion steps

1. `find-animation-opportunities` on the target.
2. `animate` for each item in its Opportunities table, within the motion volume rule in Known conflicts. Its rejected list stays rejected.
3. Motion review: invoke `emil-design-eng` with a concrete request, for example "Review the motion in <files>. Use your Before/After table." With no request it only prints a greeting. Fix what it finds.

## Add-ons

Load an add-on only when its trigger is true, at the step shown.

| Trigger | Skill | When |
|---|---|---|
| The brief uses a style word (see Style packs) | That ONE style pack | After direction is pinned, before the build |
| Gestures, drag, sheets, springs, or "feel like Apple" | `apple-design`. On a Persuade surface, ask at the start whether "Apple" means interface feel (`apple-design`) or apple.com scroll storytelling (`gpt-taste`, which then loads as the style pack and counts as asking for more motion). | `apple-design`: before the motion steps |
| The brief asks for a logo or brand identity. If the product has none, ask whether to make one. | `brandkit` for concept boards. The boards are raster, so redraw the chosen mark by hand as SVG in code. | After any style pack, before comps |
| A chart, graph or stat display | `dataviz` | When you build it |
| Toasts built with Sonner | `ask-sonner` | When you build them |
| The user describes motion but lacks the word | `animation-vocabulary` | When it comes up |
| A React Native or Expo app | `animate-expo` in place of `animate` | Motion steps |

### Style packs

Quality words (premium, beautiful, polished, high-end, expensive) set the bar. They name no style, so they load no pack. "Great animations" raises the motion bar; it does not ask for more motion. Style words do load a pack:

- `minimalist-ui`: minimal, editorial, calm, warm monochrome.
- `industrial-brutalist-ui`: brutalist, blueprint, Swiss, terminal, telemetry.
- `high-end-visual-design`: agency, Awwwards, luxury.
- `gpt-taste`: GSAP, scroll-pinned or scroll-driven storytelling.

Load a pack only on a Persuade or Experience surface. It adds detail to the pinned style; impeccable still owns direction.

## Images

Impeccable runs its comp and asset steps whenever image generation exists. In Claude Code that usually means Higgsfield: invoke `higgsfield-generate` and follow it. It costs credits. Higgsfield counts as image generation for impeccable, even when impeccable's setup names no image tool.

Ask once, before the first image, and name what you will generate (comps, assets, logo boards). Ask even when the brief asks for images, because comps add images the brief did not name. With a yes, impeccable's comps and assets and `brandkit` use Higgsfield. With a no, impeccable continues without images.

Make every image call from the main thread, where the credit approval lives. Subagents such as `impeccable-asset-producer` may process images that already exist, but do not generate new ones.

## Dependencies

Add a dependency only with the user's OK. A brief that already grants it ("use whatever is best") counts. For motion, `animate` picks the tool, and a new motion library still needs that OK. For other libraries (charts, toasts, command menus, virtualization), offer `/pick-ui-library <need>`.

## User-only skills

`prototype`, `review-animations` and `pick-ui-library` are blocked from the Skill tool. Do not imitate their workflow. Give the user the exact command instead:

- The user wants to compare versions. With image generation, impeccable's three comps compare layouts. Without it, or for one component in live code, stop and hand over `/prototype <component>`. Continue after the user picks.
- A strict motion gate: `/review-animations`. It is optional. Do not stop for it; list it in the finish report.
- A non-motion library choice: `/pick-ui-library <need>`, as above.

## Never in this flow

- `stitch-design-taste`: it writes its own DESIGN.md, and impeccable's documenter owns that file. Use it only when the user targets Google Stitch.
- `imagegen-frontend-web`, `image-to-code`, `imagegen-frontend-mobile`: they duplicate impeccable's comp step.
- `design-taste-frontend-v1` (superseded), `full-output-enforcement` (not a design step), `write-swift`.
- Impeccable's `animate` command: Emil's `animate` is the one motion author per job.

## Known conflicts

| Topic | Clash | Winner |
|---|---|---|
| Button press | Emil: `scale(0.97)` on `:active` | The project's press rule, if one exists |
| Stack | `design-taste-frontend` defaults to Tailwind v4, Motion, Phosphor | The project's stack and icon family, or impeccable's choice in an empty project. The checklist never adds a dependency. |
| DESIGN.md | `stitch-design-taste` writes one | `impeccable-documenter` |
| Motion volume | `gpt-taste`, `high-end-visual-design`: scroll choreography, magnetic hover, constant motion | Operate and Read: Emil's frequency gate. Persuade: one focal sequence, unless the brief asks for more motion. Press, hover and state feedback do not count toward it. |

## Common mistakes

- Letting a taste skill build the page. It checks; impeccable builds.
- Skipping the motion review because the motion "looks fine".
- In flow A, adding motion after impeccable's section 7, so the reviewer and DESIGN.md never see it.
- Reading a quality word as a style word, and loading a style pack nobody asked for.

## Finish report

List the skills that ran, the skills skipped and why, the conflicts resolved, and the user-only commands still worth running.
