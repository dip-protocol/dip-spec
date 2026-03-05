# DIP Security Model

DIP provides cryptographic guarantees for decision artifacts.

The protocol ensures:

Artifact Integrity  
Artifacts are hashed deterministically.

Authenticity  
Artifacts are signed using Ed25519.

Transparency  
Artifacts are recorded in an append-only evidence registry.

Auditability  
Merkle inclusion proofs allow independent verification.

## Threat Model

DIP protects against:

Artifact tampering  
Signature forgery  
Registry mutation  
Evidence deletion

DIP does not attempt to guarantee correctness of decisions.
It guarantees only the integrity and traceability of decision artifacts.