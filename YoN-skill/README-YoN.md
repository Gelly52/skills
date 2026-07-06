# YoN (Yes-or-No)

Stress-test a plan or design by reducing every decision to **Yes / No / Custom** — one judgment at a time.

## Install

```bash
npx skills add Gelly52/skills --skill=YoN
```

```bash
npx skills update YoN
```

[Source](https://github.com/Gelly52/skills/tree/main/skills/YoN)

## What it does

YoN interviews you about a plan the same way a code review forces you to justify each line — except the only answers it accepts are Yes, No, or a custom alternative. It decomposes your proposal into atomic decision points, presents them one at a time with a recommended verdict, and iterates in rounds until no new decisions remain. The output is a clean `DECISIONS.md` that records only what was decided, not how you got there.

## When to reach for it

Invoke `/YoN` when a plan feels roughly shaped but you want every implicit assumption surfaced and stamped before you build. It is the right fit when:

- You have a proposal and need to **confirm or veto** each part quickly.
- You want a **structured decision record** without writing one by hand.
- The plan is clear enough that decisions can be framed as Yes/No — if it's still too fuzzy, use [grill-me](https://github.com/mattpocock/skills) to explore first, then come back to YoN to lock things down.

## How it differs from grill-me

|               | grill-me                 | YoN                           |
| ------------- | ------------------------ | ----------------------------- |
| Answer format | Open-ended               | Yes / No / Custom             |
| Pace          | Deep exploration         | Rapid confirmation            |
| Output        | Nothing (stateless)      | `DECISIONS.md`                |
| AI role       | Challenger — finds holes | Proposer — offers verdicts    |
| Best for      | Fuzzy plans              | Shaped plans needing sign-off |

## The session

1. **Checklist** — The agent analyzes your plan and presents a numbered list of judgment items for the round.
2. **One at a time** — Each item appears via an interactive prompt with three options. No batch questions.
3. **Rounds** — After a full pass, the agent evaluates whether earlier answers opened new decision points. If so, a new round begins. This repeats until convergence.
4. **Conclusions** — A preview of the final document is shown for approval before anything is written.

## It's working if

- You never see more than one question at a time.
- Every prompt has exactly three clickable options — no free-text reply expected.
- Saying "No" is respected immediately with no follow-up.
- The conclusions document contains only positive statements of what was decided — no trace of the Yes/No process.

## Where it fits

YoN is a **pre-build alignment tool** — the step between "I have a plan" and "start coding." It pairs naturally with grilling skills: run `/grill-me` to explore and shape the plan, then run `/YoN` to lock each decision down with a paper trail. Downstream, the `DECISIONS.md` it produces feeds cleanly into PRD writing, ticket creation, or implementation planning.
