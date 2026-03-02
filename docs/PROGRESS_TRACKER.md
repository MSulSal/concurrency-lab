# Progress Tracker

Use this file as the source of truth for commit-wise progress.

## Workflow Rules

1. Work one project ID at a time (`P00`, `P01`, ...).
2. Make atomic commits only (one meaningful change per commit).
3. Update this file in the same commit when status changes.
4. Do not mark `done` without tests + benchmark evidence noted.

## Commit Convention

Use:

```text
PXX(scope): short summary
```

Examples:
- `P03(queue): add bounded buffer with condvar signaling`
- `P14(raft): enforce election timeout randomization`
- `P21(kv): add WAL replay on startup`

## Status Values

- `todo`
- `in_progress`
- `blocked`
- `done`

## Project Board

| Project | Title | Status | Branch | Last Commit | Notes |
|---|---|---|---|---|---|
| P00 | Benchmark Harness | in_progress | main | - | doc kickoff complete; code scaffold + first benchmark pending |
| P01 | False Sharing Demo | todo | - | - | - |
| P02 | Counter Race | todo | - | - | - |
| P03 | Producer-Consumer Queue | todo | - | - | - |
| P04 | Readers-Writers | todo | - | - | - |
| P05 | Dining Philosophers + Deadlock Lab | todo | - | - | - |
| P06 | Thread Pool | todo | - | - | - |
| P07 | Async Echo Server | todo | - | - | - |
| P08 | Mini Executor | todo | - | - | - |
| P09 | Backpressure and Cancellation | todo | - | - | - |
| P10 | Lock-Free Queue | todo | - | - | - |
| P11 | Memory Ordering Litmus Lab | todo | - | - | - |
| P12 | Lamport Clock Simulator | todo | - | - | - |
| P13 | Vector Clock Chat | todo | - | - | - |
| P14 | Raft Mini | todo | - | - | - |
| P15 | Paxos Mini | todo | - | - | - |
| P16 | FLP and Failure Detector Experiment | todo | - | - | - |
| P17 | Byzantine Generals Toy Model | todo | - | - | - |
| P18 | PBFT-Style Prototype | todo | - | - | - |
| P19 | Distributed Compute Scheduler | todo | - | - | - |
| P20 | Stream Processing Pipeline | todo | - | - | - |
| P21 | Replicated Key-Value Store | todo | - | - | - |
| P22 | Storage Engine Internals | todo | - | - | - |
| P23 | Distributed Cache and Lease Simulator | todo | - | - | - |
| P24 | Transaction and Workflow Semantics | todo | - | - | - |
| P25 | CUDA Reduction | todo | - | - | - |
| P26 | Warp Divergence Lab | todo | - | - | - |
| P27 | Streamed Pipeline | todo | - | - | - |
| P28 | CPU+GPU Hybrid Service | todo | - | - | - |
| P29 | End-to-End Performance Report | todo | - | - | - |
| P30 | Reliability Harness | todo | - | - | - |
| P31 | Original Contribution | todo | - | - | - |
| P32 | Public Defense | todo | - | - | - |

## Session Log Template

Append one line per working session:

```text
YYYY-MM-DD | PXX | start_commit..end_commit | result | next action
```

## Session Log

- 2026-03-02 | P00 | TBD..TBD | started | implement benchmark harness scaffold and first sample benchmark
