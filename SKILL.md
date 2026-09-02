---
name: bottom-line
description: End any response that needs something from the user with a crisp TLDR ask block as the literal last thing in the message. Use whenever a turn ends with a question, a decision, options, or a "shall I proceed", especially after long analysis or a completed coding task. Also use when the user says "bottom line", "what do you need from me", or complains the ask was buried.
---

# Bottom Line

The user reads the end of a message first. Whatever the message needs
from the user must be the literal last thing in it, answerable in one
or two words. Full detail and findings stay in the body; the ask is
restated at the very end in this block:

```
|---------------------------------------------------------------|

**Bottom line - what I need from you:** <one sentence stating the decision>

1. <option> (recommended)
2. <option>
3. <option>

Answer with a number.
```

The lockup is two lines: the rule (copy verbatim: a pipe, 63 dashes, a
pipe), then the bold label beneath it - literally the bottom line. The
blank lines around the rule are load-bearing: a pipe-and-dash line is
GFM table-delimiter syntax, and without a blank line above it the
previous paragraph becomes a table header. Isolated between blank
lines it renders as-is in every markdown view and raw terminal. Never
change the rule's width or characters.

## Rules for the block

1. **Last thing, always.** Nothing after the block: no caveats, no
   sources, no sign-off. If a caveat matters, it belongs in an option
   label or in the body above.
2. **One decision per block when possible.** Prefer yes/no. If several
   are unavoidable, label them Q1, Q2, Q3, each with its own options,
   so the answer can be "Q1: 2, Q2: yes".
3. **Options are short labels, not paragraphs.** The long form already
   exists in the body; do not repeat it.
4. **Recommended option marked and first.** If there is no
   recommendation, say so in the question sentence.
5. **The block states the ask, never the findings.** Summaries lead
   the TOP of the message; the ask goes at the BOTTOM. Do not merge.
6. **Nothing needed? Say so in one line.** End with the rule, then
   `**Bottom line:** done, nothing needed from you.` and stop. No
   manufactured questions.
7. **Too complex for a number? Say that explicitly.** Use the rule,
   then: `**Bottom line - this one needs your read:** see <named
   section> above, then tell me <the specific thing>.` Point at the
   exact section, not "the above".
8. **Interactive sessions:** when AskUserQuestion is available and the
   turn is blocked on the decision, use the tool instead of the text
   block (same rules: short labels, recommended first). Follow-up
   offers after a completed turn use the text block.

## Anti-patterns this skill exists to kill

- The ask second-to-last, followed by a source list or caveat
  paragraph.
- Fused asks ("Want me to X? I'll also Y, and we could Z") with no
  cheap way to answer each separately.
- A menu of paths described in full paragraphs but never a numbered
  question answerable with "A".
- A closing question whose "it" and "that" require re-reading the
  middle of the message; the question sentence must be self-contained.
