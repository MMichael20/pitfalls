---
name: pitfalls
description: Use the moment a mistake is discovered — one you notice yourself, or one someone points out. Applies when you find a defect in code you wrote, a test fails on something you asserted was correct, a review turns up your own flawed work, new evidence contradicts an earlier claim or verdict, you catch yourself about to repeat a known mistake, or a user corrects you. Record the mistake and the reasoning that produced it BEFORE fixing anything, then fix. Also use to bootstrap the pitfalls system in a project that does not have one.
---

# Pitfalls

## The rule

**When you discover a mistake, record it before you fix it.**

That ordering is the entire skill. Everything below explains why it matters and how to do it, but if
only one sentence survives, it is that one.

## The reflex this replaces

Something wrong surfaces. The standard response:

> "You're right, sorry — I misread the schema there. Let me fix it."

...followed immediately by the fix. It reads as accountability. It is not. It is the fastest
possible route to destroying the only part of the incident that had lasting value.

The fix is the cheap half. Almost anyone can fix a mistake once it has been pointed out. **The
reasoning that produced the mistake is the expensive half — and it is the half that will produce
the next one.** That reasoning is recoverable for roughly one moment: right after discovery, before
the fix. Once the correct version exists, the wrong version stops feeling like a plausible path and
becomes obviously wrong in hindsight. It cannot be reconstructed later. It is gone.

So the response is not an apology followed by a fix. It is:

1. **State what you did.** Flatly, no apology. "The address field was verified on the create form
   and never on the edit form."
2. **State why it looked correct at the time.** The actual reasoning, first person, as it ran — not
   a diagnosis written after you already know the answer.
3. **Record it** — full entry, index line, enforcement site (below).
4. **Then fix.**

Steps 1-3 cost a couple of minutes. Skipping them costs the same mistake again in six weeks, in a
session that has no memory of this one.

**Do not apologize.** Not because apologies are wrong, but because they occupy the exact slot where
the reasoning belongs, and they feel like they discharge the obligation. "Sorry, my mistake" closes
the incident emotionally while leaving it open operationally. State the failure, state the cause,
record it, move on.

## When this fires

### Self-detected — the primary case

You do not need to be told. Fire this the moment any of these happen:

- You re-read your own code or output and find a defect in it.
- A test fails on something you wrote and asserted was correct.
- You are reviewing code and the flawed code turns out to be yours.
- New evidence contradicts a claim, verdict, or conclusion you gave earlier in this session.
- You realize a step was skipped, an assumption went unchecked, or a result was asserted rather
  than verified.
- You catch yourself about to do something the pitfalls file already warns against — a near-miss is
  an incident; record why the existing rule did not stop you.
- A task you called finished turns out not to have been.

The strongest signal is an internal one: **the moment you think "actually, that's wrong"** — about
your own work, before anyone else has said anything — that thought is the trigger. Do not let the
next sentence be the fix.

### Externally raised — the secondary case

- Someone corrects a claim, verdict, or conclusion of yours.
- Someone points out something skipped, assumed, or rounded up.
- Someone says: *"did you learn"*, *"remember this"*, *"why didn't you catch this"*, *"add to the
  pitfalls"*, *"we have a rule for this"*, *"this happened before"*.
- A reviewer, teammate, or later run finds something your pass declared clean.

This case is secondary not because it matters less, but because a system that only learns when
prompted is not learning — it is being taught, one correction at a time, by someone who has to
notice every miss personally.

### Not every error is a pitfall

A typo, a transient network failure, a wrong path corrected within the same breath — no decision
behind it, nothing to learn. The bar is: **was there reasoning that felt correct and was not?** If
yes, that reasoning is the artifact. If no, just fix it.

## The checkable rule

> **The closing line of any answer about a mistake must contain a real file path — or the words
> "not written down yet."**

No path and no disclaimer means the lesson was narrated rather than recorded. It is deliberately
mechanical: verifiable by looking at the output, not by trusting the intention behind it. That is
the only kind of rule that survives being inconvenient — and the moment right after a mistake is
always inconvenient.

## Workflow

### Step 0 — Bootstrap (only if the project has no pitfalls file)

Use the first of these that exists:

```
knowledge/pitfalls.md
docs/pitfalls.md
.claude/pitfalls.md
PITFALLS.md
```

If none exists, create `.claude/pitfalls.md` from `templates/pitfalls.md` and add the block from
`templates/CLAUDE-block.md` to the project's always-loaded instruction file (`CLAUDE.md`,
`AGENTS.md`, or equivalent — create it if absent). Say in one line where you put it. Do not stop to
ask permission: an uncaptured lesson is worse than a file in a slightly wrong place, and files move
easily.

### Step 1 — Write the entry, before the fix

Append to the pitfalls file using `templates/PITFALL-TEMPLATE.md`. Next free number. **Never
renumber** — entries are cited by number from other files.

This happens *before* the correction, not after it. If the fix is genuinely urgent — production is
down, a user is blocked — fix first, but write the entry in the same turn, and say plainly that you
inverted the order and why.

### Step 2 — Add the index line

One imperative sentence stating the **rule**, not the story:

```
17. **Diff against the previous state before calling anything a regression.**
```

The index is what gets read at the start of a session. A rule that is not in the index does not
fire.

### Step 3 — Wire the enforcement

Put the rule where the work happens:

| Where the mistake happened | Where the rule goes |
|---|---|
| A step in a documented workflow, skill, or runbook | That step, as a checkable instruction |
| A command sequence or CI pipeline | A hook, a script assertion, or a test |
| A recurring task with no written workflow | Write the workflow — see below |
| Judgment with no natural home | The index, plus a trigger in this skill's description |

**This step is the difference between a rule and a wish.** A rule in a list is consulted when
someone remembers to consult it. A rule wired into step 4 of a procedure fires whether or not
anyone remembers.

If an existing rule *should* have caught this and did not, **that is the finding.** Do not add a
sibling rule beside it — fix why it failed. Was it unfindable, unclear, in the wrong place, too
easy to argue around? A second rule saying the same thing louder is how a rule list becomes noise.

### Step 4 — Sweep for staleness

Changing a rule can invalidate other files. Search the project for the old claim, identifier, or
procedure and fix every occurrence — not just the one in front of you. A future reader follows the
stale line, not your update.

### Step 5 — Now fix the original problem

With the reasoning preserved, correct the actual defect.

### Step 6 — Report

Short. What the mistake was, what produced it, where it is recorded, what you then fixed. The
write-up belongs in the file, not pasted into the reply.

Self-correcting, not self-flagellating: name the failure, name the mechanism that catches it next
time, move on.

## The entry

Seven fields, in `templates/PITFALL-TEMPLATE.md`. Three carry the weight:

**Rule** — one imperative sentence. If it needs two, it is two pitfalls.

**The rationalization** — **the field that makes this system work, and the one that gets skipped.**
The reasoning that made the mistake feel correct, in the first person, as it actually ran. Not
"I failed to consider X" — that is hindsight in the costume of a cause. The real thing usually
looks like a sound argument in which every individual clause is true and the conclusion is wrong.
That is what makes it dangerous: **the next occurrence will not feel like a mistake either. It will
feel like the same reasonable argument.** A rule recorded without the argument it has to defeat
gets argued around again.

Write it while you can still remember believing it. That window closes fast.

**Enforcement** — where the rule now lives so it fires automatically. If this field says "the
index", the rule is weak. Find a better site.

The rest: symptom (recognizable *while it is happening*, not only in hindsight), how to avoid
(mechanical — a command, a count, an ordering; "be more careful" is not an action), why it matters
(the cost, one or two lines, so a future cleanup does not trim it), origin (date, trigger, and any
sharp verbatim quote — quotes age better than paraphrase and make entries findable by memory).

## What does not belong in a pitfalls file

- **Facts** — how a system behaves, where something lives. That is knowledge; different file.
- **Preferences** — how someone likes to be communicated with. That is configuration.
- **Errors with no reasoning behind them** — typos, transient failures.
- **Anything a test, type, or lint rule can catch.** Add the check. It is a strictly better
  enforcement site than a paragraph asking politely.

The bar: *would a competent agent, acting in good faith, make this mistake again next month?*

## Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| Apologize, then fix | Occupies the slot where the reasoning belongs, and feels like it settles the matter |
| Fix first, capture "after" | The fix ships, the task closes, the capture is what gets dropped as cleanup |
| Explain the lesson in chat, write nothing | The insight dies with the context window. This is the failure the skill exists for |
| Record the rule without the rationalization | The next occurrence feels reasonable too, and the rule loses the argument |
| Record without wiring an enforcement site | Depends on someone re-reading the list at exactly the right moment. They will not |
| Add a sibling rule instead of fixing why the existing one did not fire | Rule lists grow, signal drops, everything gets skimmed |
| Wait to be told | A system that only learns when prompted is not learning |
| Renumber entries during a cleanup | Every cross-reference in the project silently breaks |

## When the real finding is a missing workflow

If the mistake happened inside a multi-step process that exists only in someone's head, the pitfall
is a symptom — **the process was never written down.** Write it. A procedure carried out by hand
twice is one that should have been documented after the first time; re-deriving it from memory is
precisely the condition under which steps get dropped.

## Files

| File | Purpose |
|---|---|
| `templates/pitfalls.md` | Seed file — format rules, ready to fill |
| `templates/PITFALL-TEMPLATE.md` | The seven-field entry template |
| `templates/CLAUDE-block.md` | Block to add to a project's always-loaded instruction file |
