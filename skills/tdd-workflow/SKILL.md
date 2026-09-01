---
name: tdd-workflow
description: Use before writing implementation code for any feature or bugfix. Enforces a test-first loop.
---

# Test-first workflow

1. Write ONE failing test describing the smallest next increment of
   behavior. Run it. Confirm it fails, and fails for the right reason.
2. Write the minimum implementation to make that test pass. Run it.
   Confirm green.
3. Refactor with the test green. Run again.
4. Repeat from step 1 until the feature is complete.

Rules:
- Never write implementation before a failing test exists for it.
- One behavior per test. Name the test by the behavior, not the method.
- Keep the whole suite green between increments.
- If a piece genuinely cannot be tested, say why before writing it.
