# P00 Runbook

This runbook defines exactly how to execute and validate `P00`.

## 1. Required CSV Schema

Each measured run must emit one CSV row with these columns:

```text
timestamp_utc,project_id,workload,threads,iterations_per_thread,warmup_runs,measured_runs,run_index,total_ops,elapsed_ns,throughput_ops_per_sec,latency_ns_per_op,correct,host_os,cpu_model,logical_cores
```

Notes:
- `run_index` starts at `1` and increments for measured runs only.
- `correct` is `true` only when result validation passes.
- `total_ops` should equal expected operations for the workload.

## 2. Required Terminal Summary

For each workload/thread configuration, print:
- expected operations
- measured run count
- median throughput
- p95 throughput
- median latency
- p95 latency
- correctness status

## 3. First Required Matrix

Run:
- workloads: `counter_single_thread`, `counter_mutex`, `counter_atomic`
- thread counts: `1,2,4,8`
- iterations per thread: `1_000_000`
- warmup runs: `3`
- measured runs: `10`

## 4. Evidence Artifacts

Store these under `bench/results/p00/`:
- CSV file for full matrix
- one terminal output capture (markdown or text)
- one short findings note:
  - highest throughput workload
  - correctness failures observed (if any)
  - one hypothesis for `P01`
- completed [P00_RESULTS_TEMPLATE.md](./P00_RESULTS_TEMPLATE.md)

## 5. Done Check

`P00` is done only if:
- all runs are `correct=true`
- CSV schema is complete and consistent
- median/p95 metrics are reported
- evidence artifacts are present
