# skills

Agent skills I write. Each one lives in `skills/<name>/SKILL.md`.

| Skill | What it does |
|---|---|
| `design-studio` | Runs Impeccable as the lead for premium website and interface work, and calls the taste skills and Emil Kowalski's motion skills at fixed points. |

## Install

`design-studio` calls other people's skills, so install those too:

```bash
npx skills add chrvsd/skills
npx impeccable install
npx skills add Leonxlnx/taste-skill
npx skills add emilkowalski/skill
npx skills add higgsfield-ai/skills   # optional: image generation, uses Higgsfield credits
```

Install Impeccable with `npx impeccable install`, not `npx skills add`. Only its own installer adds the `impeccable-*` agents that `design-studio` uses.

To update later:

```bash
npx skills update -g
npx impeccable update
```

Restart your agent after an install or update.

## Edit on this machine

`~/.claude/skills/design-studio` is a symlink to `skills/design-studio` in this clone, so an edit here is live at once. Commit it on a branch like any other change.
