---
id: architecture
title: Architecture
---

# DIP Architecture

The Decision Integrity Protocol (DIP) defines a deterministic pipeline
for producing verifiable decision artifacts.

The architecture separates decision execution from verification,
allowing independent systems to validate decision evidence.

---

## Core Components

### Decision Producer

A system that executes a decision process and produces a structured
decision record.

Examples:

- automated decision engines
- governance workflows
- policy evaluation systems

---

### Artifact Construction

The decision record is embedded into a DIP artifact that contains:

- artifact_version
- artifact_id
- decision
- signature

This artifact becomes the verifiable unit of decision evidence.

---

### Canonicalization Layer

Before signing, artifacts are serialized using deterministic JSON
canonicalization.

Canonicalization ensures that all implementations produce identical
byte representations of the artifact.

This property is required for cross-implementation verification.

---

### Cryptographic Signature

Artifacts are signed using Ed25519 signatures.

The signature provides:

- authenticity
- tamper detection
- signer attribution

Any modification to the artifact invalidates the signature.

---

### Decision Ledger (Optional)

Artifacts or artifact hashes may be recorded in an append-only ledger.

Ledgers provide:

- durability
- transparency
- inclusion proofs

Examples include transparency logs or registry systems.

---

### Verification Engine

Independent verifiers validate artifacts by:

1. canonicalizing the artifact
2. computing the artifact hash
3. verifying the signature
4. optionally validating ledger proofs

Verification does not require access to the system that produced the
artifact.

---

## System Flow

The DIP execution pipeline is:

Execution → Artifact → Canonicalization → Signature → Ledger → Independent Verification

---

## Architectural Principle

DIP separates decision production from verification.

This separation enables:

- independent auditing
- infrastructure portability
- long-term verifiability