# Distributed Systems Coverage Matrix

This matrix makes the distributed scope explicit across compute, storage, memory, and coordination layers.

| Domain | Core Questions | Projects | Deliverable |
|---|---|---|---|
| Distributed compute | How do tasks schedule, rebalance, and recover under stragglers/failures? | `P19`, `P20` | Scheduler + stream pipeline with failure tests |
| Messaging and logs | What guarantees exist for ordering, retries, deduplication, and backpressure? | `P09`, `P20`, `P21` | Semantics report (at-most/at-least/exactly-once tradeoffs) |
| Replicated storage | How do durability, replication, and compaction affect latency and correctness? | `P21`, `P22` | Mini replicated KV + LSM-style storage prototype |
| Consistency and transactions | What invariants need linearizability vs eventual consistency vs compensation? | `P21`, `P24` | Quorum vs transaction behavior matrix |
| Distributed memory/cache | How do leases, invalidations, and staleness windows shape correctness? | `P23` | Cache coherence simulator and stale-read analysis |
| Coordination/control plane | How do elections, lock services, and quorum systems behave under partitions? | `P12` to `P18` | Raft/Paxos/BFT simulations with fault injection |
| Failure and recovery | Which guarantees survive crash, partition, and Byzantine faults? | `P14` to `P18`, `P24`, `P30` | Fault matrix with reproduced failures and fixes |
| Observability/verification | How do we prove behavior beyond happy-path tests? | `P30`, `P32` | Deterministic or adversarial test evidence and defense doc |

## Modern systems you will be able to discuss

- Compute: batch schedulers, stream processors, actor/work-stealing runtimes.
- Storage: key-value stores, log-structured engines, quorum replication, multi-region tradeoffs.
- Memory path: distributed caches, lease protocols, remote-memory trends (RDMA/disaggregation concepts).
- Coordination: consensus, leader election, replicated state machines, and BFT when needed.

## Scope rule

Every distributed project must include:

1. Fault model (`crash`, `partition`, or `Byzantine`).
2. Consistency target (for example `linearizable`, `sequential`, `eventual`).
3. Measured tradeoff (latency/throughput/availability/cost).
