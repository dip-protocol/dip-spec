\# DIP Protocol Flow



This document explains the lifecycle of a Decision Integrity Protocol (DIP) artifact.



The protocol ensures that automated decisions can be independently verified.



---



\## Overview



The DIP lifecycle consists of five stages:



Decision → Artifact → Registry → Proof → Verification



---



\## 1. Decision



A decision system produces a structured decision record.



Example fields:



\- decision\_id

\- timestamp

\- inputs

\- outputs



The decision record represents the execution of an automated decision.



---



\## 2. Artifact Creation



The decision record is converted into a DIP artifact.



Steps:



1\. Serialize the decision using canonical JSON.

2\. Compute SHA256 hash of the canonical decision.

3\. The resulting hash becomes the artifact\_id.

4\. Sign the artifact using Ed25519.



Result:



artifact.json



---



\## 3. Registry Append



The artifact is submitted to the DIP registry.



The registry:



\- stores the artifact

\- appends artifact\_id to the ledger

\- updates the Merkle tree

\- computes a new Merkle root



The registry is append-only.



---



\## 4. Proof Generation



A Merkle inclusion proof can be generated for an artifact.



The proof contains:



\- artifact\_hash

\- proof\_path

\- Merkle root



This proves the artifact exists in the registry.



---



\## 5. Verification



Verification is performed independently using a DIP verifier.



Verification checks:



1\. artifact\_id matches SHA256(canonical(decision))

2\. Ed25519 signature is valid

3\. Merkle proof recomputes the correct root



If all checks pass:



artifact + proof + verifier = truth

