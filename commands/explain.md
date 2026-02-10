---
description: Explain a file, error, concept, or piece of output in plain language. Point it at anything you do not understand. Use when you need a quick explanation, not a full review.
argument-hint: [file path, error message, or concept]
---

# /clarity:explain

Explain one thing in plain language.

## Purpose

This is the quick version of Clarity. No full review, no saved file, no structure. The user points at something and gets an explanation they can understand.

## What it accepts

- **No argument (most common)** — explain Claude's most recent response. What did it just do? What files did it touch? What does it mean? This is the default and most frequent use.
- **A file path** — explain what this file does, how it fits into the project, and anything worth knowing about it
- **An error message** — explain what went wrong, why, and what to do about it (in terms of what to ask Claude, not how to fix it yourself)
- **A terminal output** — explain what just happened and whether it is good, bad, or neutral
- **A plan** — explain what Claude is proposing to do, what it means for the project, and what to consider before approving
- **A concept or term** — explain it in plain language with a concrete example from the current project if possible
- **A piece of code shown in the session** — explain what it does and why it matters

## Behaviour

### Step 1: Identify the target

Determine what the user wants explained:

1. If no argument is given, explain Claude's most recent response. Check whether that response was a plan (use plan format), an error (use error format), or general work (use last-response format).
2. If a file path is provided, read the file and use the file format.
3. If an error message or terminal output is quoted, use the error or terminal output format.
4. If a concept or term is provided, use the concept format.
5. If it is genuinely unclear what the user wants explained, ask: "What would you like me to explain?"

### Step 2: Explain it

Follow the review-methodology skill for language and tone. Follow the explanation-frameworks skill for all technical translations.

The explanation must:

- Be understandable by someone who has never programmed
- Start with what the thing IS or DOES (one sentence)
- Then explain why it matters in the context of this project
- Then flag anything the user should know (risks, gotchas, important context)
- Define every technical term inline
- Be concise — this is a quick explanation, not a report

For **Claude's last response** (the default when no argument is given), cover:
- What Claude just did — in one or two sentences, plain language
- What files were created, changed, or deleted, and what each change means
- Whether any new dependencies or external services were introduced
- Whether anything risky or worth questioning happened
- If Claude made choices (picked a library, chose an approach, structured something a particular way), briefly note what was chosen and whether it is easy to change later
- Keep it focused on the last response only, not the whole session. If the user wants the full picture, suggest `/clarity:session`.

For **files**, cover:
- What the file does (one sentence)
- How it fits into the project (its role)
- What depends on it / what it depends on
- Anything noteworthy (security-relevant, recently changed, unusually complex)

For **errors**, cover:
- What went wrong (in plain language)
- Why it happened (the cause, not the stack trace)
- How serious it is (will it cause further problems, or is it a one-off?)
- What to do next (a paste-ready prompt for Claude to fix it)

For **terminal output**, cover:
- What just happened (success, failure, warning)
- Whether it requires action
- If it is a build or test result, what passed and what did not

For **plans** (implementation plans, proposed changes, architecture proposals), cover:
- What is being proposed, in plain language — what will be different after this plan is carried out?
- What files or parts of the project will be created or changed
- What new dependencies or services will be introduced, if any
- What the plan commits you to — is this easy to reverse, or does it set a direction that is hard to change later?
- What the risks are if the plan has gaps or makes wrong assumptions
- Questions to ask before approving — specific things the user should confirm or challenge before saying yes. Frame these as plain questions, not technical review items.

Plans are decision points. The user needs to understand what they are agreeing to. Be direct about anything that looks like a significant commitment, an assumption that has not been validated, or a choice with non-obvious consequences.

For **concepts**, cover:
- What it means (one sentence, no jargon)
- Why it matters for this project specifically
- A concrete example from the current project if possible

### Step 3: Offer more

After the explanation, ask briefly:

> Want me to go deeper, or is that clear?

If the user asks for more, provide additional detail following the same language rules.

## Output rules

- Print the explanation directly in the terminal
- Do NOT save a file — this is quick and informal
- Do NOT produce a full review structure (no headers, no jargon buster, no "Worth Understanding")
- Keep it short — aim for a few paragraphs, not a page
- Use the language rules from the review-methodology skill throughout

## What this is not

- Not a full session review — use `/clarity:session` for that
- Not a full project review — use `/clarity:project` for that
- Not a fixer — if the user needs something fixed, suggest a prompt for a new session
