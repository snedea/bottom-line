# bottom-line

A Claude Code skill that forces the ask to the bottom of the message.

## The problem

Long agent responses bury their actual question ("shall I write the plan?")
in the middle of paragraphs of analysis. The human has to read everything
before and after the question just to find out what is being asked, which
turns a two-second "yes" into a five-minute read.

## The fix

Whenever a response needs something from the user, it must end with a crisp
block, as the literal last thing in the message:

```
|---------------------------------------------------------------|

**Bottom line - what I need from you:** should I write PLAN v2 now?

1. Yes, write PLAN v2 with the four fixes (recommended)
2. No, stop here
3. Revise something first (tell me what)

Answer with a number.
```

The lockup is two lines: an ASCII rule, then the bold "Bottom line"
label directly beneath it - the words sit under the line, so they are
literally the bottom line. The rule needs a blank line on each side to
survive markdown rendering: a pipe-and-dash line is GFM table-delimiter
syntax, and without the blank line above, the preceding paragraph would
be parsed as a table header. Isolated, it renders as-is in a raw
terminal and a rendered view alike. It is also the anchor: scrolling up
through scrollback, the eye snaps to it before anything else. When
nothing is needed, the same rule closes with one line:

```
|---------------------------------------------------------------|

**Bottom line:** done, nothing needed from you.
```

The full detail stays in the body for context. The block only states the
ask. When nothing is needed, one line: "done, nothing needed from you."
When the decision genuinely requires reading, the block says so and points
at the exact section instead of faking a multiple-choice question.

## Install

```bash
git clone https://github.com/snedea/bottom-line ~/.claude/skills/bottom-line
```

Restart Claude Code (or start a new session). Invoke explicitly with
`/bottom-line`, or let it trigger when a turn ends with a decision. To make
it a standing habit, add one line to your `~/.claude/CLAUDE.md`:

```
- End every response that needs my input per the bottom-line skill.
```

## Files

- `SKILL.md` - the skill itself (frontmatter + rules)
