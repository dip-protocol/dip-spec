# DIP Protocol Overview

The Decision Integrity Protocol (DIP) defines a standard for producing
cryptographically verifiable records of automated decisions.

The protocol separates **decision execution** from **decision verification**.

## Architecture


decision
↓
Documentation Engine (dip-cli)
↓
Decision Artifact (artifact.json)
↓
Proof Generation
↓
Proof (proof.json)
↓
Portable Bundle (decision.dip)
↓
Independent Verification


## Components

### Artifact

The artifact is the signed representation of the decision.

It contains:

* decision content
* artifact identifier
* cryptographic signature

### Proof

A proof demonstrates that the artifact was included in the decision ledger.

Proofs use a Merkle inclusion proof derived from the registry log.

### Bundle

A DIP bundle is a portable archive containing:


artifact.json
proof.json


The bundle format uses the `.dip` extension.

### Verification

Verification validates:

1. artifact signature
2. artifact integrity
3. proof correctness

Verification must work without requiring access to the original system.

## Protocol Guarantee

If verification succeeds:


artifact + proof + verifier = truth


The decision record is considered cryptographically valid.