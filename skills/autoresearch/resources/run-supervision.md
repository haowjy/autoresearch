# Run Supervision

Use this loop state while `@autoresearch-runner` or another project runner is
active. The goal is to protect interpretability without hijacking execution.

## Stay at Coordination Altitude

Do not rewrite the experiment mid-run unless the user or runner reports a clear
blocker. Track whether the run is still answering the stage brief. If it drifts,
record the drift and decide whether it becomes a calibration run,
infrastructure failure, protocol deviation, or a new design branch.

## Monitor for Classification Signals

Watch for signals that affect later interpretation:

- **Healthy run:** setup matches the stage brief and artifacts are being saved.
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

- required artifacts are not being written,
- the runner is executing the wrong config, dataset, or protocol,
- the run no longer matches the stage brief,
- a cheap stop can save substantial compute after a clear infrastructure issue,
- the user must choose between cost, delay, and interpretability.

When intervening, record what changed and why so the reconvene step does not
misrepresent the setup.
