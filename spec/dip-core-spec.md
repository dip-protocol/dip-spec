# Decision Integrity Protocol (DIP)
## Core Specification

Version: 0.1.0  
Status: Draft

---

# 1. Introduction

The Decision Integrity Protocol (DIP) defines a standard method for generating **cryptographically verifiable artifacts representing automated decisions**.

DIP enables systems to produce portable artifacts that allow independent verification of decision integrity without requiring trust in the system that generated them.

This specification defines:

- artifact structure
- canonicalization rules
- hashing
- signing
- verification

---

# 2. Terminology

Artifact  
A structured record representing a specific decision.

Producer  
The system that generates the artifact.

Verifier  
A system that verifies artifact integrity.

Registry  
A storage system for DIP artifacts.

---

# 3. Artifact Structure

A DIP artifact is a JSON document with the following structure.

Example:

```json
{
  "protocol_version": "1.0.0",
  "decision_id": "dec-0001",
  "timestamp": "2026-03-04T12:00:00Z",
  "input_hash": "abc123...",
  "artifact_hash": "def456...",
  "signature": "789xyz...",
  "public_key": "ed25519:..."
}
````

Required fields:

| Field            | Description                |
| ---------------- | -------------------------- |
| protocol_version | DIP protocol version       |
| decision_id      | Unique decision identifier |
| timestamp        | Decision timestamp         |
| artifact_hash    | Hash of canonical artifact |
| signature        | Cryptographic signature    |
| public_key       | Public verification key    |

---

# 4. Canonicalization

Artifacts must be canonicalized before hashing.

Canonicalization ensures deterministic byte representation.

Requirements:

* JSON keys must be sorted
* No whitespace
* UTF-8 encoding

The canonicalization process MUST follow:

RFC 8785 (JSON Canonicalization Scheme)

---

# 5. Hashing

The artifact hash is computed as:

```
artifact_hash = SHA256(canonical_artifact)
```

The hashing algorithm used by DIP is:

```
SHA256
```

---

# 6. Signing

Artifacts are signed using the artifact hash.

Recommended algorithm:

```
Ed25519
```

Signature generation:

```
signature = Sign(private_key, artifact_hash)
```

---

# 7. Verification

Verification consists of the following steps:

1. Validate JSON schema
2. Canonicalize artifact
3. Recompute artifact hash
4. Verify signature using the public key

Verification succeeds if:

```
computed_hash == artifact_hash
AND
signature_valid == true
```

---

# 8. Conformance

Implementations must pass the conformance tests defined in:

```
conformance/test-vectors
```

These ensure consistent protocol behavior across implementations.

---

# 9. Security Considerations

Implementations must ensure:

* secure key storage
* tamper-resistant artifact storage
* proper timestamp validation

Compromise of private keys may invalidate artifact authenticity.

---

# 10. Versioning

The protocol follows semantic versioning:

```
MAJOR.MINOR.PATCH
```

Breaking changes require a MAJOR version increment.

---

# 11. Future Extensions

Future versions of the protocol may introduce:

* transparency logs
* artifact registries
* multi-signature support
* additional cryptographic algorithms

````

---

# Save the File

Then commit it.

```powershell
git add spec\dip-core-spec.md
git commit -m "Add DIP core specification"
````

---

# What You Have Now

Your repo now contains:

```
dip-spec
│
├ spec
│   └ dip-core-spec.md
├ schemas
├ docs
├ proposals
├ conformance
├ examples
├ sdk
```

This means you now officially have:

✔ protocol specification
✔ governance model
✔ documentation
✔ conformance tests

That is the **foundation of a real protocol standard**.

---

