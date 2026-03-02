# Historical Concurrency Problems: Naive to Best-Known Approaches

Best solution always depends on assumptions. Each section states common progression.

## 1. Mutual Exclusion (Critical Section)

Problem:
- Multiple agents update shared state without corruption.

Naive:
- No synchronization.
- Disable interrupts (works only for kernel/single-core assumptions).

Major discoveries:
- Software-only mutual exclusion (Peterson, bakery algorithm).
- Hardware atomics (`test-and-set`, `compare-and-swap`) enable practical locks.
- Queue locks (ticket, MCS) improve fairness and scalability.

Modern best practice:
- Use high-level lock primitives unless proven bottleneck.
- Prefer lock partitioning/sharding before lock-free complexity.

## 2. Producer-Consumer Coordination

Problem:
- Bounded buffer without lost wakeups.

Naive:
- Busy waiting or ad hoc flags.

Major discoveries:
- Semaphores and condition variables formalize signaling.
- Monitor patterns reduce manual signaling mistakes.

Modern best practice:
- Bounded queues with explicit backpressure and cancellation.

## 3. Readers-Writers Tradeoff

Problem:
- High read concurrency with write correctness.

Naive:
- Single global mutex.

Major discoveries:
- Reader-writer locks.
- Fairness policies to avoid writer starvation.
- Read-copy-update (RCU), seqlocks for read-heavy systems.

Modern best practice:
- Choose by workload shape: rw-lock, RCU, or copy-on-write.

## 4. Deadlock

Problem:
- Circular waiting and permanent blocking.

Naive:
- Independent lock acquisition order.

Major discoveries:
- Coffman conditions and wait-for graph reasoning.
- Lock hierarchy/order, timeout/try-lock strategies.
- Banker-like avoidance under known resource bounds.

Modern best practice:
- Global lock ordering plus watchdog/failure diagnostics.

## 5. Livelock and Starvation

Problem:
- System active but makes no useful progress.

Naive:
- Aggressive retries without fairness.

Major discoveries:
- Exponential backoff.
- Fair queueing/turn-taking.
- Priority inheritance to mitigate inversion.

Modern best practice:
- Combine fairness policy with contention-aware backoff.

## 6. Memory Ordering and Reordering Bugs

Problem:
- Observed behavior differs from source-code order.

Naive:
- Assume sequential consistency on all hardware.

Major discoveries:
- Formal memory models (C/C++11, Java, Rust atomics).
- Acquire/Release semantics and fences.

Modern best practice:
- Use strongest ordering needed for correctness, no weaker.
- Validate with litmus tests and architecture-aware review.

## 7. Lock-Free Data Structures and Reclamation

Problem:
- Progress under contention without blocking.

Naive:
- CAS loops without safe memory reclamation.

Major discoveries:
- Linearizability as correctness criterion.
- ABA problem and solutions (tagged pointers, hazard pointers, epochs).

Modern best practice:
- Prefer mature libraries unless specific need justifies custom lock-free design.

## 8. Global Time and Event Ordering

Problem:
- No shared clock across distributed nodes.

Naive:
- Local wall-clock ordering.

Major discoveries:
- Lamport logical clocks.
- Vector clocks for concurrency detection.

Modern best practice:
- Use logical/causal metadata where causality matters.

## 9. Crash-Fault Consensus

Problem:
- Agreement with node failures and partitions.

Naive:
- Leader says value, followers trust blindly.

Major discoveries:
- FLP impossibility in asynchronous settings.
- Paxos safety under minimal assumptions.
- Raft improves understandability and implementation ergonomics.

Modern best practice:
- Well-tested consensus libraries and strong fault-injection testing.

## 10. Byzantine Generals

Problem:
- Agreement with arbitrary/malicious behavior.

Naive:
- Simple majority without authenticated protocol details.

Major discoveries:
- Byzantine agreement lower bounds and OM(m) formulations.
- Practical Byzantine Fault Tolerance (PBFT).
- Newer protocols (HotStuff-family) improve pipeline/latency characteristics.

Modern best practice:
- Use BFT only when threat model requires it; cost is significant.
- Define adversary model and quorum math explicitly.

## 11. Transactions and Atomic Commit

Problem:
- Multi-step operations across components.

Naive:
- Best-effort updates with no rollback protocol.

Major discoveries:
- Two-phase commit (2PC), then consensus-backed replication for stronger behavior.
- MVCC and serializability models.

Modern best practice:
- Limit cross-service transactions; use idempotency and saga patterns when suitable.

## 12. CAP and Consistency Tradeoffs

Problem:
- Partition tolerance forces consistency/availability decisions.

Naive:
- Promise strong consistency and full availability always.

Major discoveries:
- CAP framing and refined consistency taxonomies.
- Eventual consistency, causal consistency, linearizability distinctions.

Modern best practice:
- Make consistency contract explicit per API path and business invariant.
