# P00 Interface Contract

This document fixes external behavior for the `P00` benchmark harness.

## 1. CLI Contract

Support these flags (long form required; short aliases optional):

```text
--workload <name|all>
--threads <csv>
--iterations <u64>
--warmup <u32>
--runs <u32>
--csv-out <path>
```

Defaults:
- `--workload all`
- `--threads 1,2,4,8`
- `--iterations 1000000`
- `--warmup 3`
- `--runs 10`
- `--csv-out bench/results/p00/results.csv`

## 2. Workload Names

Allowed names:
- `counter_single_thread`
- `counter_mutex`
- `counter_atomic`

Unknown names must return a non-zero exit code and print allowed values.

## 3. Exit Behavior

Return code:
- `0`: all requested benchmarks completed with correctness checks passing
- `1`: invalid CLI input
- `2`: runtime benchmark failure (thread panic, I/O error, etc.)
- `3`: correctness check failure

## 4. Workload Result Contract

Every workload run must provide:
- `workload` (string)
- `threads` (u32)
- `iterations_per_thread` (u64)
- `total_ops` (u64)
- `elapsed_ns` (u128)
- `correct` (bool)

Derived metrics computed by runner:
- `throughput_ops_per_sec`
- `latency_ns_per_op`

## 5. Invariants

- `total_ops == threads * iterations_per_thread` for shared-counter workloads.
- `elapsed_ns > 0`.
- `throughput_ops_per_sec > 0` when `correct=true`.
- if any measured run returns `correct=false`, the configuration result is invalid.

## 6. Minimal Terminal Output Shape

For each `(workload, threads)`:

```text
[P00] workload=<name> threads=<n> iterations=<n>
correct=<true|false> expected_ops=<n>
median_throughput_ops_per_sec=<value> p95_throughput_ops_per_sec=<value>
median_latency_ns_per_op=<value> p95_latency_ns_per_op=<value>
```

## 7. Compatibility Rule

If implementation details change, keep this contract stable so downstream docs and scripts remain valid.
