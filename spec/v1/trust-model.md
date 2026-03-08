---
id: trust-model
title: Trust Model
---

# Trust Model

The Decision Integrity Protocol (DIP) minimizes trust requirements by
relying on deterministic artifacts and cryptographic verification.

DIP enables independent verification of decision evidence without
requiring trust in the system that originally produced the decision.

---

# Trust Minimization

Traditional systems require trust in infrastructure, databases,
or service providers.

DIP reduces these dependencies by making decision evidence
self-verifiable.

Verification depends only on:

- the artifact
- the signer public key
- a compliant verification implementation

This allows artifacts to be verified independently of the
systems that generated them.

---

# Trust Anchors

DIP verification relies on a limited set of trust anchors.

## Public Keys

Verifiers must trust the public keys used to sign artifacts.

Public key trust may be established through:

- organizational key management
- certificate infrastructures
- key transparency systems
- governance policies

---

## Verification Implementations

Verifiers must trust that verification software correctly
implements the DIP specification.

Independent implementations improve ecosystem trust by reducing
reliance on a single software implementation.

---

# Trust Boundaries

DIP intentionally avoids requiring trust in the following
entities:

- decision producers
- infrastructure providers
- ledger operators
- hosting platforms

Verification remains possible even if the original system
is unavailable or compromised.

---

# Verification Principle

The core DIP verification principle is:

artifact + verifier = truth

When ledger proofs are included:

artifact + proof + verifier = truth

This model allows independent systems to validate decision
evidence without relying on centralized authorities.

---

# Operational Trust

While cryptographic verification guarantees artifact integrity,
operational trust is still required for:

- protecting signing keys
- ensuring correct decision execution
- maintaining governance policies

These responsibilities belong to organizations deploying
the protocol rather than the protocol itself.