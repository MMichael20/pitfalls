# Enforcement block

Paste into the project's always-loaded instruction file — `CLAUDE.md`, `AGENTS.md`, or equivalent.
Adjust the path if the pitfalls file lives elsewhere.

The index at the bottom grows one line per captured incident. It is the part actually read at the
start of a session, so keep the lines short and imperative.

---

## Pitfalls — record before you fix

Mistakes made on this project. Each line below is the rule; full write-ups are in
[`.claude/pitfalls.md`](.claude/pitfalls.md). Open the full entry before acting in the relevant
scenario — the one-liners are reminders, not the whole story.

**When a mistake is discovered, record it BEFORE correcting it.**

- **Do not apologize and fix.** The apology occupies the slot where the reasoning belongs and feels
  like it settles the matter. Instead: state what happened, state why it looked correct at the time,
  record it, and only then fix.
- **The reasoning is the artifact, not the fix.** Anyone can fix a mistake once it is pointed out.
  The reasoning that produced it is what will produce the next one, and it is recoverable only in
  the moment before the correct version exists. After the fix, it is gone.
- **Fire on self-detection first.** Do not wait to be told. A defect found in your own code, a test
  that fails on something you asserted was correct, a review that turns up your own flawed work, new
  evidence contradicting an earlier claim, a step you notice was skipped, a near-miss on a rule
  already in this list — each is an incident. The moment you think *"actually, that's wrong"* about
  your own work is the trigger; do not let the next sentence be the fix.
- **Also fires when raised externally:** someone corrects a claim or verdict, points out something
  skipped, or says "did you learn", "remember this", "why didn't you catch this", "we have a rule
  for this".
- **Recorded means all three, or it is not done:** (1) the full write-up appended to the pitfalls
  file, including the rationalization — the reasoning as it actually ran, first person, in the tense
  of someone who still believes it; (2) a one-line rule added to the index below; (3) the rule wired
  into the workflow step that would have caught it, so it fires next time instead of relying on
  someone re-reading this list.
- **The checkable rule:** the closing line of any answer about a mistake must contain a real file
  path — or the words "not written down yet." No path and no disclaimer means the lesson was
  narrated, not recorded.
- **Not every error qualifies.** A typo or a transient failure has no reasoning behind it. The bar
  is: was there an argument that felt correct and was not?
- **Self-correcting, not self-flagellating.** Name the failure, name the mechanism that catches it
  next time, move on. If a rule in this list should have caught it and did not, that is the finding
  — fix that rule's enforcement rather than adding a sibling beside it.

### Index

1. **<one-line rule>**
2. ...
