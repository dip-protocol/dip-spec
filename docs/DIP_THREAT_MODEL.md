\# DIP Threat Model



This document describes the threat model for the

Decision Integrity Protocol (DIP).



The goal of the protocol is to provide verifiable

evidence of automated decisions.



---



\# Security Goals



DIP provides the following guarantees.



\### Artifact Integrity



Decision artifacts cannot be modified without detection.



\### Cryptographic Provenance



Artifacts are signed using Ed25519 signatures.



\### Tamper Detection



Changes to artifacts or proofs invalidate verification.



\### Ledger Integrity



The decision ledger provides append-only evidence

using Merkle tree construction.



\### Offline Verification



Verification requires only:



artifact + proof + verifier



---



\# Threat Actors



The protocol considers the following adversaries.



\### Malicious Artifact Producer



A producer may attempt to generate incorrect artifacts.



Mitigation:



\- signature verification

\- canonical artifact hashing



---



\### Malicious Ledger Operator



The ledger may attempt to hide or reorder artifacts.



Mitigation:



\- Merkle root verification

\- independent artifact storage



---



\### Network Attacker



An attacker may intercept or modify artifacts.



Mitigation:



\- cryptographic signatures

\- artifact hash verification



---



\### Artifact Tampering



Artifacts may be modified after creation.



Mitigation:



\- artifact\_id verification

\- signature validation



---



\# Non-Goals



The protocol intentionally does not provide:



\### Decision Correctness



DIP verifies that a decision occurred,

not whether the decision was correct.



\### Confidentiality



DIP artifacts are not encrypted.



Sensitive inputs should not be included in artifacts.



\### Identity Management



The protocol does not define identity systems.



External identity infrastructure may be used.



---



\# Security Assumptions



The protocol assumes:



\- SHA256 remains secure

\- Ed25519 signatures remain secure

\- canonicalization is deterministic



---



\# Security Summary



DIP provides a minimal cryptographic protocol for

verifiable automated decisions.



The protocol prioritizes:



determinism  

verification independence  

long-term survivability

