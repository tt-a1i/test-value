<p align="center">
  <img src="assets/banner.svg" alt="Test Value — Less friction. Meaningful protection. Keep the tests that earn their place." width="100%">
</p>

<p align="center">
  <a href="README.md">简体中文</a> · <strong>English</strong>
</p>
<p align="center">
  <a href="#quick-start">Quick start</a> ·
  <a href="#what-it-improves">What it improves</a> ·
  <a href="#the-principles">The principles</a> ·
  <a href="SKILL.md">Read the skill</a>
</p>

# AI writes tests quickly. Maintaining them is expensive.

A routine refactor turns dozens of tests red. A clearer automatic layout fails an old coordinate snapshot. Every small change launches another complete suite, adding more waiting and false-alarm investigation.

**Test Value** is a testing-maintenance skill for AI agents. It helps agents decide which tests to add, reuse, rewrite or retire during implementation, before a commit, and when improving an existing suite.

> **Which concrete mistake does this test catch — and what maintenance cost is that protection worth?**

Developed from hands-on test maintenance in [Archify](https://github.com/tt-a1i/archify), it helps tests keep protecting the product while allowing valid refactors, performance improvements and better product outcomes.

## What it improves

| The problem | A better agent decision | The value retained |
| --- | --- | --- |
| Every small edit runs the complete suite | Select checks by impact and reuse applicable results | Feedback proportionate to the current risk |
| Shared rules are repeated across entrypoints | Cover shared rules and verify each entrypoint's integration | Protection for rules and entrypoint differences |
| Tests depend on private names or source spelling | Check output, state or actual failure boundaries | Equivalent refactors can pass |
| Every automatic-output change breaks a snapshot | Separate explicit requirements from algorithm-selected choices | Room for better valid outcomes |
| A retry turns red into green without explanation | Investigate readiness, isolation, cleanup and real races | Failures remain visible |
| AI-generated implementation and tests share a mistake | Establish expectations from requirements, contracts or real failures | An independent basis for correctness |

**Cuts need evidence too.** Preserve effective protection for data integrity, permissions, compatibility, essential accessibility, resource cleanup and failure recovery. A rare, severe fault can justify more protection than many inexpensive assertions.

## Quick start

Install with the [Skills CLI](https://github.com/vercel-labs/skills):

```sh
npx skills add tt-a1i/test-value --skill test-value
```

Choose the target agent and installation scope in the installer. To inspect the available skill without installing:

```sh
npx skills add tt-a1i/test-value --list
```

In Codex, invoke it explicitly with `$test-value`. Other skill-capable agents use their host's supported invocation method. For manual installation, place `SKILL.md` and `references/` in the host's skill directory; `agents/` contains Codex UI metadata.

Skill instructions remain in English; the README is available in Chinese and English. The skill provides reusable decision guidance. Discovery and invocation depend on the agent host.

## Three prompts to copy

### ① During implementation: catch the actual mistake

```text
Use $test-value while fixing this bug.
Look for existing coverage, then choose the cheapest regression that exposes
the real failure. Confirm the bad result fails and the fix passes.
```

### ② Before a commit: examine the change without expanding the task

```text
Use $test-value to review tests relevant to this diff.
Identify missing protection, duplicate checks and assertions that would
reject an equivalent refactor. Select verification by risk.
Do not commit or push.
```

### ③ During an audit: reduce waiting and future maintenance

```text
Use $test-value to investigate slow, brittle or redundant tests in this project.
Implement evidence-backed improvements in batches, preserving core behavior
and real failure boundaries. Report gains, removed combinations and
validation gaps. Keep changes local.
```

## The principles

**Correctness needs an independent basis.** Code and tests generated from that code can agree and still be wrong. Establish expectations from requirements, public contracts, compatibility fixtures and observed failures.

**Protect outcomes and allow improvement.** Automatically chosen bends can often change. User-authored coordinates, ports and paths remain constraints. Public formats and promised deterministic output may still require exact comparison.

**Count the whole cost.** Waiting, false-alarm investigation, fixture upkeep, blocked refactors and repeated verification all matter. Test counts and coverage percentages cannot establish value on their own.

**Use evidence for additions and cuts.** When relaxing an assertion, check that a valid alternative passes and the original mistake still fails. When removing duplicates, identify the surviving protection.

**Match verification to risk.** Reuse applicable evidence and expand checks by impact. Confirm intended tests actually ran. Accidental zero selection, skipped environments and simulated results each have different evidential limits.

## Grow through real use

Agents may refine the skill when evidence reveals a useful new principle. Explain the observation, which decision improves, when it applies and a meaningful exception.

Prefer refining existing principles to accumulating rules. After every update, the agent must tell the user **what changed, why, where, and whether it was saved**. Local learning does not automatically publish or synchronize changes to other installations.

## Contents and contributions

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Scope, decisions, protection boundaries and learning from use |
| [Audit guide](references/audit.md) | Cost investigation, reduction evidence and execution by risk |
| [Decision examples](references/decision-examples.md) | Layouts, shared matrices, source assertions, asynchronous waits and more |
| [Contributing](CONTRIBUTING.md) | Improve the guidance using real problems and counterexamples |

The skill has received independent agent review and scenario-based review. Broader effectiveness still needs to be established through real use. Bring a concrete failure, counterexample or maintenance improvement to help make it more useful and concise.

<p align="center">
  <a href="LICENSE">MIT License</a> · <a href="README.md">Chinese version</a> · <a href="https://github.com/tt-a1i/test-value/issues">Feedback &amp; discussion</a>
</p>
