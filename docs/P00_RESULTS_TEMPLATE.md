# P00 Results Template

Use this file after running the `P00` matrix.

## Run Metadata

- Date:
- Commit:
- OS:
- CPU model:
- Logical cores:
- Rust version:
- Notes:

## Configuration

- Workloads: `counter_single_thread`, `counter_mutex`, `counter_atomic`
- Thread counts: `1,2,4,8`
- Iterations per thread: `1_000_000`
- Warmup runs: `3`
- Measured runs: `10`
- CSV path:

## Summary Table

| Workload | Threads | Median Throughput (ops/s) | p95 Throughput (ops/s) | Median Latency (ns/op) | p95 Latency (ns/op) | Correct |
|---|---|---|---|---|---|---|
| counter_single_thread | 1 |  |  |  |  |  |
| counter_mutex | 1 |  |  |  |  |  |
| counter_mutex | 2 |  |  |  |  |  |
| counter_mutex | 4 |  |  |  |  |  |
| counter_mutex | 8 |  |  |  |  |  |
| counter_atomic | 1 |  |  |  |  |  |
| counter_atomic | 2 |  |  |  |  |  |
| counter_atomic | 4 |  |  |  |  |  |
| counter_atomic | 8 |  |  |  |  |  |

## Key Findings

1. Highest throughput configuration:
2. Worst tail-latency configuration:
3. Correctness failures:
4. One bottleneck hypothesis:

## P01 Hypothesis

What you expect false sharing to show and why:
