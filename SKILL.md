---
name: bottom-line
description: End any response that needs something from the user with a crisp TLDR ask block as the literal last thing in the message. Use whenever a turn ends with a question, a decision, options, or a "shall I proceed", especially after long analysis or a completed coding task. Also use when the user says "bottom line", "what do you need from me", or complains the ask was buried.
---

# Bottom Line

The user reads the end of a message first. When a long response buries its
question in the middle of the prose, the user has to read everything before
and after just to find out what is being asked. That is slow. This skill
fixes it: whatever the message needs from the user must be the literal last
thing in it, formatted so it can be answered in one or two words.

## The rule

Full detail, findings, and reasoning go in the body as usual. The message
must not contain the ask only in the body. Restate it at the very end in
this block:

```
|---------------------------------------------------------------|

**Bottom line - what I need from you:** <one sentence stating the decision>

1. <option> (recommended)
2. <option>
3. <option>

Answer with a number.
```

## The line

The separator is a two-line lockup: an ASCII rule, then the bold
"Bottom line" label directly beneath it. That is the joke and the
mnemonic - the words sit under the line, so they are literally the
bottom line.

- The rule (copy verbatim, a pipe, 63 dashes, a pipe):
  `|---------------------------------------------------------------|`
- Under it, after a blank line, the label opens the ask:
  `**Bottom line - what I need from you:** ...`

Why the blank lines are load-bearing: a pipe-and-dash line is exactly
GFM's table delimiter row, so without a blank line above it the
paragraph before would be swallowed as a table header. Standing alone
between blank lines it is not a table, not a horizontal rule, and not a
setext heading - just a literal paragraph that renders the same in
every markdown view and raw terminal. Always leave a blank line above
the rule and between the rule and the label. Do not improvise other
widths or characters; one fixed rule means the lockup is instantly
recognizable in a scrollback.

## Rules for the block

1. **Last thing, always.** Nothing after the block: no caveats, no "also
   note", no sources, no sign-off. If a caveat matters, it belongs in an
   option label or in the body above. The ASCII line always opens the
   block; nothing but the block ever follows the line.
2. **One decision per block when possible.** Prefer yes/no questions. If
   several decisions are genuinely unavoidable, label them Q1, Q2, Q3, each
   with its own numbered options, so the answer can be as short as
   "Q1: 2, Q2: yes".
3. **Options are short labels, not paragraphs.** "1. Write PLAN v2" not
   "1. I could write a version 2 of the plan incorporating the four fixes
   and the scripted-pipeline reframe, leaving v1 in place". The long form
   already exists in the body; do not repeat it.
4. **Mark the recommended option and put it first.** If there is no
   recommendation, say so in the question sentence.
5. **The block states the ask, never the findings.** It is not a summary of
   the work. Summaries of the work go at the TOP of the message (lead with
   the outcome); the ask goes at the BOTTOM. Do not merge the two.
6. **Nothing needed? Say so in one line.** When the task is done and no
   input is required, end with the rule and then:
   `**Bottom line:** done, nothing needed from you.`
   and stop. No options, no manufactured questions.
7. **Too complex for a number? Say that explicitly.** When the decision
   genuinely requires the user to read the details, do not pretend it fits
   in three options. Use the rule, then:
   `**Bottom line - this one needs your read:** see <named section> above,
   then tell me <the specific thing>.`
   Point at the exact section, not "the above".
8. **Interactive sessions:** when the AskUserQuestion tool is available and
   the turn is blocked on the decision, use the tool instead of the text
   block; its options follow the same rules (short labels, recommended
   first). When the turn is complete and the question is a follow-up offer,
   use the text block.

## Anti-patterns this skill exists to kill

- The ask appearing as the second-to-last sentence, followed by a source
  list, a caveat paragraph, or a "one note before you hand it off".
- "Want me to X? I'll also Y, and we could Z" - three asks fused into one
  sentence with no way to answer "yes to X, no to Y" cheaply.
- Ending with a menu of paths (Path A / Path B / Path C) described in full
  paragraphs but never asking a numbered question the user can answer with
  "A".
- A closing question that requires re-reading the middle of the message to
  understand what "it" and "that" refer to. The block's question sentence
  must be self-contained.

## Example

Bad (real pattern this skill was written against):

> ...The clean move is to fold all of this into a v2 plan - most
> importantly, splitting the goal into the two tracks. Want me to write
> PLAN v2 incorporating the four fixes? I'll leave v1 and the audit in
> place beside it so the trail survives.

Good:

> ...body of the message, full findings, as long as it needs to be...
>
> |---------------------------------------------------------------|
>
> **Bottom line - what I need from you:** should I write PLAN v2 now?
>
> 1. Yes, write PLAN v2 with the four fixes (recommended)
> 2. No, stop here
> 3. Revise something first (tell me what)
>
> Answer with a number.

Good, task complete with nothing to decide:

> ...body of the message...
>
> |---------------------------------------------------------------|
>
> **Bottom line:** done, nothing needed from you.
