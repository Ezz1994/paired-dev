# paired-dev

Claude Code plugin: a `developer` agent and a `reviewer` agent, plus the
`tdd-workflow` and `debug-workflow` skills they depend on. No dependency
on `superpowers`, `caveman`, or any other plugin.

## Install

```
/plugin marketplace add ezzshaheen/paired-dev
/plugin install paired-dev@paired-dev
```

## Update

After a new version is pushed:

```
/plugin update paired-dev
```

## What you get

- `paired-dev:developer` — implements features and fixes bugs. Explores
  first, invokes `tdd-workflow` for new behavior and `debug-workflow`
  for bugs, runs the test suite before reporting.
- `paired-dev:reviewer` — read-only. Reviews a finished change for
  correctness, security, regression risk, and fit. One line per
  finding, ends with `VERDICT: SHIP` or `VERDICT: FIX`.
- `paired-dev:tdd-workflow` / `paired-dev:debug-workflow` — short,
  self-contained skills the developer agent invokes directly.

## Optional: enforce the workflow in a project

The plugin does not force itself onto any repo. If you want the
developer → reviewer handoff enforced for non-trivial changes, paste
the contents of [`CLAUDE-snippet.md`](./CLAUDE-snippet.md) into that
project's `CLAUDE.md`. Skip it for typos, one-liners, and small
changes — see the snippet for the exact cutoff.
