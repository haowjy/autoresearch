# Reconvene, Record, Decide

Use this loop state when a run finishes, fails, or produces a surprising
observation. Interpret the evidence, update research memory, and choose the next
loop move.

## Classify the Result

Classify before writing conclusions:

- **Calibration-only:** debugging, sizing, smoke test, or threshold-setting. Skip
  official promotion unless the project or user says otherwise.
- **Infrastructure failure:** setup broke before the hypothesis was tested.
  Record enough to avoid repeating it; do not draw scientific conclusions.
- **Official candidate:** setup matches the stage brief and can be compared to
  the current best or gate.
- **Surprising result:** behavior matters even if the run is not a new best.
  Preserve the setup and observation as a possible branch.
- **Design failure:** the result shows the experiment could not answer the
  intended question. Return to experiment design rather than forcing a metric
  interpretation.

## Write the Experiment Entry

A useful entry answers:

1. Hypothesis or design branch.
2. Setup: commit, config, parameters, data, protocol, and runner command when
   relevant.
3. Result: metrics, observations, run directory, report path, or design review.
4. Interpretation: what changed in the research state.
5. Surprises, failures, or protocol deviations.
6. Next experiment IDs, design branches, or stop condition.

Prefer links or paths to bulky artifacts over pasted logs. Use the project's
link style and path conventions.

## Update the Right Layer

- Program index: update only for official bests, stage pass/fail snapshots,
  campaign state, or durable headline notes.
- Campaign narrative: record interpretation, surprises, failed hypotheses,
  design branches, and follow-up ideas.
- Machine run ledger: ensure the run ID, config, metrics, logs, and output path
  are preserved.
- KB or decisions: promote only conclusions that should guide future campaigns.

Keep speculation in the campaign narrative until evidence makes it reusable.

## Decide the Next Move

Choose one:

- **Return to dialogue:** the result changed the research tree or human priority.
- **Return to design:** alternatives, controls, or feasibility need redesign.
- **Iterate mechanically:** the metric is clear and the loop can keep improving.
- **Confirm:** the result is promising but needs replication or a confirmation
  run before promotion.
- **Promote:** the result is durable enough for the program index or KB.
- **Stop:** no useful next test is justified.

Do not default to another run. A loop is healthy only when each iteration changes
what the team knows.
