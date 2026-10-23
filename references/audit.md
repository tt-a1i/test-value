# Auditing Existing Tests

## Map the cost

Confirm the workspace, comparison baseline and uncommitted changes; read test entrypoints and CI configuration. Reuse current logs before collecting measurements that are genuinely missing. If a candidate fails before its measurement or contract phase, record that unmet precondition rather than a metric. The timeout text and a post-run artifact hash are not measurements of the metric, and lengthening the timeout does not create one. Where a change is authorized, make the precondition fail explicitly, then measure only runs that pass it.

For broad work, group tests by responsibility: core product behavior, shared algorithms, entrypoint integration, browser/platform behavior, filesystem and process safety, distribution/installation, generated artifacts and CI selection. Identify uninspected areas; one successful cut does not establish that the whole project is optimal.

Cost includes execution time, false-alarm investigation, fixture maintenance, blocked refactors, flaky reruns and resource contention. A lack of historical failures does not establish low value: rare data corruption can justify expensive protection.

Break down the slow path into dependency installation, build, collection/environment setup, execution, artifact transfer and teardown before choosing a change. Shared setup can charge every test for an environment only a few need; an installation smoke can spend most of its time installing rather than checking behavior. Scope setup to its actual consumers and check those consumers still work. Re-measure the critical path after an improvement: extra shards stop helping feedback time when another stage dominates.

Choose candidates from measured bottlenecks, frequent false alarms or current development friction. Avoid predetermined deletion ratios, coverage targets or universal time limits. An expensive test outside the daily loop may cost less than hundreds of small duplicates in every feedback cycle.

## Prove the boundary of a cut

For substantial reductions, keep a short, reviewable record:

- **Burden:** measured execution or maintenance cost, or a concrete false alarm.
- **Existing protection:** the actual mistake, entrypoints and implementation paths.
- **Change:** deletion, consolidation, rewritten assertion, fixture reuse or changed execution timing.
- **Surviving evidence:** how remaining tests detect the mistake; combinations intentionally no longer exercised.
- **Verification:** commands and outcomes, comparable timing, baseline failures and untested environments.

Prefer low-cost changes to a new test framework, dynamic dependency graph or layered runner. Selection machinery also creates maintenance obligations; introduce it only when existing tools cannot meet an evidenced need.

## Select execution by risk

Use the repository's risk distribution, not another project's command names or runtime versions.

- **Daily feedback:** core public behavior and affected regressions.
- **Expanded checks:** relevant integration and consumers of shared changes.
- **Platform and delivery checks:** distinct risks in real browsers, operating systems, installation, packaging and release identity.
- **Complete verification:** infrastructure changes, uncertain impact or the project's release requirements.

Before reducing platform matrices, distinguish runtime-compatibility smoke from platform-specific faults. Preserve actual evidence for platform differences. A mock or runner command list demonstrates dispatch, not native path behavior.

When changing affected-test selection, check new files, renames, deletions, shared dependencies and unknown paths. Classification failures must not silently become successful skips. Respect required checks; a request for faster feedback does not authorize changing branch protection or release policy.

## Remove duplicate execution and preserve CI gates

Trace which suites each job actually executes before cutting cases. A mixed browser suite may repeat ordinary checks already owned by a Node job; separating responsibilities can remove duplicate execution while retaining every case. Keep repetition that exposes a distinct runtime or platform risk, and account for any additional fixture setup introduced by the split.

When introducing shards, establish that their union covers the intended inventory and their intersections are empty unless overlap is deliberate. Required aggregation must reject failed, cancelled or missing required work; intentional skips need an explicit scope decision. Verify that deployment and release consumers still depend on the required result. Inventory checks prove dispatch, while real runs establish execution in the target environment.

Use measured job costs to balance shards and remove avoidable serial setup. Account for checks assigned to only one shard. Faster wall time can consume more compute, and extra workers can increase contention. Borrow mechanisms from other projects only when they address an observed bottleneck; caching and orchestration also have maintenance and setup costs.

## Optimize installation without bypassing acceptance

When caching, resolve the directory used by the actual consumer under its effective environment and configuration. A wrapper that sanitizes variables or supplies an empty config can use a different cache from the CI setup action. A restored archive alone proves neither consumption nor saved work. Compare a bounded cold/warm run on the same revision, including restore overhead; retain a cold check when network installation is itself the contract. Keep fresh install destinations when validating installation, rather than substituting a cached installed tree.

If install payload dominates, inspect runtime versus build-only dependencies before adding more orchestration. Validate dependency reductions from the produced package in a clean location outside checkout dependency resolution. Exercise affected runtime features, including dynamic imports, and preserve shipped assets and required third-party notices for bundled code. Static import scans support this check but cannot establish every runtime path. Keep dependencies actually used at runtime even if a common smoke does not load them.

## Work in batches

Complete a change and verification for one responsibility boundary before moving to the next. Stabilize unreliable measurements before claiming speedups. Track live process handles; an observation timeout does not justify starting another full run.

Reuse verification unaffected by later changes. When only proven redundant assertions are removed, run surviving behavior checks or reuse applicable results. Reducing test cost should not produce an ever-growing verification ritual.

At the end, identify retained protections, intentionally removed combinations and deferred candidates. Use an existing evidence location when useful rather than automatically creating a new body of governance documentation.
