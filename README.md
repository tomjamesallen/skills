# skills

Standalone agent skills. Each directory carries everything it needs.

| Skill | What it does |
| --- | --- |
| [`thread-tracker`](skills/thread-tracker/SKILL.md) | Ends each reply with a lettered table of the live threads once a session forks into three or more |
| [`ask-again`](skills/ask-again/SKILL.md) | Re-asks every open question in the session, each with its context, ready to answer |

## Credits

`skills/ask-again/show-me.md` is HumanLayer's [`show-me`](https://github.com/humanlayer/skills/tree/main/plugins/show-me/skills/show-me) skill, copied unchanged under the MIT License (`skills/ask-again/show-me.LICENSE`).

## Install

```bash
npx skills add tomjamesallen/skills
```

Or copy one directory into `~/.claude/skills/` (every project) or `.claude/skills/` (one project). Keep the directory name: it must match the `name` in the frontmatter.
