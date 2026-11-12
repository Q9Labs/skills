# Q9 Labs skills

Agent skills we use at Q9 Labs, where agents write most of our code. They work with Claude Code, Codex and any agent that reads `SKILL.md` files.

| Skill | What it does |
| --- | --- |
| [burn-tests](skills/burn-tests/SKILL.md) | Deletes most of a test suite and keeps only the tests that prove runtime behavior that types, lint and other static checks can't. |
| [write-tests](skills/write-tests/SKILL.md) | Decides whether a change needs a test at all, and when it does, writes the smallest test that catches a real defect. |

We ran burn-tests on our video-call product and deleted about 180k lines of tests in one PR. A second model checked the deletion against the list of customer journeys, and the gaps it found were put back before merge.

## Install

```sh
npx skills add Q9Labs/skills
```

Or copy a folder from `skills/` into `~/.claude/skills/` (Claude Code) or `~/.agents/skills/` (Codex).

## License

MIT
