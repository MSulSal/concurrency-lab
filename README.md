# Concurrency Lab

This repo is a project-first curriculum to learn concurrency from first principles to research-grade depth.

Goal:
- Build deep intuition from CPU execution to distributed consensus and GPU parallelism.
- Cover modern distributed system design across compute, storage, and memory paths.
- Implement major concurrency patterns and historical solutions yourself.
- Finish with publishable artifacts (benchmarks, writeups, and at least one original contribution).

## Why this stack

Primary language: `Rust`
- Safe systems programming with explicit ownership and strong concurrency primitives.
- Lets you push into lock-free and low-level performance work without normal C/C++ footguns.

Secondary language: `C++ + CUDA`
- Needed for direct NVIDIA GPU programming and understanding common production HPC stacks.

Support language: `Python`
- Plotting, data analysis, and quick experiment orchestration.

## Repository docs

- [Roadmap](./docs/ROADMAP.md): end-to-end plan (foundation to capstone).
- [Setup](./docs/SETUP.md): machine/tooling setup for Windows + NVIDIA.
- [Projects](./docs/PROJECTS.md): sequential build list of labs and systems.
- [Progress Tracker](./docs/PROGRESS_TRACKER.md): commit-wise board and session log.
- [Distributed Systems Matrix](./docs/DISTRIBUTED_SYSTEMS_MATRIX.md): explicit coverage map for compute, storage, memory, messaging, and coordination.
- [Historical Problems](./docs/HISTORICAL_PROBLEMS.md): naive-to-best solution map for classic problems.
- [Reading List](./docs/READING_LIST.md): core papers and books by phase.
- [Lab Notebook Template](./docs/LAB_NOTEBOOK_TEMPLATE.md): how to log experiments and findings.

## Definition of done

You can:
- Explain tradeoffs between threads, async, actors, lock-free, and GPU kernels with concrete examples.
- Reason about memory ordering and correctness properties (safety, liveness, linearizability).
- Implement and benchmark shared-memory and distributed protocols.
- Defend design choices in terms of model assumptions (fault model, consistency model, hardware model).
- Contribute one new result: benchmark dataset, algorithm variant, tooling improvement, or explanatory article.

## Start now

1. Complete [Setup](./docs/SETUP.md).
2. Read [Roadmap](./docs/ROADMAP.md) and [Projects](./docs/PROJECTS.md).
3. Create `lab/` folders described in Setup.
4. Start project `P00` and open your first notebook entry.
