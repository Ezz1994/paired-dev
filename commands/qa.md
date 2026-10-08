---
description: Run the QA agent — design test cases, execute them in a browser, and report
argument-hint: [feature] [--focus "<what>"] [--cases-only] [--url <url>] | rerun <report-file>
disable-model-invocation: true
---

Delegate this to the `paired-dev:qa-agent` subagent. Pass it these
arguments verbatim and nothing else as its task:

```
$ARGUMENTS
```

When the agent returns, relay its summary (pass rate, failed IDs with
causes, report path) to the user. If it stopped to ask for something
(a URL, credentials, a clarification), relay the question. Do not fix
any reported bug unless the user asks you to in a separate request.
