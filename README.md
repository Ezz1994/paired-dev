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

- `paired-dev:qa-agent` — on demand only, via `/qa`. Finds the
  feature's specs in the repo, designs test cases, runs them in a real
  browser, and writes a pass/fail report with screenshots, traces, and
  console/network logs. Never touches application code; writes only
  under `qa/`. Works in any repo with no setup — the plugin bundles
  the Playwright MCP server (Node.js required for `npx`).

## QA usage

Start your app locally, then:

```
/qa login                            full run: design, execute, report
/qa checkout --focus "coupon codes"  targeted run on one item
/qa settings --cases-only            design cases only, no browser
/qa rerun qa/reports/<report>.md     re-run Failed / Blocked / Flaky cases
/qa login --url https://staging.example.com   test a non-local URL
```

The agent finds a running local dev server by itself. It only opens
non-local URLs you pass explicitly, and asks before anything that looks
like production. If the app needs a login, give it test credentials in
the command. Results land in `qa/test-cases/`, `qa/reports/`, and
`qa/evidence/` (gitignored).

Optional: install the Snagly plugin for deeper accessibility,
visual-regression, and performance checks, or add a `qa/config.yml`
to pin environments, features, and test accounts (format in
`agents/qa-agent.md`).

## Optional: enforce the workflow in a project

The plugin does not force itself onto any repo. If you want the
developer → reviewer handoff enforced for non-trivial changes, paste
the contents of [`CLAUDE-snippet.md`](./CLAUDE-snippet.md) into that
project's `CLAUDE.md`. Skip it for typos, one-liners, and small
changes — see the snippet for the exact cutoff.
