
```markdown
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

```

spec/v1/

```

## License

Open specification for verifiable decision artifacts.
```

---

# 2️⃣ Create a Versioned Spec Folder

Inside **dip-spec**, create this structure:

```
dip-spec
│
├ README.md
│
├ spec
│   └ v1
│       └ dip.md
│
├ schemas
│
├ examples
│
└ governance
```

Example:

```
spec/v1/dip.md
```

This file contains the **actual protocol specification**.

Versioning like this is used by:

* OCI
* OpenTelemetry
* Kubernetes

---

# 3️⃣ Create the First Spec File

File:

```
spec/v1/dip.md
```

Example start:

````markdown
# Decision Integrity Protocol (DIP) v1

## Overview

The Decision Integrity Protocol defines a standard format for
cryptographically verifiable decision artifacts.

A DIP artifact contains:

- decision metadata
- decision inputs
- decision outputs
- cryptographic signature

## Artifact Structure

A DIP artifact is a JSON document.

Example:

```json
{
  "version": "1.0",
  "decision_id": "12345",
  "timestamp": "2026-03-06T12:00:00Z",
  "inputs": {},
  "outputs": {},
  "signature": {}
}
````

```

---

# Result

Your `dip-spec` repo will now look like:

```

dip-spec
│
├ README.md
│
├ spec
│   └ v1
│       └ dip.md
│
├ schemas
├ examples
└ governance

```


```
## DIP Architecture

Decision Integrity Protocol (DIP) separates decision execution from evidence storage.

decision
   ↓
Documentation Engine (dip-cli)
   ↓
Decision Artifact (artifact.json)
   ↓
Verification (dip-go-verifier)
   ↓
Decision Ledger (dip-registry)

Properties:

artifact + verifier = truth
verification works offline
ledger is append-only and tamper-evident
no single platform can kill DIP