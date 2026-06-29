# OxDeAI

**Deterministic Execution Authorization Protocol**

OxDeAI is an open-source protocol for enforcing authorization before side-effecting execution.

It is designed for AI agents, automation systems, workflow engines, orchestration platforms, and any software that can trigger external actions such as API calls, file changes, infrastructure operations, ticket creation, payments, or production mutations.

The core invariant is simple:

```text
No valid authorization → no execution path.
```

---

## Why OxDeAI exists

Modern AI and automation systems can decide, plan, and act across external systems.

They can call APIs, modify files, trigger workflows, create tickets, deploy infrastructure, or execute financial operations. Traditional access control answers questions such as:

```text
Who is this user?
Does this service account have access?
Is this API key valid?
```

OxDeAI focuses on a narrower execution-time question:

```text
Was this exact action authorized before it executed?
```

OxDeAI provides a deterministic authorization boundary between decision-making and execution.

---

## What OxDeAI does

OxDeAI defines signed protocol artifacts and an enforcement model that allow a system to verify authorization before executing an action.

Core protocol artifacts:

* `AuthorizationV1` - a signed authorization decision for one execution attempt
* `DelegationV1` - scoped delegation that cannot expand parent authority
* `SignedKRLV1` - signed key revocation list
* `canonicalization-v1` - deterministic serialization for signatures and hashes

Core enforcement model:

```text
proposal → policy decision → signed authorization → PEP verification → execution
```

The Policy Enforcement Point verifies the authorization before the side effect occurs.

If verification fails, execution does not proceed.

---

## What OxDeAI is not

OxDeAI is not:

* an AI agent framework
* a model guardrail
* a monitoring-only system
* an identity provider
* a replacement for OAuth, IAM, or API keys
* a trading strategy
* a workflow orchestrator

OxDeAI is a protocol-level execution authorization layer.

It composes with existing identity, policy, orchestration, and infrastructure systems.

---

## Current status

OxDeAI is early and under active development.

Current project state:

* open-source under Apache-2.0
* protocol specifications in progress
* TypeScript reference implementation
* Go and Python conformance harnesses
* conformance-driven verification model
* protocol whitepaper working draft
* independent review preparation underway

OxDeAI has not yet completed independent security review.

Do not rely on OxDeAI for production-critical enforcement without appropriate review, integration testing, and deployment hardening.

---

## Repository

Primary repository:

```text
https://github.com/OxDeAI/oxdeai
```

Main areas:

```text
docs/spec/                  protocol specifications
docs/whitepaper/            whitepaper working draft
docs/audits/                internal audit and residual tracking
packages/core/              protocol core
packages/guard/             enforcement guard
packages/conformance/       conformance tooling
go-harness/                 Go conformance harness
python-harness/             Python conformance harness
examples/                   integration examples
```

---

## Protocol principle

OxDeAI separates decision-making from execution.

The policy engine decides whether an action is authorized.

The signed authorization artifact carries that decision.

The Policy Enforcement Point verifies the artifact before the action reaches the execution boundary.

```text
Authorization decides.
PEP enforces.
Execution happens only after verification.
```

---

## Security posture

OxDeAI is designed around conservative security claims:

* deterministic verification
* signed authorization artifacts
* intent binding
* replay resistance
* key revocation
* fail-closed enforcement
* explicit residual trust assumptions
* conformance-driven claims

Known residuals include:

* signing key custody
* state provider trust boundary
* replay store durability
* verifier configuration integrity
* PEP placement
* clock synchronization
* external security review not yet completed

These residuals are documented rather than hidden.

---

## Whitepaper

The current working draft is available in the repository:

```text
docs/whitepaper/oxdeai-deterministic-execution-authorization.md
```

The whitepaper is not final and is not publication-ready.

It is being reconciled against the live protocol specifications, implementation, conformance vectors, and security review scope.

---

## Governance

OxDeAI is currently maintained as an open-source protocol project.

Current governance model:

* solo-maintained / lead-architect governed
* Apache-2.0 licensed
* conservative documentation discipline
* protocol decisions pinned in specs, issues, audits, or conformance vectors
* no foundation governance yet
* no formal standards-body adoption yet

The project prioritizes precision over maturity signaling.

---

## Contact

General contact:

```text
contact@oxdeai.dev
```

Security contact:

```text
security@oxdeai.dev
```

Please do not report security issues through public GitHub issues.

---

## Links

Website:

```text
https://oxdeai.dev
```

GitHub:

```text
https://github.com/OxDeAI
```

X / Twitter:

```text
https://x.com/oxdeai
```

Reddit:

```text
https://www.reddit.com/r/OxDeAI
```

---

## One-line summary

OxDeAI is a deterministic execution authorization protocol for systems that must verify authority before side effects occur.
