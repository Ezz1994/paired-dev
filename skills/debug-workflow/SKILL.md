---
name: debug-workflow
description: Use when encountering a bug, test failure, or unexpected behavior, before proposing any fix.
---

# Debugging workflow

1. Reproduce. Get a reliable, minimal repro. If you cannot reproduce
   it, gather more data before touching code.
2. Observe. Read the actual error, stack trace, and surrounding code.
   State plainly what you expected versus what happened.
3. Hypothesize ONE cause. Phrase it so it can be proven false.
4. Test the hypothesis with a targeted probe — a log line, a
   breakpoint, an assertion — not a speculative fix.
5. Confirmed: make the minimal fix and add a regression test that
   fails without it. Wrong: discard and go to the next hypothesis.
6. Never ship a fix you cannot explain.
