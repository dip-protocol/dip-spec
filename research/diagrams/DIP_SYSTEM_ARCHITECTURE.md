\# DIP System Architecture





┌───────────────────────────┐

Decision Engine

(application system)

└──────────────┬────────────┘

↓

┌───────────────────────────┐

Documentation Engine

(dip-cli)

└──────────────┬────────────┘

↓

┌───────────────────────────┐

Decision Artifact

artifact.json

└──────────────┬────────────┘

↓

┌───────────────────────────┐

Decision Ledger

(dip-registry)

└──────────────┬────────────┘

↓

┌───────────────────────────┐

Merkle Proof

proof.json

└──────────────┬────────────┘

↓

┌───────────────────────────┐

Verifier

(dip-go-verifier)

└───────────────────────────┘



Architecture Principle



Decision execution and verification are independent.



Verification requires only:



artifact + proof + verifier

