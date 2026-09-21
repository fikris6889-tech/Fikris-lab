# Fikris Lab

A collection of systems and algorithms implementations — from classical cryptography to distributed consensus and cloud orchestration.

Each project is a deep dive into a specific problem domain, with complete implementations, comprehensive tests, and detailed documentation.

---

## Projects

### 🔐 [CipherLab](https://github.com/fikris6889-tech/cipherlab) — Classical Cryptography
**Beginner-friendly exploration of substitution ciphers**

Learn the fundamentals of cryptography through hands-on implementation:
- **Caesar Cipher** — fixed-shift substitution
- **Vigenère Cipher** — repeating-key substitution  
- **Automatic Caesar Cracker** — frequency analysis with chi-squared statistics

**26 tests** | Pure Python stdlib | Educational focus

```bash
git clone https://github.com/fikris6889-tech/cipherlab.git
cd cipherlab
python3 -m unittest discover -s tests -v
```

---

### ⏱️ [RateLimitKit](https://github.com/fikris6889-tech/ratelimitkit) — Rate Limiting Algorithms
**Intermediate study of three classic rate-limiting patterns**

Understand the trade-offs between memory, precision, and burst tolerance:
- **Fixed Window** — O(1) memory, approximate precision
- **Sliding Window Log** — exact precision, O(limit) memory  
- **Token Bucket** — exact rate, burst-tolerant

**62 tests** | Demo HTTP gateway | Concurrent load tester | Pure Python stdlib

Includes a comparison table to help you choose the right algorithm for your use case.

```bash
git clone https://github.com/fikris6889-tech/ratelimitkit.git
cd ratelimitkit
python3 -m unittest discover -s tests -v
python3 -m ratelimitkit.server --port 8080 --limit 3 --window 5
```

---

### 🏗️ [MiniRaft](https://github.com/fikris6889-tech/miniraft) — Distributed Consensus
**Expert-level implementation of the Raft consensus algorithm**

A complete, production-inspired build of Raft consensus across 4 days:
- **Day 1:** Data structures & transport layer (log, key-value store, HTTP RPC)
- **Day 2:** Leader election with randomized timeouts
- **Day 3:** Log replication with consistency checks and commit tracking
- **Day 4:** ReadIndex optimization for efficient linearizable reads

**60 tests** | 3-node cluster | Real distributed failure scenarios | Zero dependencies

Reference: Ongaro & Ousterhout, "In Search of an Understandable Consensus Algorithm" (2014)

```bash
git clone https://github.com/fikris6889-tech/miniraft.git
cd miniraft
python3 -m unittest discover -s tests -v
python3 cluster_run.py --nodes 3
```

---

### ☁️ [SagaFlow](https://github.com/fikris6889-tech/sagaflow) — Distributed Transactions on AWS
**Hard-tier, production-ready serverless saga pattern**

Order processing pipeline demonstrating the Saga pattern for distributed transactions:
- **AWS Step Functions** orchestrates the workflow
- **7 Lambda functions** handle: order intake, inventory reservation, payment, shipment
- **DynamoDB** stores state with optimistic locking and idempotency keys
- **Automatic compensating transactions** on any step failure

**43 tests**: unit tests + real concurrency (50 threads) + E2E state machine validation

Covers the failure modes that make distributed systems hard:
- At-least-once execution (requires idempotency)
- Concurrent updates (requires optimistic locking)
- Partial failure (requires compensating transactions)

Deploys to **AWS Always Free tier** (~$0/month for reasonable volume).

```bash
git clone https://github.com/fikris6889-tech/sagaflow.git
cd sagaflow
python3 -m unittest discover -s tests -v
sam deploy --guided  # Deploy to AWS
```

---

## Learning Path

Start here if you're building system design knowledge:

1. **CipherLab** (1-2 hours) — Get comfortable with crypto fundamentals and test-driven thinking
2. **RateLimitKit** (2-3 hours) — Understand trade-offs between algorithms (memory vs. precision)
3. **MiniRaft** (4-6 hours) — Deep dive into distributed consensus (the hardest problem in systems)
4. **SagaFlow** (3-4 hours) — Apply learnings to real AWS infrastructure; see distributed systems "in the wild"

---

## Common Patterns Across Projects

### Testing
Every project includes comprehensive tests you can run locally:
```bash
python3 -m unittest discover -s tests -v
```

Tests cover:
- Happy paths and edge cases
- Real concurrency (actual threads, not mocks)
- Integration with external systems (HTTP servers, state machines)
- Failure modes and recovery

### Zero Dependencies
All projects use Python's standard library only — no `pip install` needed. This keeps the focus on algorithms and architecture, not framework mechanics.

### Documentation
Each project includes:
- **README** — overview, setup, usage examples
- **Code comments** — only where the "why" is non-obvious
- **Tests as documentation** — reading tests shows exactly how to use the code
- **Architecture diagrams** (where relevant)

---

## Tech Stack

- **Language:** Python 3.8+
- **Testing:** unittest (stdlib)
- **Cloud:** AWS (Lambda, Step Functions, DynamoDB, SAM CLI)
- **External dependencies:** Zero (tests) to one (boto3 in Lambda runtime)

---

## Quick Links

| Project | Repo | Tests | Difficulty |
|---------|------|-------|-----------|
| CipherLab | [repo](https://github.com/fikris6889-tech/cipherlab) | 26 | Beginner |
| RateLimitKit | [repo](https://github.com/fikris6889-tech/ratelimitkit) | 62 | Intermediate |
| MiniRaft | [repo](https://github.com/fikris6889-tech/miniraft) | 60 | Expert |
| SagaFlow | [repo](https://github.com/fikris6889-tech/sagaflow) | 43 | Hard/Cloud |

**Total: 191 tests proving correctness across 4 projects**

---

## Running Tests Locally

Each project can be cloned and tested independently with zero setup:

```bash
# Pick any project
git clone https://github.com/fikris6889-tech/miniraft.git
cd miniraft

# Run all tests
python3 -m unittest discover -s tests -v

# All tests pass with zero external dependencies
```

---

## Design Philosophy

These projects emphasize:

- **Understanding over abstraction** — See how algorithms actually work, not just library APIs
- **Concrete over theoretical** — Real failure scenarios, real concurrency, real AWS
- **Honest documentation** — Limitations are called out, trade-offs are explicit
- **Test-driven validation** — Tests prove the code works, not just that it compiles

---

## License

All projects are open source and available for learning, modification, and reuse.

---

## Get Started

Pick a project, clone it, run the tests. Everything you need is in the README.

```bash
# Start with CipherLab if you're new to this style
git clone https://github.com/fikris6889-tech/cipherlab.git
cd cipherlab
python3 -m unittest discover -s tests -v
```

Or jump straight to distributed systems:

```bash
# Go deep with MiniRaft
git clone https://github.com/fikris6889-tech/miniraft.git
cd miniraft
python3 -m unittest discover -s tests -v
python3 cluster_run.py --nodes 3
```

---

Built with attention to detail. Each line of code and test has a purpose.
