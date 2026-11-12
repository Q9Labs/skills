---
name: burn-tests
description: "Use when asked to burn tests, prune a test suite, or cut a slow or bloated test suite down to the tests that matter."
---

# Burn tests

Default to no test. A stale test has no worth. Delete most of the suite and write
new tests only when a real need appears.

Treat the entire test tree as a removal candidate. Burn duplicate, useless,
unreachable, stale, low-value, and implementation-trivia tests, especially those
that repeat what types, static analysis, schemas, or stronger gates already prove.

The few survivors must prove a current runtime behavior or regression that static
checks cannot catch. Do not keep a test just in case. Use mutation testing to find
the survivors that actually kill meaningful mutations, not to defend most of the
suite.

Remove the test-only helpers, fixtures, runner config, scripts, packages, lockfile
entries, and gate exceptions with the tests. Keep the change isolated in a worktree:
do not rewrite production code, touch concurrent work, or carry unrelated changes.
Verify the resulting deletion slice, run required gates, then open a PR that states
how much went, what little remains, and what static checks replace the removed value.
