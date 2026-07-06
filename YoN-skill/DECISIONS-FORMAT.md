# DECISIONS.md Format

Conclusions document produced by a YoN session. Records only final conclusions, not the judgment process.

## Template

```md
# {Session Title}

{One sentence describing the plan or design being decided.}

Date: {YYYY-MM-DD}

## Conclusions

**{Conclusion statement}**
{One or two sentences of context or rationale when helpful.}

**{Conclusion statement}**
{One or two sentences of context or rationale when helpful.}
```

The conclusions document can be short. The value is in recording *what was decided* — not in filling out a template.

## Writing Rules

- Every conclusion is a clear **positive statement** describing "what was decided", not "what was rejected".
- Judgments where the user selected "Yes": The accepted statement is written directly as a conclusion.
- Judgments where the user selected "No": Transform the veto into a positive conclusion. For example, if "Shipped orders cannot be cancelled" was vetoed, write "Shipped orders may still enter the cancellation flow."
- Judgments where the user selected "Custom": Use the user's final confirmed wording as the conclusion.
- Skipped judgments are not included.
- No item numbers, no "Yes/No/Custom/Skipped" labels, no recommendation values, no round numbers. The conclusions document presents only final decisions.
- If conclusions naturally group into multiple topics, use subheadings. If all conclusions belong to a single topic, a flat list is fine.

## Optional Sections

Include only when they add genuine value. Most sessions won't need them.

- **Exclusions** — When certain vetoed directions are worth noting for future readers, a brief paragraph stating "we explicitly chose not to do X". No need to list every vetoed item — only those truly worth recording.
- **Open Items** — Decision points that could not be confirmed now and need revisiting later.

## File Location

- Default: project root directory. If the user specifies another location, follow that.
- If a `DECISIONS.md` already exists, append the new session as a new section (separated by `---`), do not overwrite existing content.
