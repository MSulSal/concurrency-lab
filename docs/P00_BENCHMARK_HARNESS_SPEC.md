# P00 Benchmark Harness Spec

This is the coding target for `P00`.

## Objective

Create a repeatable benchmark harness that can compare concurrency strategies fairly.

Execution and evidence format are defined in [P00_RUNBOOK.md](./P00_RUNBOOK.md).

## Required Deliverables

1. CLI benchmark runner (`Rust`) with configurable:
- workload name
- thread count
- iteration count
- warmup runs
- measured runs

2. Output formats:
- human-readable summary in terminal
- CSV line output for later plotting

3. Metrics per run:
- total operations
- elapsed time
- throughput (ops/sec)
- latency proxy (ns/op)

4. Aggregate report:
- median throughput
- p95 throughput
- median latency proxy
- p95 latency proxy

5. Reproducibility:
- print machine metadata block (CPU model, logical cores, OS, timestamp)
- persist config values with each CSV row

## Initial Workloads

Start with one workload, then expand:

- `counter_single_thread`: increment local counter `N` times.

Then add:

- `counter_mutex`: shared counter with `Mutex` across `T` threads.
- `counter_atomic`: shared counter with atomics across `T` threads.

## Correctness Gates

- Validate final counts match expected operations.
- Fail fast if any run violates correctness.
- Do not report performance result as valid if correctness fails.

## Suggested Layout

```text
lab/
  p00-baselines/
    Cargo.toml
    src/
      main.rs
      runner.rs
      workloads/
        mod.rs
        counter_single_thread.rs
        counter_mutex.rs
        counter_atomic.rs
bench/
  results/
    p00/
scripts/
  p00-run.ps1
```

## Run Matrix (first pass)

Run with:

- thread counts: `1, 2, 4, 8`
- iterations per thread: `1_000_000`
- warmup runs: `3`
- measured runs: `10`

## Done Criteria for P00

- CLI can run all initial workloads from one command.
- CSV output exists and includes all required columns.
- Median and p95 are printed correctly.
- At least one result file is saved under `bench/results/p00/`.
- Notebook entry completed using lab template.

## Next Project Hand-off

After `P00` is done:

- promote reusable harness utilities for `P01` onward
- start `P01` false-sharing demo using the same runner and result format
