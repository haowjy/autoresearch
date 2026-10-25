# Changelog

Format: Keep a Changelog. Versioning: SemVer.

## [Unreleased]

### Changed
- Requires Meridian >=0.14.0 and Mars >=0.18.0 for portable network policies.
- `@autoresearch-lead` runs `danger-full-access`, like the other leads: Meridian refuses a sandboxed caller any child less confined than itself, which blocked five of its declared subagents (autoresearch-runner, design-lead, source-researcher, prober, reviewer).

## [0.1.7] - 2026-10-25

### Changed
- Requires Meridian >=0.13.0 for platform-owned Meridian command permissions.
- `@autoresearch-lead` drops its redundant `bash(meridian *)` rule; plain Bash already grants those commands, and Meridian grants spawn commands from its `subagents` declaration.

## [0.1.6] - 2026-10-23

### Changed
- Dependencies pinned to the current minors: meridian-base `>=0.11.0, <0.12.0`, meridian-dev-workflow `>=0.15.0, <0.16.0`. 0.1.5 left them unpinned.

## [0.1.5] - 2026-10-23

### Changed
- Dependencies unpinned: meridian-base and meridian-dev-workflow resolve to their latest releases. The old `<0.11.0` / `<0.14.0` ranges excluded current releases.

## [0.1.4] - 2026-10-15

### Changed
- `@autoresearch-lead`: default model `opus46` → `opus` (Opus 5.5). `@autoresearch-runner`: `sonnet5` fallback → `sonnet`.

## [0.1.3] - 2026-09-22

### Changed
- Removed Composer from autoresearch-runner's fallback policy; the base alias remains available during retirement.
- Autoresearch runner names Sol directly instead of the legacy gpt55 alias; high effort is unchanged.
- Research lead keeps Opus46, then Astra, Sol, Sonnet for user-facing judgment and writing. Removed its fixed harness so aliases select compatible routes.
- Requires meridian-base >=0.10.11 and meridian-dev-workflow >=0.13.6 for refreshed staffing and model aliases.

## [0.1.2] - 2026-07-09

### Changed
- Bump meridian-base dependency to `>=0.8.0, <0.9.0` and meridian-dev-workflow to `>=0.12.1, <0.13.0`.

## [0.1.1] - 2026-06-30

- Clarify that planning is human-in-the-loop while approved goal execution is autonomous, with preflight sniff tests, memory checkpoints, and gated reviewers.
- Clarify that `autoresearch-lead` owns the user-facing, evidence-grounded design-tree walk for requirements and scope.
- Require execution handoffs to include a runner handoff plus a separate user-pasteable goal block.
- Add `autoresearch-runner` execution subagent and require a user-approved goal before execution handoff.
- Require `meridian-base` v0.7.34+ and load `/goal-writing` so autoresearch goals include evidence, anti-goals, stop conditions, and reviewer gates.
- Pivoted package framing toward AI researchers and the Meridian ecosystem.
- Added `meridian-dev-workflow` dependency so `autoresearch-lead` can delegate nontrivial experiment design to `@design-lead`.
- Replaced linear phase resources with loop-state resources: evidence-grounded research dialogue, experiment design, run supervision, and reconvene/record/decide.
- Initial `autoresearch` skill and thin `autoresearch-lead` agent.
