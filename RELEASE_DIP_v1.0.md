# Decision Integrity Protocol (DIP) v1.0

Release Date: 2026

Status: Stable

---

## Overview

The Decision Integrity Protocol (DIP) defines a minimal protocol for
verifiable automated decisions.

DIP enables independent verification of decision outputs produced by
automated systems.

---

## Protocol Invariant

artifact + proof + verifier = truth

---

## Core Components

### Artifact

A signed record describing an automated decision.

### Registry

Append-only ledger storing artifact identifiers.

### Proof

Merkle inclusion proof linking artifact to registry root.

### Verifier

Independent implementation validating artifacts and proofs.

---

## Protocol Flow

decision.json
↓
artifact.json
↓
registry append
↓
proof generation
↓
independent verification

---

## Reference Implementations

dip-cli

Creates signed artifacts.

dip-registry

Append-only decision ledger.

dip-go-verifier

Independent artifact verifier.

dip CLI

Unified protocol interface.

---

## Conformance

Test vectors are available in:

conformance/test-vectors/v1

Implementations must pass these tests to be considered DIP compatible.

---

## Version

Protocol Version: 1.0