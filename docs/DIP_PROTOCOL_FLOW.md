\# DIP Protocol Flow



The Decision Integrity Protocol produces verifiable decision records

through a deterministic pipeline.





decision.json

↓

dip sign

↓

artifact.json

↓

dip proof

↓

proof.json

↓

dip bundle

↓

decision.dip

↓

dip verify

↓

verification result





\## Components



| Component | Role |

|----------|------|

Decision | Structured input describing a decision |

Artifact | Signed representation of the decision |

Proof | Merkle inclusion proof |

Bundle | Portable verification package |



\## Protocol Invariant





artifact + proof + verifier = truth



Save.



Step 2 — Create Architecture Diagram



Create:



notepad D:\\Conf\\dip-protocol\\dip-spec\\docs\\DIP\_SYSTEM\_ARCHITECTURE.md



Paste:



\# DIP System Architecture



DIP separates decision execution from evidence storage.





┌──────────────────────┐

Decision Engine

└──────────┬───────────┘

↓

┌──────────────────────┐

Documentation Engine

(dip-cli)

└──────────┬───────────┘

↓

┌──────────────────────┐

Artifact

artifact.json

└──────────┬───────────┘

↓

┌──────────────────────┐

Decision Ledger

(dip-registry)

└──────────┬───────────┘

↓

┌──────────────────────┐

Proof

proof.json

└──────────┬───────────┘

↓

┌──────────────────────┐

Verification

(dip-go-verifier)

└──────────────────────┘



Architectural Principle



Decision execution and verification must remain independent.



Verification requires only:



artifact + proof + verifier

