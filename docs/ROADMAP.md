# End-to-End Roadmap

This roadmap is project-led and cumulative. Each phase ends with a concrete artifact.

Total duration target: `10 to 18 months` depending on pace.

## Phase 0: Orientation and Baselines (1 week)

Focus:
- Tooling, benchmarking discipline, and lab process.

Output:
- `P00` benchmark harness and notebook workflow.

You must be able to explain:
- Throughput vs latency vs tail latency.
- Why benchmarks lie and how to reduce noise.

## Phase 1: CPU and Shared Memory Foundations (4 to 6 weeks)

Focus:
- Processes, threads, caches, context switches, false sharing, memory hierarchy.
- Data races and race-condition debugging.

Output:
- Microbenchmarks showing cache-line effects and contention collapse.

You must be able to explain:
- Why single-core code assumptions break under weak memory and cache coherence.
- Why "it works on my machine" is common in concurrent code.

## Phase 2: Synchronization Patterns (5 to 7 weeks)

Focus:
- Mutexes, condition variables, semaphores, barriers, rw-locks.
- Classic problems: producer-consumer, readers-writers, dining philosophers.
- Deadlock, livelock, starvation, priority inversion.

Output:
- Correct, tested implementations of core synchronization problems with failure-case demos.

You must be able to explain:
- Safety vs liveness.
- Progress guarantees and fairness tradeoffs.

## Phase 3: Memory Models and Lock-Free Design (6 to 8 weeks)

Focus:
- Atomic operations, memory ordering (Acquire/Release/SeqCst/Relaxed).
- ABA problem, hazard pointers, epoch reclamation.
- Linearizability and lock-free/wait-free progress classes.

Output:
- Lock-free queue/stack with correctness tests and benchmark comparison to mutex versions.

You must be able to explain:
- Why atomics are not enough without a memory-order model.
- When lock-free wins and when it loses.

## Phase 4: Async, Event Loops, and Runtime Design (4 to 6 weeks)

Focus:
- Thread-per-request vs event-driven async.
- Futures, tasks, cancellation, backpressure.
- Building a minimal executor and reactor model.

Output:
- Custom async runtime prototype and benchmarked I/O server.

You must be able to explain:
- Async concurrency vs parallelism.
- Why async can still deadlock or starve.

## Phase 5: Distributed Coordination and Consensus (8 to 12 weeks)

Focus:
- Logical time, causality, total order, clocks.
- Replication, leader election, log replication.
- Paxos, Raft, FLP impossibility, CAP tradeoffs.
- Byzantine fault tolerance and practical protocols.

Output:
- Simulated Raft and Paxos implementations.
- Byzantine broadcast or PBFT-style mini implementation under injected faults.

You must be able to explain:
- Crash fault vs Byzantine fault assumptions.
- Why consensus safety can hold while liveness fails under partitions.

## Phase 6: Modern Distributed Systems Breadth (8 to 12 weeks)

Focus:
- Distributed compute systems: job scheduling, work stealing, batch and stream dataflows.
- Distributed storage systems: WAL, replication, quorum reads/writes, compaction, anti-entropy.
- Distributed memory and coordination: caching, leases, invalidation, coordination services, and RDMA/disaggregated memory concepts.
- Messaging and logs: queue semantics, ordering, idempotency, backpressure, exactly-once myths and realities.

Output:
- Mini distributed scheduler, mini replicated key-value store, and cache-coherence/invalidation simulator.
- Comparative report for compute/storage/memory designs under failure and load.

You must be able to explain:
- How concurrency semantics differ between compute pipelines, storage engines, and memory/cache layers.
- Where real systems choose weaker guarantees for throughput or availability, and why.

## Phase 7: GPU Concurrency and Heterogeneous Systems (5 to 7 weeks)

Focus:
- SIMT model, warps, occupancy, memory coalescing.
- Host-device synchronization, streams, overlapping transfer/compute.
- CPU-GPU pipeline design.

Output:
- CUDA kernels for at least two workloads (for example reduction + graph traversal).
- CPU-threaded vs GPU-accelerated benchmark report.

You must be able to explain:
- When GPU parallelism dominates and when transfer overhead kills gains.
- How CPU and GPU concurrency models differ fundamentally.

## Phase 8: Verification, Testing, and Observability (3 to 5 weeks)

Focus:
- Model checking mindset (state-space exploration).
- Deterministic schedulers, randomized stress tests, fault injection.
- Tracing and distributed observability.

Output:
- Reproducible bug case and proof of fix using deterministic replay or model checks.

You must be able to explain:
- Why tests that pass are weak evidence without adversarial scheduling.

## Phase 9: Original Contribution (6 to 10 weeks)

Focus:
- Produce something new: not a tutorial copy.

Possible contribution targets:
- Novel benchmark harness for comparing sync strategies under realistic contention.
- Improved educational visualization for memory-order anomalies.
- Experimental variant of a queue, scheduler, or BFT optimization with measured tradeoffs.
- Deep article series that synthesizes CPU, async, distributed, and GPU models in one framework.

Output:
- Public artifact: GitHub release, writeup, reproducible scripts, and results.

## Weekly cadence

Use this loop each week:

1. Read one core source (paper/chapter/spec).
2. Implement naive baseline.
3. Implement improved version.
4. Benchmark and profile.
5. Write one-page technical note.
6. Capture open questions for next week.

## Graduation bar

You are "discussion-ready" with experts when you can:
- State system assumptions before proposing solutions.
- Derive which guarantees are possible vs impossible.
- Compare competing designs using correctness and performance evidence.
- Defend failure behavior (not only happy-path throughput).
- Bridge CPU, async, distributed compute, distributed storage, and GPU tradeoffs in one coherent model.
