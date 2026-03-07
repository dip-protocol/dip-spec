# Decision Integrity Protocol (DIP)

The Decision Integrity Protocol (DIP) is an open protocol for producing
cryptographically verifiable records of automated decisions.

DIP enables systems to generate deterministic decision artifacts that can be
independently verified without relying on the system that produced them.

## Core Principle

Verification must work independently of the system that produced the decision.


artifact + proof + verifier = truth


A verifier must be able to validate a decision artifact **offline** using only
the artifact, its proof, and a verification implementation.

## Protocol Primitives

The protocol defines four core primitives:

| Primitive | Description |
|----------|-------------|
| Artifact | Signed record describing the decision |
| Proof | Cryptographic inclusion proof from the decision ledger |
| Bundle | Portable container combining artifact and proof |
| Verification | Independent validation of artifact integrity |

## Repositories

| Repository | Purpose |
|-----------|--------|
| dip-spec | Protocol specification |
| dip-cli | Reference CLI implementation |
| dip-registry | Append-only decision ledger |
| dip-go-verifier | Independent verification library |

## Decision Pipeline

A typical DIP workflow:


decision.json
↓
dip sign
artifact.json
↓
dip proof
proof.json
↓
dip bundle
decision.dip
↓
dip verify decision.dip


## Protocol Specification

The full protocol specification is located in:


spec/v1/dip.md


## Properties

DIP is designed with the following guarantees:

* deterministic artifacts
* cryptographic signatures
* append-only decision ledger
* independent verification
* offline verification capability
* no single platform dependency

## License

Open protocol specification.