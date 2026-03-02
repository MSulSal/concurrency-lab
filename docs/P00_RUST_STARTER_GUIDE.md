# P00 Rust Starter Guide

This is the minimum Rust you need to implement `P00` cleanly.

## 1. Suggested File Roles

```text
src/main.rs          -> parse CLI, call runner, handle exit code
src/runner.rs        -> run warmup/measured loops, compute median/p95
src/workloads/mod.rs -> workload registry and dispatch
src/workloads/*.rs   -> concrete workload implementations
```

## 2. First Data Types to Define

```rust
pub struct Config {
    pub workload: String,
    pub threads: Vec<u32>,
    pub iterations: u64,
    pub warmup: u32,
    pub runs: u32,
    pub csv_out: String,
}

pub struct RunResult {
    pub workload: String,
    pub threads: u32,
    pub iterations_per_thread: u64,
    pub total_ops: u64,
    pub elapsed_ns: u128,
    pub correct: bool,
}
```

Keep these aligned with `docs/P00_INTERFACE_CONTRACT.md`.

## 3. Recommended Implementation Order

1. Parse CLI flags into `Config`.
2. Implement `counter_single_thread`.
3. Implement one measured run path (no warmup yet).
4. Add warmup loop.
5. Add median/p95 helpers.
6. Add CSV writer.
7. Add `counter_mutex`.
8. Add `counter_atomic`.

## 4. Minimal Function Shape

```rust
pub fn run_workload_once(name: &str, threads: u32, iters: u64) -> Result<RunResult, String>;
pub fn run_matrix(cfg: &Config) -> Result<(), String>;
```

Start with string errors, then improve later.

## 5. Median and P95 (Practical Rule)

- Sort the values ascending.
- Median: middle element (or average of two middle values for even count).
- p95 index: `ceil(0.95 * n) - 1`, clamped to range.

Use this consistently for throughput and latency vectors.

## 6. Common Beginner Mistakes in P00

- Measuring setup time: start timer immediately before workload logic.
- Integer division errors: cast carefully when calculating throughput.
- Shared mutable state races: use `Mutex` or atomics, not raw shared `mut`.
- Missing correctness checks: always validate final count before recording result.
- Panic-driven flow: return `Result` from runner paths.

## 7. Quick Self-Check Before Commit

```powershell
cargo check --manifest-path lab/p00-baselines/Cargo.toml
cargo test --manifest-path lab/p00-baselines/Cargo.toml
```

If tests are not written yet, add at least one for metric helper logic (median/p95).
