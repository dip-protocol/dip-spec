---
id: security-model
title: Security Model
---

# Security Model

The Decision Integrity Protocol (DIP) provides cryptographic
integrity guarantees for decision artifacts.

DIP ensures that once a decision artifact is produced and signed,
any modification to the artifact can be detected during verification.

---

## Security Objectives

DIP provides the following guarantees:

- Artifact integrity
- Decision authenticity
- Tamper detection
- Independent verification

These guarantees allow decision artifacts to function as verifiable
evidence of automated or human decisions.

---

## Threat Model

The protocol considers the following threats.

### Artifact Tampering

An attacker modifies a decision artifact after it has been created.

Mitigation:

Artifact identifiers and signatures are derived from canonical
artifact bytes. Any modification changes the artifact hash and
invalidates the signature.

---

### Signature Forgery

An attacker attempts to produce a valid signature without access
to the private signing key.

Mitigation:

DIP uses Ed25519 signatures which provide strong cryptographic
security guarantees.

---

### Ledger Manipulation

An attacker attempts to rewrite or remove entries from the
decision ledger.

Mitigation:

Decision ledgers are append-only and may use Merkle trees
to provide verifiable inclusion proofs.

---

### Replay Attacks

An attacker reuses an artifact in a different context.

Mitigation:

Artifacts include timestamps and decision identifiers
that allow contextual validation.

---

## Trust Assumptions

DIP requires trust in the following components:

- the signer’s private key security
- correct implementation of the verification algorithm
- the correctness of the decision payload

DIP does not attempt to validate the correctness of the
decision itself, only the integrity of the decision artifact.

---

## Verification Principle

The core DIP verification rule is:


artifact + verifier = truth


When ledger proofs are used:


artifact + proof + verifier = truth


This property enables long-term independent verification
of decision artifacts.