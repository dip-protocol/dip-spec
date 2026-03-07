\# DIP Trust Boundary





┌───────────────────────────┐

Decision System

(trusted)

└──────────────┬────────────┘

↓

┌───────────────────────────┐

Artifact Generation

(dip-cli)

└──────────────┬────────────┘



TRUST BOUNDARY



┌──────────────▼────────────┐

Decision Ledger

(dip-registry)

└──────────────┬────────────┘

↓

┌───────────────────────────┐

Verifier

(independent)

└───────────────────────────┘



Key Principle



Verification does not require trust in:



the decision system



the ledger



the artifact producer



Verification requires only:



artifact + proof + verifier

