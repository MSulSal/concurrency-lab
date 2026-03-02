# Career Value Map

This is a live document for translating lab progress into realistic career value.

## How to Use

After each meaningful project milestone:

1. Add evidence to this file.
2. Map evidence to the relevant level and role below.
3. Do not claim a level unless the evidence gate is met.

## Experience and Expertise Levels

### Level 0: Beginner (0-2 months)

You can claim:
- "I can build and run Rust projects with tests."
- "I understand basic concurrency terms and can implement simple benchmarks."

Evidence gate:
- `P00` complete with reproducible CSV benchmarks.
- At least 2 notebook entries with hypotheses and results.

### Level 1: Junior Systems Candidate (2-5 months)

You can claim:
- "I can implement thread-safe code with mutexes/condition variables."
- "I can diagnose basic deadlock/starvation issues."
- "I can compare synchronization strategies with real measurements."

Evidence gate:
- `P01` to `P05` complete.
- At least 1 reproduced failure bug and documented fix.
- Benchmark report comparing at least 2 synchronization approaches.

### Level 2: Early-Mid Concurrency Engineer (5-9 months)

You can claim:
- "I can implement async + thread-pool systems and reason about backpressure."
- "I understand memory ordering tradeoffs and lock-free basics."
- "I can explain safety/liveness and defend design choices with data."

Evidence gate:
- `P06` to `P11` complete.
- One lock-free structure implemented and stress-tested.
- One performance regression found and fixed with profiling evidence.

### Level 3: Mid-Senior Distributed Systems Engineer (9-14 months)

You can claim:
- "I can implement and evaluate consensus and fault-tolerant protocols."
- "I can reason about consistency models, partitions, and recovery behavior."
- "I can design for compute/storage/cache coordination tradeoffs."

Evidence gate:
- `P12` to `P24` complete.
- Fault-injection evidence for crash and partition scenarios.
- Clear consistency contract documented for at least one storage/cache project.

### Level 4: Senior/Staff Specialist Track (14+ months)

You can claim:
- "I can bridge CPU, async, distributed, and GPU concurrency models."
- "I can produce original technical contributions with reproducible evidence."
- "I can mentor others with principled engineering guidance."

Evidence gate:
- `P25` to `P32` complete.
- Public artifact (writeup/tool/benchmark set) with reproducibility instructions.
- At least one original contribution validated against baseline approaches.

## Role Mapping (Software and Adjacent)

### Software and Infrastructure Roles

- Backend/platform engineer:
  - Strong fit after Level 2.
  - Highest signal projects: `P06` to `P11`, `P19` to `P24`.

- Distributed systems/storage engineer:
  - Strong fit after Level 3.
  - Highest signal projects: `P14`, `P15`, `P21`, `P22`, `P23`, `P24`.

- SRE/performance engineer:
  - Strong fit after Level 2-3.
  - Highest signal projects: `P00`, `P01`, `P06`, `P20`, `P29`, `P30`.

- ML systems/performance engineer:
  - Strong fit after Level 3-4.
  - Highest signal projects: `P19`, `P20`, `P25` to `P29`.

- Security/distributed trust engineer:
  - Strong fit after Level 3.
  - Highest signal projects: `P17`, `P18`, `P24`, `P30`.

### Adjacent and Cross-Disciplinary Roles

- Quant/low-latency engineering:
  - Fit starts at Level 2, stronger at Level 3.
  - Highest signal projects: `P00`, `P10`, `P11`, `P29`.

- Robotics/autonomy systems:
  - Fit starts at Level 2.
  - Highest signal projects: `P06`, `P07`, `P09`, `P28`, `P30`.

- Industrial automation and control software:
  - Fit starts at Level 2.
  - Highest signal projects: `P03`, `P04`, `P09`, `P24`, `P30`.

- Research assistant (systems/performance/distributed):
  - Fit starts at Level 3.
  - Highest signal projects: `P14` to `P18`, `P25` to `P32`.

## Anti-Self-Deception Checks

Do not claim expertise from reading alone. Claim only when you have:

- implemented working code,
- reproduced at least one failure mode,
- measured and explained tradeoffs,
- documented assumptions and limits.

If you cannot explain failure behavior, you are not done.

## Live Evidence Log

Add one entry whenever a milestone materially changes your market value:

```text
YYYY-MM-DD | Project | Level Claim Impact | Evidence | Roles unlocked/strengthened
```

Starter entry:

- 2026-03-02 | P00 docs kickoff | preparing Level 0 | spec/runbook/interface/results templates complete | none yet (implementation pending)
