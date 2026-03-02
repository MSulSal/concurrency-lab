# Lab Notebook Template

Use one entry per project session. Keep it short, factual, and reproducible.

## Header

- Date:
- Project ID:
- Commit hash:
- Machine:
  - CPU:
  - Cores/threads:
  - RAM:
  - GPU:
  - OS:

## 1. Question

What exact concurrency question are you testing?

## 2. Hypothesis

What do you expect and why?

## 3. Baseline

- Implementation version:
- Correctness checks:
- Metrics collected:

## 4. Change

What changed from baseline? Include algorithm, data layout, or synchronization policy differences.

## 5. Results

- Throughput:
- Latency median:
- Latency p95:
- CPU utilization:
- GPU metrics (if relevant):

## 6. Correctness and Failure Cases

- New race/deadlock/livelock findings:
- Reproduction steps:
- Fix summary:

## 7. Interpretation

Explain why this result happened (scheduler, cache, memory order, network timing, warp divergence, etc.).

## 8. Threats to Validity

- Measurement noise:
- Uncontrolled variables:
- Missing cases:

## 9. Next Step

Single highest-value next experiment.
