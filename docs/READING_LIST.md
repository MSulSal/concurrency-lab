# Reading List (Primary Sources First)

Use this list with the roadmap phases. Prefer reading original papers/specs before summaries.

## Phase 1-2: Foundations

- Edsger W. Dijkstra, "Cooperating Sequential Processes" (1965).
- C. A. R. Hoare, "Monitors: An Operating System Structuring Concept" (1974).
- Maurice Herlihy and Nir Shavit, *The Art of Multiprocessor Programming*.
- Remzi and Andrea Arpaci-Dusseau, *Operating Systems: Three Easy Pieces* (threads/locks chapters).

## Phase 3: Memory Models and Lock-Free

- Leslie Lamport, "How to Make a Multiprocessor Computer That Correctly Executes Multiprocess Programs" (1979).
- ISO C++ memory model references (C++11 onward).
- Rust atomics and memory ordering docs (`std::sync::atomic`).
- Maurice Herlihy and Jeannette Wing, "Linearizability: A Correctness Condition for Concurrent Objects" (1990).
- Maged Michael and Michael Scott, "Simple, Fast, and Practical Non-Blocking and Blocking Concurrent Queue Algorithms" (1996).

## Phase 4: Async Runtime Design

- Reactor pattern references and event loop architecture docs.
- Rust async book and Tokio internals documentation.
- "Structured Concurrency" design discussions (language/runtime dependent).

## Phase 5: Distributed Concurrency and Consensus

- Leslie Lamport, "Time, Clocks, and the Ordering of Events in a Distributed System" (1978).
- Leslie Lamport, "The Part-Time Parliament" (1998) and "Paxos Made Simple" (2001).
- Diego Ongaro and John Ousterhout, "In Search of an Understandable Consensus Algorithm (Raft)" (2014).
- Fischer, Lynch, Paterson, "Impossibility of Distributed Consensus with One Faulty Process" (1985).
- Miguel Castro and Barbara Liskov, "Practical Byzantine Fault Tolerance" (1999).
- Leslie Lamport, Robert Shostak, Marshall Pease, "The Byzantine Generals Problem" (1982).

## Phase 6: Modern Distributed Systems (Compute, Storage, Memory)

- Jeffrey Dean and Sanjay Ghemawat, "MapReduce: Simplified Data Processing on Large Clusters" (2004).
- Sanjay Ghemawat, Howard Gobioff, and Shun-Tak Leung, "The Google File System" (2003).
- Fay Chang et al., "Bigtable: A Distributed Storage System for Structured Data" (2006).
- Giuseppe DeCandia et al., "Dynamo: Amazon's Highly Available Key-value Store" (2007).
- James C. Corbett et al., "Spanner: Google's Globally-Distributed Database" (2012).
- Keith A. Marzullo and others on leases/coordination concepts (plus production coordination docs such as ZooKeeper/etcd).
- Aleksey Dragojevic et al., "FaRM: Fast Remote Memory" (2014) for distributed-memory direction.

## Phase 7: GPU Concurrency

- CUDA Programming Guide (official NVIDIA).
- NVIDIA best practices guide for memory hierarchy, occupancy, and streams.
- Nsight Systems/Compute official profiling guides.

## Phase 8-9: Verification and Advanced Practice

- Papers/tutorials on model checking, stateless model checking, and deterministic replay.
- Jepsen analyses (for practical distributed failure reasoning).
- TLA+ introductory materials for protocol specifications.

## Recommended books (companion)

- *Rust Atomics and Locks* by Mara Bos.
- *Concurrency in Action* (for C++ perspective).
- *Designing Data-Intensive Applications* by Martin Kleppmann (distributed consistency perspective).

## How to read effectively

For each paper:

1. State assumptions (network model, fault model, hardware model).
2. Write claimed guarantees (safety/liveness/performance).
3. Reproduce one figure, algorithm, or experiment in code.
4. Note what changed in later work and why.
