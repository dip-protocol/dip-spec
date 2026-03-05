# DIP Trust Boundary

The Deterministic Integrity Protocol separates three trust domains.

Decision Systems  
AI models, automation engines, or workflows producing decisions.

DIP Infrastructure  
Artifact creation, hashing, signing, verification, and registry.

External Auditors  
Entities verifying artifacts independently.

The protocol guarantees that any decision artifact crossing the DIP boundary becomes cryptographically verifiable.

Decision System
      │
      │  (untrusted)
      ▼
Artifact Producer
      │
      │  (DIP begins here)
      ▼
Canonicalization
      ▼
Hash
      ▼
Signature
      ▼
Verification