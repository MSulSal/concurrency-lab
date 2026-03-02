# Setup

This lab assumes Windows with a dedicated NVIDIA GPU (your environment), plus optional WSL2.

## 1. Install required tools

### Core
- `git`
- `rustup` (stable toolchain)
- `llvm` or `Visual Studio Build Tools` (C/C++ toolchain)
- `python` 3.12+
- `just` (optional command runner)

### GPU
- Latest NVIDIA driver
- CUDA Toolkit (match your driver compatibility)
- Nsight Systems / Nsight Compute

### Optional but recommended
- WSL2 with Ubuntu (for easier Linux-style profiling and tooling)
- `perf`, `flamegraph`, `valgrind` (inside WSL2/Linux)

## 2. Verify installs

Run and record outputs in your notebook:

```powershell
git --version
rustc --version
cargo --version
cl
nvcc --version
nvidia-smi
python --version
```

## 3. Create initial folder layout

```text
lab/
  p00-baselines/
  p01-cpu-memory/
  p02-counter-race/
  p03-producer-consumer/
  p04-readers-writers/
  p05-deadlock-lab/
  p06-thread-pool/
  p07-async-echo/
  p08-mini-executor/
  p09-backpressure-cancel/
  p10-lockfree-queue/
  p11-memory-litmus/
  p12-lamport-clocks/
  p13-vector-clocks/
  p14-raft/
  p15-paxos/
  p16-flp-failure-detector/
  p17-byzantine-generals/
  p18-pbft-style/
  p19-distributed-scheduler/
  p20-stream-processing/
  p21-replicated-kv/
  p22-storage-engine/
  p23-cache-lease-sim/
  p24-transactions/
  p25-cuda-reduction/
  p26-warp-divergence/
  p27-cuda-streams/
  p28-cpu-gpu-hybrid/
  p29-perf-report/
  p30-reliability-harness/
  p31-original-contribution/
  p32-public-defense/
notes/
bench/
scripts/
```

## 4. Ground rules for every project

- Start with a naive implementation first.
- Define correctness property before coding (for example: no lost updates, at-most-once processing).
- Add stress test and deterministic test.
- Benchmark before and after improvements.
- Write one page of findings.

## 5. Measurement standards

- Record hardware details (`CPU`, core count, RAM, GPU model).
- Use the same input sizes across versions.
- Run at least 10 trials, report median and p95.
- Track throughput, latency, tail latency, and CPU utilization where relevant.

## 6. First milestone

You are ready for `P00` when:
- Toolchain commands all work.
- CUDA is visible in `nvidia-smi`.
- Folder layout exists.
- You opened your first notebook entry.
