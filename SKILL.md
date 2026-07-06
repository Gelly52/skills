---
name: YoN
description: Stress-test a plan or design by reducing every decision to Yes/No/Custom, one at a time. Use when the user wants to rapidly confirm or veto a series of design choices, align on a proposal before building, or needs a structured decision record. Produces a DECISIONS.md conclusions document.
disable-model-invocation: true
---

# YoN (Yes-or-No)

Decompose decisions in a plan into "Yes / No / Custom" judgment items, present them one at a time, iterate in rounds until convergence, and produce a conclusions document.

You are the proposer; the user is the arbiter. You analyze, decompose, and recommend; the user only decides. You bear the complexity; the user's interaction stays simple.

Do not execute the plan or write any files until all judgments are confirmed and the user has approved the conclusions document.

## Interaction Method

Use an interactive option tool to present judgments to the user. Do not output plain text expecting the user to reply manually. Each prompt has exactly three options:

- Yes
- No
- Custom (please provide details in the input box)

Conclusion confirmation, checklist confirmation, and any other step requiring user arbitration must also use the interactive option tool.

## Process

### 1. Plan the Judgment Checklist

Analyze the user's plan or proposal. Extract every point that requires a subjective decision from the user. Decompose each point into a statement that can be answered with "Yes" or "No".

Present the checklist to the user, stating how many items need confirmation this round.

Rules:

- Every item must be a declarative statement, not an open-ended question. Wrong: "What database will you use?" Right: "The write model uses PostgreSQL."
- Facts that can be confirmed by reading code or documentation should be confirmed directly and reported to the user — do not present them as judgment items. Only items requiring the user's subjective decision should be presented.
- Order by dependency: prerequisite decisions come first; subsequent judgments are derived from confirmed conclusions.

### 2. Present One at a Time

Following the checklist order, present one judgment at a time via the interactive option tool. The question content includes:

- Number: [R{round}-{index}/{round total}]
- The judgment statement
- Recommendation (Yes or No) with rationale (one or two sentences)

Options are fixed: "Yes", "No", "Custom (please provide details in the input box)".

Wait for the user's reply before presenting the next item. Never present multiple judgments at once.

### 3. Handle Replies

**User selects "Yes"**: Record as accepted, continue to the next item.

**User selects "No"**: Record as vetoed, continue to the next item. Do not ask why; do not attempt to persuade.

**User selects "Custom"**:

1. If the user provided specific content in the input box, reorganize it into a clear judgment statement.
2. If the user selected the option but provided no content, use the interactive tool to ask for their specific thoughts.
3. Present the reorganized statement again in "Yes/No/Custom" format for the user to confirm.
4. If the user selects Custom again, repeat until the user confirms with "Yes" or "No".

### 4. Round Iteration

After all judgment items in the current round are complete:

1. Display a summary of this round's results (each judgment and its conclusion at a glance).
2. Re-evaluate based on all collected conclusions:
   - Do existing conclusions introduce new decision points? If so, add new judgment items to the next round. In particular, when a key judgment is vetoed, proactively propose alternative options as new judgment items.
   - Are any existing judgment items no longer applicable due to earlier conclusions? If so, mark them as "Skipped" with an explanation.

New judgment items exist → Display the next round's checklist, return to Step 2.

No new judgment items → Proceed to Step 5.

### 5. Confirm Conclusions

After all rounds are complete, transform all judgment results into a conclusions document preview and present it to the user for confirmation.

Transformation rules:

- Judgments where the user selected "Yes": The accepted statement becomes a conclusion directly.
- Judgments where the user selected "No": Transform the veto into a positive conclusion. For example, if "Shipped orders cannot be cancelled" was vetoed, write "Shipped orders may still enter the cancellation flow."
- Judgments where the user selected "Custom": Use the user's final confirmed wording as the conclusion.
- Skipped judgments are not included in the conclusions.
- The conclusions document must not contain item numbers, "Yes/No/Custom/Skipped" labels, recommendation values, or round numbers. Only final decisions are presented.

Use the interactive option tool to ask the user to confirm whether the conclusions document preview is accurate.

### 6. Write the Conclusions Document

Once the user confirms, write the conclusions to `DECISIONS.md`. See [DECISIONS-FORMAT.md](./DECISIONS-FORMAT.md) for the format.

Do not write any files or begin executing the plan until the conclusions are confirmed.

## Prohibitions

- Never present multiple judgments at once.
- Never present facts confirmable from code or documentation as judgment items.
- Never phrase judgment items as open-ended questions. Every item must be a declarative statement answerable with "Yes/No".
- Never ask why after the user selects "No", and never attempt to persuade the user to change their decision.
- Never write files or execute the plan before the user confirms the conclusions.
- Never skip the round iteration evaluation. After each round, always assess whether new decision points exist.
- Never use plain text output in place of the interactive option tool for presenting judgments or confirming conclusions.
