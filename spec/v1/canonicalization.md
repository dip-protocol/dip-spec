---
id: canonicalization
title: Canonicalization
---

# Canonicalization

Canonicalization ensures that DIP artifacts produce the same
byte representation across all implementations.

Deterministic serialization is required so that identical
artifacts produce identical hashes and signatures.

All DIP artifacts MUST be canonicalized prior to hashing
and signing.

---

## Canonical JSON Rules

DIP canonicalization follows these rules:

1. JSON MUST be encoded using UTF-8.
2. Object keys MUST be sorted lexicographically using bytewise UTF-8 ordering.
3. No insignificant whitespace is permitted.
4. Arrays MUST preserve element order.
5. Strings MUST follow standard JSON escaping rules.
6. Numbers MUST use standard JSON numeric representation.

---

## Canonicalization Process

The canonicalization procedure is:

1. Construct the artifact object.
2. Remove the `signature` field.
3. Serialize the artifact using deterministic JSON.
4. Produce canonical byte representation.

These canonical bytes are used for:

- artifact_id derivation
- artifact signature generation
- artifact verification

---

## Deterministic Requirement

All DIP implementations MUST produce identical canonical
byte representations for the same artifact.

This requirement ensures interoperability across independent
implementations.

---

## Verification Principle

Because canonicalization is deterministic:

artifact + proof + verifier = truth

A verifier can independently:

1. Canonicalize the artifact.
2. Verify the artifact signature.
3. Verify the Merkle proof against the ledger root.

This enables any verifier implementation to independently
validate decision artifacts and their inclusion in the
decision ledger.