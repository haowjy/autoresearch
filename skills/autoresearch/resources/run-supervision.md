# Run Supervision

Use this loop state while `@autoresearch-runner` or another project runner is
active. The goal is to protect interpretability and memory without hijacking
execution. After the goal is approved, the runner should execute autonomously and
use stop-and-report rather than mid-run user questions.

## Stay at Coordination Altitude

Do not rewrite the experiment mid-run unless the user or runner reports a clear
blocker. Track whether the run is still answering the stage brief. If it drifts,
record the drift and decide whether it becomes a calibration run,
infrastructure failure, protocol deviation, or a new design branch.

## Monitor for Classification Signals

Watch for signals that affect later interpretation:

- **Healthy run:** setup matches the stage brief and artifacts are being saved.
- **Preflight failure:** the short setup-and-signal sniff test shows inputs,
  instrumentation, logging, evaluator, or primary readout is not wired well
  enough for the long run to be interpretable.
- **Calibration run:** sizing, smoke-testing, threshold-setting, or debugging.
- **Infrastructure failure:** data, environment, command, logging, or runner
  failure prevents interpretation.
- **Protocol drift:** the setup changed enough that the original hypothesis no
  longer applies.
- **Early surprise:** a metric or behavior is unexpected enough to preserve even
  before the run finishes.

Classify; do not overinterpret. Conclusions belong after provenance is captured.

## Intervene Only for Interpretability

Intervene when it prevents wasted or unusable work:

- the preflight sniff test failed and a long run would waste compute,
- required artifacts are not being written,
- the runner is executing the wrong config, dataset, or protocol,
- the run no longer matches the stage brief,
- a cheap stop can save substantial compute after a clear infrastructure issue,
- the approved goal lacks a cost, delay, or interpretability tradeoff needed to
  continue safely; checkpoint state, stop, and return the tradeoff report unless
  the goal already authorizes an autonomous choice.

When intervening, record what changed and why so the reconvene step does not
misrepresent the setup.

## Memory and Review Cadence

For long-running or multi-attempt execution, define a cadence before the run
starts. A useful default is: write a checkpoint after the preflight sniff test,
after each meaningful attempt, before launching any materially longer job, and
when stopping. The checkpoint should capture current best evidence, failed or
calibration-only attempts, open risks, and the next intended action.

Use reviewers at gates, not continuously. Review gates are named milestones,
not routine memory checkpoints, unless the approved goal explicitly schedules a
review at a checkpoint. Independent review is most valuable before promoting a
result, when the metric/evaluator/data/baseline might change, when a surprising
result redirects the research tree, when cheating or metric gaming is plausible,
or after a fixed budget of attempts/time if the goal is still not converging.
