# Contributing

Help the skill make better testing decisions without turning it into another maintenance burden.

For a proposed change, explain:

- The observed problem or counterexample, using redacted or public material.
- What an agent should decide differently.
- When the guidance applies, and a meaningful exception.
- Why the existing guidance does not already cover it.

Prefer improving an existing principle to adding a new rule. Keep cross-cutting guidance in `SKILL.md` and conditional examples in the relevant reference. Keep instructions and examples in English.

Review changes against a realistic scenario. For example, does the new guidance distinguish a valuable slow regression from redundant coverage? Does it let an equivalent refactor pass without concealing the original bug? Check relative links and keep the skill's frontmatter and UI metadata valid when editing them.

Avoid mandatory scorecards, universal timing thresholds, test-count targets and new automation unless an observed need justifies their ongoing cost. Do not include private project logs, credentials or personal information.

A local agent improvement is not automatically an upstream contribution. Review the diff before opening a pull request, and describe any intentional change in the skill's scope or protection boundaries.
