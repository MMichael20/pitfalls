# Pitfalls

Mistakes made on this project, recorded so they are not repeated by a session that has no memory of
them. Each entry is a real incident, not a guideline.

This file is empty until the first mistake. That is the intended starting state — entries are
earned, never invented.

## How this file is written

**Record before you fix.** The entry is written at the moment of discovery, before the correction.
The fix is the cheap half; the reasoning that produced the mistake is the half that will produce the
next one, and it is only recoverable in the moment before the correct version exists. Afterwards the
wrong path stops looking plausible and cannot be reconstructed.

**Append only. Never renumber.** Entries are cited by number from other files. A tidy-up that
renumbers them silently breaks every cross-reference in the project.

**Every entry fills the seven fields in `PITFALL-TEMPLATE.md`.** The rationalization field is not
optional; it is the field that does the work.

### On the rationalization field

Record the reasoning that made the mistake feel correct **at the time**, in the first person, in the
tense of someone who still believes it.

Not this — hindsight wearing the costume of a cause:

> *I failed to consider the second code path.*

But this — the argument as it actually ran:

> *The change is small and I can see it is correct by reading it; running the full check costs
> minutes for something already verified.*

The second one is useful because it is still persuasive. That is the point: a rationalization is
usually a sound-looking argument in which every clause is true and the conclusion is wrong. The next
occurrence will not feel like a mistake either — it will feel like that same reasonable argument. A
rule recorded without the argument it must defeat gets argued around again.

### What belongs here

An incident with a decision behind it. The bar: *would a competent agent, acting in good faith, make
this mistake again next month?*

Not here: facts about how a system behaves (knowledge), preferences about how to work
(configuration), errors with no reasoning behind them (typos, transient failures), or anything a
test, type, or lint rule could catch instead — add the check, it is a better enforcement site than a
paragraph.

## Index

Add one imperative line per entry. This is the part read at the start of a session; a rule that is
not here does not fire.

_(empty)_

---

_(entries begin below)_
