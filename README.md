# Skills

Agent skills for real-world engineering workflows. Small, composable, opinionated.

These skills work with any AI coding agent that supports the [skills protocol](https://github.com/mattpocock/skills) — Claude Code, Cursor, Codex, Gemini CLI, and others.

## Quickstart

```bash
npx skills add Gelly52/skills
```

Pick your skills and agents from the interactive prompt. Or install a specific one:

```bash
npx skills add Gelly52/skills --skill=YoN
```

Update installed skills:

```bash
npx skills update YoN
```

## Philosophy

- **User stays in control.** The agent proposes, you decide. No auto-pilot.
- **Small and composable.** Each skill does one thing well. Combine them as needed.
- **Produces artifacts.** Sessions leave behind useful documents, not just conversation.
- **Works with any model.** No vendor lock-in.

## Skills

| Skill | Type | Description |
|-------|------|-------------|
| [YoN](./YoN/) | User-invoked | Stress-test a plan or design by reducing every decision to Yes/No/Custom, one at a time. Iterates in rounds until convergence. Produces a `DECISIONS.md` conclusions document. |

> More skills coming. This table will grow.

## How skills work

Skills split on **who can invoke them**:

- **User-invoked** — You type the command (e.g. `/YoN`). The agent won't reach for it on its own.
- **Model-invoked** — The agent activates it automatically when the task fits.

A user-invoked skill may call model-invoked skills, but never another user-invoked one.
