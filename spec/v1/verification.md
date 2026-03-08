---
id: verification
title: Verification
---

# Verification

DIP artifacts are designed to be independently verifiable.

Verification confirms that a decision artifact is authentic,
has not been modified, and was produced by a valid signer.

Verification can be performed without access to the system
that originally generated the decision.

---

# Verification Inputs

A verifier requires:

- the decision artifact
- the signer public key
- a verification implementation

If ledger proofs are used, the verifier may also require:

- ledger proof
- ledger root or checkpoint

---

# Deterministic Verification Algorithm

Given a DIP artifact **A**, verification MUST perform the following
steps in order:

1. Parse the artifact.
2. Extract the `signature` object.
3. Remove the `signature` field from the artifact.
4. Canonicalize the artifact using the DIP canonicalization rules.
5. Compute

artifact_id = SHA256(canonical_artifact_bytes)

6. Verify that the computed `artifact_id` matches the
   `artifact_id` field in the artifact.
7. Verify the Ed25519 signature using the signer public key.

If any step fails, the artifact **MUST be rejected**.

---

# Ledger Validation (Optional)

If the artifact is recorded in a decision ledger:

1. Verify the ledger proof.
2. Confirm the artifact hash exists in the ledger.
3. Validate the ledger root or checkpoint.

This step provides evidence that the artifact was recorded
in an append-only registry.

---

# Verification Principle

The core DIP verification principle is:

artifact + verifier = truth

When ledger proofs are included:

artifact + proof + verifier = truth

This enables independent verification of decision evidence
without reliance on the original decision-producing system.

---

---

## Artifact Verification Procedure

Verification confirms that a DIP artifact is authentic,
has not been modified, and was produced by the holder
of the signing key.

Verification procedure:

1. Parse the artifact JSON.
2. Extract the `signature` object.
3. Remove the `signature` field from the artifact.
4. Canonicalize the remaining artifact using the DIP canonicalization rules.
5. Recompute the artifact identifier:


artifact_id = SHA256(canonical_artifact_without_signature)


6. Confirm that the recomputed `artifact_id` matches the
`artifact_id` field in the artifact.
7. Verify the Ed25519 signature using the provided public key.

If any verification step fails, the artifact MUST be rejected.

Successful verification guarantees that:

- the artifact content has not been modified
- the artifact identifier matches the artifact content
- the artifact was signed by the holder of the corresponding private key

---