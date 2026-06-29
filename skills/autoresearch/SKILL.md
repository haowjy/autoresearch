---
name: autoresearch
type: reference
description: >
  Load when coordinating an autonomous research campaign: framing hypotheses,
  planning experiments, routing execution, triaging results, and maintaining
  research artifacts across work logs, machine run indexes, and durable KB.
model-invocable: true
---

# Autoresearch

Use this skill to run research as a disciplined campaign loop. Own the framing,
state, interpretation, and next-step decisions. Delegate implementation and long
runs to project-specific runners or workers.

## Operating Frame

Start by making the research question explicit:

- What hypothesis is being tested?
- What observation would change the plan?
- What metric, gate, or qualitative signal decides whether the result matters?
- What artifact will preserve the decision after the run?

Do not spend compute until the hypothesis, setup, and success signal are clear
enough that another agent could run the experiment without reinterpreting intent.

## Artifact Layers

Maintain three layers of research memory. Use the project's configured paths and
names; do not hardcode package-specific paths unless the project provides them.

| Layer | Purpose | Contents |
|---|---|---|
| Program index | Cross-campaign state | Best official results, active campaigns, stage snapshots, durable pointers |
| Campaign narrative | Human interpretation | Hypotheses, setups, results, surprises, next experiment IDs |
| Machine run ledger | Exhaustive run record | Run IDs, configs, metrics, logs, output directories |

Keep these layers distinct. The program index is compact and curated. The
campaign narrative explains why the result matters. The machine ledger preserves
every run without forcing full logs into human-facing summaries.

## Campaign Loop

1. **Frame.** Convert the user's goal into one or more testable hypotheses.
2. **Stage.** Define the next gate: expected setup, metric, pass/fail criteria,
   and what will happen after each outcome.
3. **Route.** Hand execution to the right project-specific runner. Pass concrete
   files and exact success criteria; avoid broad context dumps.
4. **Triage.** Separate infrastructure failures, calibration-only runs, official
   candidate runs, and surprising results.
5. **Record.** Update the appropriate artifact layer with provenance and
   interpretation.
6. **Decide.** Choose the next experiment, promote a durable decision, or stop
   when the campaign no longer has a useful next test.

## Result Triage

Treat runs differently by purpose:

- **Calibration-only:** use for debugging, sizing, smoke tests, or threshold
  setting. Do not promote as an official result unless the project or human says
  to.
- **Infrastructure failure:** record only enough to avoid repeating the failure.
  Do not interpret scientific meaning from a broken setup.
- **Official candidate:** record commit, config, parameters, run directory,
  metrics, and comparison to the current best or stage gate.
- **Surprising result:** preserve the setup and observed behavior even if it is
  not a new best. Surprises often become the next campaign.

## Logging Shape

A useful experiment entry answers:

1. Hypothesis.
2. Setup: commit, config, parameters, data, and runner command when relevant.
3. Result: metrics and run directory or report path.
4. Interpretation: what changed in the research state.
5. Surprises or failure notes.
6. Next experiment IDs or stop condition.

Prefer links or paths to bulky artifacts over pasted logs. Use the project's
link style and path conventions.

## Durable Decisions

Promote a conclusion to durable KB or decision docs when it will guide future
campaigns, not merely explain one run. Durable decisions include benchmark
selection, official metric policy, accepted/rejected experimental mechanisms,
and recurring failure modes with known fixes.

Keep speculation in the campaign narrative until evidence makes it reusable.

## Delegation

When handing work to another agent or runner, include:

- the hypothesis and stage gate,
- exact files or directories to read,
- the command or project runner entrypoint if known,
- what counts as success, failure, or calibration,
- where to write outputs,
- what summary to return.

Managers and leads coordinate. They should not silently become the experiment
implementation worker unless the user explicitly asks for direct execution.
