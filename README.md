---

# Decision Integrity Protocol (DIP) Specification

The **Decision Integrity Protocol (DIP)** defines a minimal standard for producing **verifiable artifacts representing automated decisions**.

A DIP artifact records the inputs and outputs of an automated decision together with cryptographic evidence that the artifact has not been altered.

Artifacts created using this protocol can be **verified independently and offline**, without requiring access to the original system that produced them.

---

# Protocol Goals

The protocol is designed to ensure that automated decision records are:

* **Independently verifiable**
* **Deterministically auditable**
* **Preserved for long-term verification**
* **Implementable across multiple programming languages**

DIP intentionally minimizes protocol surface area in order to maximize interoperability and long-term stability.

---

# Core Protocol Concepts

## Decision Artifact

The primary protocol object is the **decision artifact**.

A decision artifact is a structured record containing the information necessary to verify an automated decision event.

At minimum, a DIP artifact contains:

```
artifact_version
artifact_id
decision
signature
```

The artifact identifier is derived from the canonical representation of the artifact.

```
artifact_id = SHA256(canonical_artifact)
```

This identifier uniquely represents the artifact contents.

---

# Canonicalization

Artifacts must be serialized using **deterministic canonical JSON**.

Canonicalization rules include:

* Object keys must be sorted lexicographically
* No extraneous whitespace is permitted
* Encoding must use UTF-8

Canonical serialization ensures that artifacts produce **stable hashes and signatures across implementations**.

---

# Cryptographic Signing

Artifacts are signed using the **Ed25519 digital signature algorithm**.

Signing procedure:

```
artifact (without signature)
        ↓
canonicalization
        ↓
SHA256 hash
        ↓
Ed25519 signature
```

The resulting signature binds the artifact contents to the signing key.

---

# Verification

Any DIP-compatible verifier can validate a decision artifact.

Verification process:

```
artifact
   ↓
remove signature
   ↓
canonicalize artifact
   ↓
recompute artifact_id
   ↓
verify Ed25519 signature
```

If all checks succeed, the artifact is considered **valid and unmodified**.

Verification does not require network access or access to the originating system.

---

# Protocol Architecture

The reference ecosystem contains several independent components:

```
dip-spec
    Protocol specification

dip-cli
    Artifact creation and signing tools

dip-registry
    Append-only transparency log

dip-go-verifier
    Go implementation of artifact verification

dip-js-verifier
    JavaScript implementation of artifact verification
```

These implementations demonstrate how the protocol can be adopted across multiple environments.

---

# Verification Example

A DIP artifact can be verified using any compatible verifier.

Example command:

```
verify artifact.json
```

If verification succeeds, the verifier prints:

```
Artifact verified successfully
```

This demonstrates the core DIP invariant:

```
artifact + proof + verifier = truth
```

---

# License

This specification is released under the **Apache License 2.0**.

---
