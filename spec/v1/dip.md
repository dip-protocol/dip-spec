\# Decision Integrity Protocol (DIP) v1



\## Overview



The Decision Integrity Protocol defines a format for producing

cryptographically verifiable records of automated decisions.



A DIP artifact records a decision and provides the information necessary

for independent verification.



\## Artifact Format



Artifacts are JSON documents.



Example artifact:



```json

{

&nbsp; "artifact\_version": "1.0",

&nbsp; "artifact\_id": "sha256-hash",

&nbsp; "decision": {},

&nbsp; "signature": {

&nbsp;   "algorithm": "ed25519",

&nbsp;   "public\_key": "...",

&nbsp;   "value": "..."

&nbsp; }

}

Fields

Field	Description

artifact\_version	Protocol version

artifact\_id	SHA256 hash of canonical artifact

decision	Structured decision record

signature	Cryptographic signature

Canonicalization



Artifacts must be canonicalized before signing.



Canonicalization rules:



JSON objects must use deterministic ordering



No whitespace changes allowed



UTF-8 encoding



Signature



Artifacts are signed using:



Ed25519



The signature is computed over the canonicalized artifact content.



Proof Format



Proofs demonstrate inclusion in the decision ledger.



Example:



{

&nbsp; "artifact\_hash": "...",

&nbsp; "proof\_path": \[],

&nbsp; "root": "..."

}



Fields:



Field	Description

artifact\_hash	Hash of artifact

proof\_path	Merkle inclusion path

root	Ledger Merkle root

Bundle Format



DIP bundles use the .dip extension.



A bundle is a zip archive containing:



artifact.json

proof.json



Bundles allow portable verification.



Verification



Verification performs the following checks:



artifact canonicalization



signature validation



artifact hash consistency



proof verification against ledger root



If all checks succeed, the artifact is considered valid.



Protocol Invariant



The protocol guarantees:



artifact + proof + verifier = truth



Verification must be possible offline.

