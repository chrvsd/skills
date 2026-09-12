# skills

Agent skills I write. Each one lives in `skills/<name>/SKILL.md`.

| Skill | What it does |
|---|---|
| `design-studio` | Runs Impeccable as the lead for premium website and interface work, and calls the taste skills and Emil Kowalski's motion skills at fixed points. |

## Install on another machine

```bash
npx skills add chrvsd/skills
```

The repository is private, so the machine needs GitHub access to `chrvsd/skills`.

## Edit on this machine

`~/.claude/skills/design-studio` is a symlink to `skills/design-studio` in this clone, so an edit here is live at once. Commit it on a branch like any other change.

`design-studio` expects its companion skills to be installed: `impeccable`, `Leonxlnx/taste-skill`, `emilkowalski/skill`, and `higgsfield-ai/skills` for images.
