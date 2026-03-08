# DIP Protocol Architecture

The Decision Integrity Protocol (DIP) provides verifiable automated decisions.

The architecture separates decision generation from verification.

---

## Protocol Components

DIP consists of four primary components.

### DIP CLI

Creates signed decision artifacts.

Responsibilities:

- canonicalization
- artifact ID generation
- signature creation

---

### DIP Registry

Append-only decision ledger.

Responsibilities:

- artifact storage
- Merkle tree maintenance
- proof generation

---

### DIP Verifier

Independent verification tool.

Responsibilities:

- artifact validation
- signature verification
- proof verification

---

### DIP Specification

Defines the protocol rules.

Responsibilities:

- artifact format
- canonicalization rules
- verification procedure

---

## System Architecture

Decision System
      │
      ▼
   Decision
      │
      ▼
Canonical JSON
      │
      ▼
SHA256 → artifact_id
      │
      ▼
Signature
      │
      ▼
Artifact
      │
      ▼
Registry Append
      │
      ▼
Merkle Root