# Distributed Key-Value Store (Mini DynamoDB) Project Plan

**Goal**: Build a fault-tolerant, distributed key-value store in Rust, inspired by DynamoDB.  
**Why**: Demonstrate mastery of Rust, distributed systems, and async programming.  
**Target Timeline**: 12 weeks (3 months) with daily progress.

---

## Phase 1: Foundation (Week 1-2)

**Objective**: Single-node key-value store with HTTP API.

### Milestone 1.1: Basic Key-Value Store

- **Tasks**:
  1. Create a Rust project with `cargo new dynamo-rs`.
  2. Implement an in-memory key-value store using `HashMap`.
  3. Add basic CRUD operations (GET, PUT, DELETE).
  4. Write unit tests for all operations (use `cargo test`).
  5. Integrate logging with `tracing` or `env_logger`.

### Milestone 1.2: HTTP API

- **Tasks**:
  1. Use `axum` or `warp` to expose the store via HTTP endpoints.
  2. Add endpoints:
     - `GET /key/{id}`
     - `PUT /key/{id}` (with JSON body)
     - `DELETE /key/{id}`
  3. Test API with `curl` or Postman.
  4. Add serialization/deserialization with `serde_json`.

### Tools/Libraries:

- `axum`/`warp` (HTTP server)
- `serde` (serialization)
- `tracing` (logging)
- `tokio` (async runtime)

---

## Phase 2: Persistence & Replication (Week 3-6)

**Objective**: Add disk persistence and multi-node replication.

### Milestone 2.1: Disk Persistence

- **Tasks**:
  1. Replace in-memory `HashMap` with a disk-backed store (e.g., `sled` or custom log-structured storage).
  2. Implement Write-Ahead Logging (WAL) for durability.
  3. Benchmark performance with `criterion`.

### Milestone 2.2: Leader-Follower Replication

- **Tasks**:
  1. Design a replication protocol (e.g., leader writes → followers replicate).
  2. Use `gRPC` (`tonic` crate) or custom TCP protocol for node communication.
  3. Handle replication conflicts (last-write-wins or vector clocks).
  4. Test with 2-3 nodes locally using Docker.

### Tools/Libraries:

- `sled` (embedded database)
- `tonic` (gRPC)
- `bincode` (binary serialization)
- `docker` (local node testing)

---

## Phase 3: Distributed Systems (Week 7-10)

**Objective**: Cluster coordination, partitioning, and fault tolerance.

### Milestone 3.1: Sharding (Partitioning)

- **Tasks**:
  1. Implement consistent hashing to distribute keys across nodes.
  2. Add a `ShardManager` to track partition ownership.
  3. Handle node joins/leaves (rebalance shards).

### Milestone 3.2: Consensus with Raft

- **Tasks**:
  1. Integrate the `raft-rs` crate for leader election and log replication.
  2. Ensure linearizable reads/writes via Raft consensus.
  3. Simulate network partitions and test recovery.

### Milestone 3.3: Failure Handling

- **Tasks**:
  1. Add retries for transient failures.
  2. Implement health checks and timeouts.
  3. Write integration tests with fault injection (e.g., kill nodes randomly).

### Tools/Libraries:

- `raft-rs` (Raft implementation)
- `hashring` (consistent hashing)
- `rand` (failure simulation)

---

## Phase 4: Polish & Extras (Week 11-12)

**Objective**: Optimize, document, and prepare for open-source.

### Milestone 4.1: Performance Tuning

- **Tasks**:
  1. Optimize read/write paths with async I/O.
  2. Add caching with `moka` or `lru`.
  3. Profile with `flamegraph` and `perf`.

### Milestone 4.2: Documentation & Open-Source Prep

- **Tasks**:
  1. Write a `README.md` with setup/usage instructions.
  2. Generate API docs with `cargo doc`.
  3. Set up CI/CD with GitHub Actions (test + lint).
  4. Add a demo (e.g., load test with `wrk`).

### Tools/Libraries:

- `moka` (caching)
- `flamegraph` (profiling)
- GitHub Actions (CI/CD)

---

## Stretch Goals (If Time Permits)

- TLS support for secure communication.
- Prometheus metrics integration.
- Kubernetes deployment example.

---

## Learning Outcomes

By the end, you’ll have:

- Mastered Rust’s concurrency model (`async/await`, `Arc<Mutex>`).
- Built a complex distributed system from scratch.
- Gained experience with networking, consensus, and performance tuning.
- A project that screams “hire me” for infrastructure/backend roles.

---

**Next Step**: Start with Phase 1! Let me know if you want daily/weekly task breakdowns. 🚀
# database_rust
