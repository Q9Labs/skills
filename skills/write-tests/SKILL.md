---
name: write-tests
description: "Use when deciding whether to add or change software tests."
---

# Write tests

Default to no new test. Identify the consequential runtime behavior or real regression at risk and what existing tests or automated checks already cover. Types, schemas, static analysis and stronger gates may be enough. If there is no distinct gap, verify with existing checks or a direct run instead.

A user-facing journey is the exception. A change that adds or alters one gets an end-to-end test of that journey, written as the steps a user takes and checked by what the user sees.

For each test worth adding:

1. Identify the observable behavior and a plausible defect it catches that existing checks miss. Prefer a real regression or an important boundary, failure, or state transition over speculative cases.
2. Exercise the narrowest realistic public boundary that reveals the defect. Assert outcomes a caller can observe, not private calls, mock choreography, incidental text, or implementation shape. Use real collaborators when practical; replace external or costly dependencies only as needed for reliability.
3. Add the smallest set of distinct cases covering the gap. Extend an existing test when appropriate; avoid duplicate cases, trivial getters, framework behavior, and tests that restate types or production code. Keep fixtures and setup proportionate, and avoid one-off test abstractions.
4. Run the relevant test and checks. Where practical, demonstrate that the test fails for the defect it claims to catch, then restore the correct code and confirm it passes. Otherwise explain what was verified and the limitation.

While working in a test, improve the relevant tests around it when justified: update or remove obsolete or duplicate cases, or rewrite the touched section if that produces a clearer, smaller set. Check what distinct behavior each existing test covers before changing it, and preserve coverage that still matters. Keep cleanup related to the task and verify the resulting tests; a whole-suite pruning is burn-tests, not routine cleanup.

Honor explicit requests for tests, TDD, or a regression test and project-required gates.
