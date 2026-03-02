# Project Ladder

Each project has:
- `Problem`: what you are solving.
- `Naive baseline`: intentionally basic first attempt.
- `Target`: stronger design to reach.
- `Evidence`: tests and benchmarks required.

## Foundation Track (P00-P05)

### P00. Benchmark Harness
- Problem: measure concurrency changes credibly.
- Naive baseline: single timing run with wall clock only.
- Target: repeatable benchmark tool with median/p95 and CSV output.
- Evidence: same binary measured 10+ runs with stable variance.

### P01. False Sharing Demo
- Problem: why independent counters can still contend.
- Naive baseline: adjacent counters in one struct.
- Target: padded/aligned counters plus comparison.
- Evidence: throughput delta and cache-miss profile.

### P02. Counter Race
- Problem: lost updates under contention.
- Naive baseline: unsynchronized shared integer.
- Target: mutex, atomic, and sharded-counter variants.
- Evidence: correctness checks plus throughput under thread scaling.

### P03. Producer-Consumer Queue
- Problem: bounded buffer coordination.
- Naive baseline: busy waiting.
- Target: condition-variable or semaphore-based queue.
- Evidence: no drops/duplicates; latency under load.

### P04. Readers-Writers
- Problem: maximize read concurrency while preserving write correctness.
- Naive baseline: single mutex for all access.
- Target: rw-lock and fair policy variant.
- Evidence: starvation tests and mixed-workload benchmark.

### P05. Dining Philosophers + Deadlock Lab
- Problem: deadlock and progress failures.
- Naive baseline: symmetric lock order causing deadlock.
- Target: lock ordering or arbitrator strategy.
- Evidence: forced deadlock reproduction and fix verification.

## Systems Concurrency Track (P06-P11)

### P06. Thread Pool
- Problem: task scheduling with bounded worker threads.
- Naive baseline: spawn per task.
- Target: work queue + worker reuse + graceful shutdown.
- Evidence: throughput and latency under bursty load.

### P07. Async Echo Server
- Problem: high-concurrency I/O.
- Naive baseline: blocking thread-per-connection.
- Target: async runtime-based server.
- Evidence: connection scale benchmark and resource comparison.

### P08. Mini Executor
- Problem: understand async internals.
- Naive baseline: simple polling loop.
- Target: task waker queue + cooperative scheduling.
- Evidence: runnable examples + fairness behavior notes.

### P09. Backpressure and Cancellation
- Problem: overload behavior.
- Naive baseline: unbounded queue.
- Target: bounded queue + cancellation propagation.
- Evidence: overload test showing controlled degradation.

### P10. Lock-Free Queue
- Problem: contention without global lock.
- Naive baseline: mutex queue.
- Target: Michael-Scott style lock-free queue.
- Evidence: linearizability reasoning + stress/fuzz tests.

### P11. Memory Ordering Litmus Lab
- Problem: counterintuitive reorderings.
- Naive baseline: assume sequential consistency everywhere.
- Target: litmus tests with explicit memory orders.
- Evidence: documented anomalies and corrected ordering choices.

## Distributed Coordination Track (P12-P18)

### P12. Lamport Clock Simulator
- Problem: event ordering without global time.
- Naive baseline: local timestamps only.
- Target: Lamport clocks with causality visualizer.
- Evidence: trace proving happened-before properties.

### P13. Vector Clock Chat
- Problem: concurrency detection across nodes.
- Naive baseline: Lamport-only ordering.
- Target: vector clock concurrency detection.
- Evidence: detection of concurrent vs causally-related events.

### P14. Raft Mini
- Problem: crash-fault consensus.
- Naive baseline: single leader without election safety checks.
- Target: leader election + replicated log + commit rules.
- Evidence: partition/failure injection with safety preserved.

### P15. Paxos Mini
- Problem: compare consensus formulations.
- Naive baseline: one-shot happy-path agreement only.
- Target: multi-round proposer/acceptor logic.
- Evidence: side-by-side trace comparison with Raft behavior.

### P16. FLP and Failure Detector Experiment
- Problem: impossibility boundaries.
- Naive baseline: assume eventual delivery and progress.
- Target: simulation showing liveness failure under asynchronous faults.
- Evidence: written analysis of assumptions needed for progress.

### P17. Byzantine Generals Toy Model
- Problem: malicious participants.
- Naive baseline: majority vote with no authentication.
- Target: OM(m) style simulation with traitors.
- Evidence: scenarios showing when agreement is impossible/possible.

### P18. PBFT-Style Prototype
- Problem: practical BFT replication.
- Naive baseline: ignore view changes and quorum thresholds.
- Target: primary/backup phases with quorum validation.
- Evidence: fault-injection run showing tolerated Byzantine behavior.

## Modern Distributed Systems Breadth Track (P19-P24)

### P19. Distributed Compute Scheduler
- Problem: schedule many tasks across workers with stragglers and failures.
- Naive baseline: centralized FIFO scheduler.
- Target: work-stealing + retry + idempotent task model.
- Evidence: tail latency and throughput under skewed workloads.

### P20. Stream Processing Pipeline
- Problem: continuous event processing with ordering and backpressure.
- Naive baseline: at-least-once processing with duplicates.
- Target: partitioned workers, checkpoints, and replay-aware semantics.
- Evidence: correctness under crash-recovery and load spikes.

### P21. Replicated Key-Value Store
- Problem: durable low-latency storage under node failures.
- Naive baseline: single-node hash map with no WAL.
- Target: WAL + replication + quorum read/write modes.
- Evidence: failover tests and consistency-latency tradeoff report.

### P22. Storage Engine Internals
- Problem: write-heavy storage performance over time.
- Naive baseline: append log with full scan reads.
- Target: memtable + SSTable compaction model (LSM-style mini engine).
- Evidence: read/write amplification measurements and compaction impact.

### P23. Distributed Cache and Lease Simulator
- Problem: stale reads and invalidation races in cached distributed data.
- Naive baseline: TTL-only cache with no coordination.
- Target: lease-based coherence/invalidation protocol simulation.
- Evidence: stale-read rate and invalidation-latency measurements.

### P24. Transaction and Workflow Semantics
- Problem: multi-step consistency across services.
- Naive baseline: best-effort writes without compensation.
- Target: compare 2PC and saga-based workflows with idempotency keys.
- Evidence: failure matrix showing correctness and recovery behavior.

## GPU and Heterogeneous Track (P25-P29)

### P25. CUDA Reduction
- Problem: parallel aggregation efficiently.
- Naive baseline: CPU reduction only.
- Target: optimized shared-memory CUDA reduction.
- Evidence: speedup vs CPU across input sizes.

### P26. Warp Divergence Lab
- Problem: branch divergence cost.
- Naive baseline: branch-heavy kernel.
- Target: divergence-aware kernel refactor.
- Evidence: Nsight report comparing occupancy and execution efficiency.

### P27. Streamed Pipeline
- Problem: hide transfer latency.
- Naive baseline: synchronous copy-then-compute.
- Target: overlapping transfers and kernels using streams.
- Evidence: throughput improvement with timeline capture.

### P28. CPU+GPU Hybrid Service
- Problem: heterogeneous scheduling.
- Naive baseline: all work pinned to one processor type.
- Target: routing policy between CPU threads and GPU kernels.
- Evidence: policy comparison under mixed workloads.

### P29. End-to-End Performance Report
- Problem: convert experiments into defendable conclusions.
- Naive baseline: ad hoc benchmarks.
- Target: structured report with methodology, threats, and replication steps.
- Evidence: publishable markdown report and scripts.

## Capstone Track (P30-P32)

### P30. Reliability Harness
- Problem: concurrency bugs hide in rare schedules.
- Naive baseline: happy-path unit tests.
- Target: randomized scheduler + fault injector.
- Evidence: at least one bug found and fixed.

### P31. Original Contribution
- Problem: add new value.
- Naive baseline: reimplementation only.
- Target: one novel algorithmic, tooling, or empirical contribution.
- Evidence: benchmark data and reproducible scripts.

### P32. Public Defense
- Problem: communicate and defend work.
- Naive baseline: code without narrative.
- Target: technical writeup + architecture diagrams + results.
- Evidence: document that can support interview-level deep discussion.
