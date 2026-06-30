# Changelog

Format: Keep a Changelog. Versioning: SemVer.

## [Unreleased]

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
