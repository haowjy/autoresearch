---
name: autoresearch
type: reference
description: >
  Load when coordinating an AI research loop: grounding research dialogue in
  evidence, designing the next investigation, supervising runs, reconvening on
  results, and maintaining durable research memory.
model-invocable: true
---

# Autoresearch

Use this skill to coordinate AI research as a disciplined loop. Own the
research frame, conversation state, experiment-design handoffs, interpretation,
artifact hygiene, and next-step decision. Delegate heavyweight design and
execution to the right Meridian specialists.

This package is ecosystem-native: reuse `meridian-dev-workflow` rather than
recreating its design, review, source-study, probing, and implementation
machinery.

## Loop States

Autoresearch is not a linear pipeline. Designing can reopen after any result,
surprise, failed run, literature finding, or human correction. Before acting,
identify the current loop state and load one or more matching resources when the
task needs procedural detail:

| State | Load | Use when |
|---|---|---|
| Research dialogue | `resources/research-dialogue.md` | Lead-owned user interaction: evidence-grounded design-tree walk for requirements, scope, constraints, and uncertainty |
| Experiment design | `resources/experiment-design.md` | Turning a branch into a stage brief, deciding whether to spawn `@design-lead`, comparing alternatives |
| Run supervision | `resources/run-supervision.md` | Monitoring or coordinating an active run without taking over implementation |
| Reconvene, record, decide | `resources/reconvene-record-decide.md` | Interpreting outputs, updating artifacts, promoting decisions, and choosing the next loop move |

If the user asks broadly, start with research dialogue unless a concrete result
or active run is already in hand.

## Core Autoresearch Invariant

Every loop should preserve the Karpathy-style autoresearch discipline:

- define a measurable goal or observation,
- use real data or real artifacts when the domain allows it,
- capture a baseline before claiming improvement,
- change one meaningful thing at a time,
- verify mechanically where possible,
- keep, discard, or branch based on evidence,
- log enough provenance that future loops can learn from the attempt,
- checkpoint memory during long or multi-attempt execution instead of keeping
  research state only in context.

When the work is wet-lab-adjacent or still pre-hypothesis, the verification
signal may be a design review, literature constraint, assay feasibility check,
or decision artifact rather than a benchmark number. Do not treat subjective
confidence as a metric; name the evidence type honestly.

## Artifact Layers

Maintain three layers of research memory. Use the project's configured paths and
names; do not hardcode package-specific paths unless the project provides them.

| Layer | Purpose | Contents |
|---|---|---|
| Program index | Cross-campaign state | Best official results, active campaigns, stage snapshots, durable pointers |
| Campaign narrative | Human interpretation | Hypotheses, designs, setups, results, surprises, next experiment IDs |
| Machine run ledger | Exhaustive run record | Run IDs, configs, metrics, logs, output directories |

Keep these layers distinct. The program index is compact and curated. The
campaign narrative explains why the result matters. The machine ledger preserves
every run without forcing full logs into human-facing summaries.

## Delegation Rule

Managers and leads coordinate. They should not silently become the experiment
implementation worker unless the user explicitly asks for direct execution.

Before handing execution to a runner, produce two separate blocks: a runner
handoff and a fenced `Goal to paste`. Tell the user to paste the goal back
unchanged or edited. Use the pasted goal as the execution contract; do not rely
on a paraphrase.

The runner handoff should include the loop state, research question, hypothesis
or design branch, stage gate, exact files to read, expected command or entrypoint
if known, output location, anti-goals, evidence of success, preflight sniff
test, autonomous execution boundaries, stop-and-report conditions, checkpoint
cadence, reviewer gates, and what summary should come back. After the user
approves the goal, execution is autonomous: the runner should not ask the user
mid-run unless the approved goal explicitly permits it.
