---
name: ask-again
description: Re-ask every question still open in this session, each with enough context that the user can answer without scrolling back, and sketch the complex ones. Use on request — "/ask-again", "re-ask", "what did you ask me", "what do you need from me". Read-only — no writes, no commands. Not for tracking every live thread (that is thread-tracker).
---

# ask-again

**A question asked twenty messages ago is a question lost.** The user has to scroll back, find it, and rebuild what it was about. This skill brings every open one back to the bottom of the screen, ready to answer.

## 1. Find the open questions

Sweep the whole session, not just the last reply.

- **Your own questions** that got no answer, or only half an answer.
- **Choices you parked** — "we can do A or B, your call", an unresolved-questions list at the end of a plan.
- **Questions a skill or subagent raised** that you passed on and nobody settled.
- ⛔ **Not answered ones.** If the user answered, even in passing, it is closed. If you are unsure, list it and say what they said.
- ⛔ **Not questions you can answer yourself** from the code, the docs or a sensible default. Answer those instead, in one line each under "Settled myself".

**None open → say so in one line** and stop.

## 2. Re-ask each one

Number them. Each one stands alone — the user should not need the scrollback or another question to answer it.

```
### 1. <the question, one line>

**Context:** what this is about and why it came up — two or three short sentences. Name the file, screen or term it touches.
**Options:**
- **A — <name>** (recommended): what happens if they pick it.
- **B — <name>**: what happens if they pick it.
**Blocks:** what waits on the answer, or "nothing yet".
```

1. **Lead with your recommendation** when you have one, and say why in a clause.
2. **Use the project's own terms** — its `CONTEXT.md` or `GLOSSARY.md` where one exists.
3. **Keep paths and names exact.** Do not paraphrase an identifier.
4. **An open-ended question gets no options**, just the context and what a good answer covers.
5. **Most important first** — the one that blocks the most work goes at the top.

## 3. Sketch the complex ones

A question is complex when its options differ in shape — a flow, a data model, a layout, a call tree, before and after — and prose would make the user hold it in their head.

**For those, read [`show-me.md`](show-me.md) beside this file and apply it**: the smallest view that makes the difference plain, inside that question's block, under its options.

- One sketch per complex question, not one for the whole list.
- ⛔ Do not draw a simple yes/no or a naming choice.

## 4. End with the short form

Close with one line the user can reply to fast:

```
Reply like: 1A, 2B, 3 "<your words>"
```

## Traps

1. ⛔ **Do not act while asking.** This skill re-asks; the work resumes after they answer.
2. ⛔ **Do not invent new questions** to fill the list. Only ones already open in this session.
3. ⛔ **Do not use a multiple-choice modal** (such as AskUserQuestion). Ask inline, so the user can still type.
4. If `thread-tracker` is running, its block goes after this one.
