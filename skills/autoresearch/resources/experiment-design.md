# Experiment Design

Use this loop state when the next investigation needs design before execution.
Designing is recurring; reopen it after surprising results, failed gates, new
evidence, or human correction. Use `/goal-writing` to define the optimization
target, evidence, anti-goals, and reviewer gates. The user must provide or
approve the exact goal block before the design becomes a runner handoff.

## Direct Brief vs Design Lead

Write the stage brief directly only when the design is low-risk and has one
credible path.

Spawn `@design-lead` when the next experiment has nontrivial alternatives,
unclear boundaries, meaningful cost, feasibility risk, data/benchmark choices,
or downstream decisions that depend on the design. Reuse the Meridian design
workflow instead of rebuilding it inside autoresearch.

A good `@design-lead` handoff includes:

- research question and current campaign context,
- chosen branch from the dialogue,
- alternatives that need comparison,
- constraints and failure modes,
- relevant artifacts and prior results,
- the expected output: an experiment design brief, not implementation.

## Stage Brief

Whether written directly or returned by `@design-lead`, the stage brief should
make the next investigation runnable and interpretable:

1. Hypothesis or mechanism.
2. Baseline, control, or competing explanation.
3. Setup: data, model/system, branch or commit, config, parameters.
4. Metric or evidence type: benchmark number, validation signal, literature
   constraint, assay feasibility, or review gate.
5. Runner: usually `@autoresearch-runner`, plus the command, script, notebook,
   lab protocol owner, or project-specific worker it should use.
6. Outputs: where metrics, logs, notes, and artifacts should land.
7. Gate: pass/fail/ambiguous criteria and what each outcome implies.
8. Next branches: likely follow-up if pass, fail, or surprise.

Do not overfit the design to one expected result. A useful design makes failure
and surprise interpretable too.
