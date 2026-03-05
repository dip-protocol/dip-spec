# Decision Integrity Protocol (DIP)

The Decision Integrity Protocol (DIP) is an open protocol for generating
deterministic, cryptographically verifiable decision records.

DIP enables automated systems to produce decision artifacts that can be
independently verified for integrity, provenance, and reproducibility.

## Core Concepts

- **Decision Record** — Structured representation of a decision.
- **Signature** — Cryptographic proof of integrity.
- **Verification** — Independent validation of the artifact.

## Repositories

| Repository | Purpose |
|-----------|--------|
| dip-spec | Protocol specification |
| dip-cli | Reference CLI implementation |
| dip-registry | Artifact registry |
| dip-go-verifier | Verification library |

## Workflow

1. Produce a decision record
2. Sign the record
3. Publish or store the artifact
4. Verify integrity independently

## Specification

The protocol specification lives in:
