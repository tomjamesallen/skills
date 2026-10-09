---
name: thread-tracker
description: Print a compact thread-tracker block when a session has grown several open lines at once — one lettered row per live thread, which one is on now, which are waiting on the user, and what unblocks each parked one. Invoke it YOURSELF, unprompted, as soon as a conversation has forked into three or more things the user has to hold in their head, or a question you asked has gone unanswered while a side-question ran; then keep the block at the end of every reply until the threads collapse. Also invoke on request — "what is outstanding", "where were we", "track these threads", or /thread-tracker. Lightweight and read-only — no tools, no writes, no files.
---

# thread-tracker

**The problem it solves: a long session forks faster than a person can hold it.** A question opens a side-question, the side-question turns out to be blocked on something else, and four exchanges later the user has silently dropped the thing they actually asked about. **Nothing in the transcript flags that**, because every individual reply looked complete.

**The fix is small: end each reply with a block naming every live thread and its state.** The user reads five lines instead of scrolling back. It costs a few lines per turn, and it needs nothing installed.

**Read-only, and needs nothing.** No tools, no file reads, no commands. It is a rendering of what is already in context.

## Two ways in, and the first is the one that matters

**1. You invoke it yourself, unprompted.** That is the design. The user should not have to notice they are losing track — **by the time they notice, the thread is already dropped.** Watch for the trigger below and start the block without being asked.

**2. `/thread-tracker`, by hand**, when the trigger did not fire. ⚠ **A manual invocation is a signal you missed one** — start the block, and do not defend the miss.

## When to start

**At the THIRD live thread.** Two is a conversation; the block is noise. Four or more and the drop has usually already happened.

Also start whenever the user asks what is open, what is outstanding, where were we, or what else is there.

## When to stop

When one thread is left, or the user says to stop. **Say that you are stopping** — a block that simply disappears reads like an error.

## What counts as a thread

**A question or line of work the USER has to come back to.**

The test: *if this session ended right now, would something be left unanswered or unbuilt that nobody has written down?*

- ✅ An open question you put to them and they have not answered.
- ✅ A decision that is ruled but not yet applied.
- ✅ Something parked on an external blocker.
- ✅ A side-question they raised that pulled the conversation off the main line.
- ⛔ **A step in the task you are doing right now.** That is your work, not a thread.
- ⛔ A fact you looked up. That is an answer, not a thread.

## The block

```
🧵 Threads

| | Thread | State |
|---|---|---|
| **A** | <five words> | 👈 **on now** |
| **B** | <five words> | ⏳ waiting on you — <the question, in one line> |
| **C** | <five words> | ⏸ parked — <what unblocks it> |
| **D** | <five words> | ✅ ruled |
```

Put it at the **end** of the reply, after the substance. It is a footer, not a heading.

## Rules that make it work

1. ⭐⭐ **A letter is permanent for the session.** Thread B stays B even when A closes. **Renumbering destroys the block's whole value** — the user is tracking letters across turns, and a row that changes identity is worse than no row.
2. **One line per thread.** If it needs a paragraph it is not a thread, it is a document.
3. ⭐ **Every parked thread names what unblocks it.** *"Parked"* on its own is a dropped thread wearing a badge.
4. **A ruled thread shows once more, then drops.** Otherwise the block only ever grows.
5. **Cap it at about seven.** Past that, say plainly that the session is carrying too much and offer to split it or hand part of it off.
6. **Do not re-sort by priority each turn.** Stable letters, stable order. The user is reading positionally.

## The traps

1. ⛔⛔ **Never mark a thread ✅ that the user has not actually ruled.** Agreement is not evidence, and neither is silence: a question that was asked, went unanswered, and is then shown as settled **vanishes for good**, and it looks deliberate. If you are unsure, it is ⏳.
2. ⛔ **The block is not a to-do list.** A to-do is work you do next. A thread is something the user owns. Mixing the two makes a long list that nobody can act on.
3. ⛔ **Do not invent threads to fill the table.** Three real ones beat seven padded.
4. ⛔ **The block does not replace writing things down.** It is ephemeral and dies with the context. **A ruling belongs in the PRD, the issue or the doc it governs**, and the block is a pointer to work still owed, never the record of it.
5. ⚠ **Do not restate the substance in the block.** One row per thread, five words. The detail is in the reply above it, or in the file the ruling landed in.
