---
id: protocol
title: DIP Protocol
---

# Decision Integrity Protocol (DIP)

The Decision Integrity Protocol (DIP) defines a deterministic
and verifiable method for recording automated decisions.

DIP enables independent verification of decision artifacts
produced by automated systems.

The protocol guarantees that decision records can be verified
without trusting the system that produced them.

---

# Protocol Model

DIP defines a verifiable decision artifact composed of:

- a decision record
- a cryptographic signature
- an optional ledger inclusion proof

Verification is performed independently by a verifier.

The core verification principle of DIP is:

artifact + proof + verifier = truth

This means that a verifier can independently validate:

1. the integrity of the decision artifact
2. the authenticity of the signature
3. the inclusion of the artifact in the decision ledger

---

# Decision Artifact

A DIP artifact represents a signed automated decision.

The artifact structure is defined by the `artifact.schema.json`.

An artifact contains the following components:


artifact
├ artifact_version
├ artifact_id
├ decision
└ signature


### artifact_version

Defines the version of the artifact format.

### artifact_id

A deterministic identifier derived from the canonical artifact.

### decision

The decision payload describing the inputs and outputs of the decision.

### signature

A cryptographic signature over the canonical artifact.

---

# Decision Record

The decision record represents the semantic content of the decision.

The structure is defined in `decision.schema.json`.


decision
├ decision_id
├ timestamp
├ inputs
└ outputs


The decision payload is intentionally domain-neutral.

DIP does not interpret the meaning of decisions.
It only guarantees their integrity and provenance.

---

# Artifact Canonicalization

All artifacts MUST be canonicalized before hashing and signing.

Canonicalization ensures that identical artifacts produce
identical byte representations across implementations.

The canonicalization rules are defined in:

canonicalization.md

---

# Artifact ID Derivation

The `artifact_id` uniquely identifies a DIP artifact.

The identifier MUST be derived from the canonical representation
of the artifact.

## Derivation Procedure

1. Construct the artifact object.
2. Remove the `signature` field.
3. Canonicalize the artifact according to the canonicalization rules.
4. Compute the SHA256 hash of the canonical byte representation.
5. Encode the resulting hash as lowercase hexadecimal.

## Formula

artifact_id = SHA256(canonical_artifact_bytes)

## Determinism Requirement

All compliant DIP implementations MUST produce the same
`artifact_id` for the same artifact.

This guarantees that identical artifacts produce identical
identifiers across independent implementations.

---

# Artifact Signature

After canonicalization, the artifact MUST be signed.

The signature covers the canonical artifact bytes.

Signature parameters are defined in `artifact.schema.json`.

The current protocol version supports:

- Ed25519 signatures

The verifier MUST validate the signature before accepting
an artifact as valid.

---

# Decision Ledger

DIP optionally supports inclusion of artifacts in an append-only
decision ledger.

The ledger produces a Merkle tree over artifact hashes.

Artifacts included in the ledger can be proven using
Merkle inclusion proofs.

---

# Merkle Proof

The structure of a proof is defined in:

`proof.schema.json`


proof
├ artifact_hash
├ proof_path
└ root


Where:

- `artifact_hash` is the SHA256 hash of the canonical artifact
- `proof_path` is the Merkle path
- `root` is the ledger Merkle root

The verifier reconstructs the root using the proof path.

If the reconstructed root matches the provided root,
the artifact is proven to be part of the ledger.

---

# Verification Procedure

A verifier validates a DIP artifact in three steps.

## Step 1 — Canonicalization

The verifier canonicalizes the artifact according to
the canonicalization rules.

## Step 2 — Signature Verification

The verifier validates the cryptographic signature
over the canonical artifact bytes.

## Step 3 — Ledger Proof Verification (Optional)

If a proof is provided, the verifier validates the
Merkle proof linking the artifact to the ledger root.

---

# Verification Outcome

If all verification steps succeed, the verifier can
independently confirm that:

- the decision artifact was not modified
- the artifact was signed by the declared key
- the artifact may be proven to exist in the decision ledger

This guarantees deterministic and independent verification
across implementations.

---

# Protocol Scope

DIP does not define:

- how decisions are produced
- how decision logic operates
- how decision inputs are generated

DIP only defines how decisions are recorded,
signed, and independently verified.

---

# Protocol Invariants

The DIP protocol follows three core invariants.

### Deterministic Artifacts

Identical decisions produce identical canonical artifacts.

### Independent Verification

Any verifier implementation can validate artifacts.

### Survivability

Artifacts remain verifiable even if the original system
or registry becomes unavailable.

---

# Summary

The Decision Integrity Protocol provides a deterministic
and cryptographically verifiable record of automated decisions.

By combining canonical artifacts, cryptographic signatures,
and optional ledger proofs, DIP enables independent validation
of automated decision systems.