# Changelog

Format: Keep a Changelog. Versioning: SemVer.

## [Unreleased]

- Require `meridian-base` v0.7.34+ and load `/goal-writing` so autoresearch goals include evidence, anti-goals, stop conditions, and reviewer gates.
- Pivoted package framing toward AI researchers and the Meridian ecosystem.
- Added `meridian-dev-workflow` dependency so `autoresearch-lead` can delegate nontrivial experiment design to `@design-lead`.
- Replaced linear phase resources with loop-state resources: evidence-grounded research dialogue, experiment design, run supervision, and reconvene/record/decide.
- Initial `autoresearch` skill and thin `autoresearch-lead` agent.
