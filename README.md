# paired-dev

Claude Code plugin: a `developer` agent and a `reviewer` agent for a
tight implement → review loop.

## Requirements

The `developer` agent invokes skills from the **`superpowers`** plugin,
so it must be installed alongside this one:

```
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
```

Without `superpowers`, the developer agent still runs but falls back to
unstructured work — the test-first and debugging loops are gone. The
`reviewer` agent has no such dependency.

## Install

```
/plugin marketplace add Ezz1994/paired-dev
/plugin install paired-dev@paired-dev
```

## Update

After a new version is pushed:

```
/plugin update paired-dev
```

## What you get

- `paired-dev:developer` — implements features and fixes bugs. Explores
  first, then follows `superpowers:test-driven-development` for new
  behavior and `superpowers:systematic-debugging` for bugs, and runs
  `superpowers:verification-before-completion` before reporting.
- `paired-dev:reviewer` — read-only. Reviews a finished change for
  plan alignment, correctness, security, regression risk, and fit,
  using the superpowers code-review rubric. Reports Strengths, then
  Critical / Important / Minor issues, then an Assessment with a
  "Ready to merge? Yes | No | With fixes" verdict.

## Optional: enforce the workflow in a project

The plugin does not force itself onto any repo. If you want the
developer → reviewer handoff enforced for non-trivial changes, paste
the contents of [`CLAUDE-snippet.md`](./CLAUDE-snippet.md) into that
project's `CLAUDE.md`. Skip it for typos, one-liners, and small
changes — see the snippet for the exact cutoff.
