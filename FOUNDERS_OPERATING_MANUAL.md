\# DIP Founder Operating Manual



This document defines the architectural invariants of the

Decision Integrity Protocol (DIP).



All development must preserve these invariants.



---



\# 1 Protocol Vision



DIP is a foundational protocol for producing

verifiable automated decision records.



The protocol enables independent verification of

decision integrity.



---



\# 2 Protocol Philosophy



DIP follows a minimal protocol design.



The protocol defines only the primitives necessary

to produce and verify decision artifacts.



The protocol is intentionally small to enable

implementation across many environments.



---



\# 3 Core Protocol Primitives



The protocol defines four primitives.



| Primitive | Description |

|----------|-------------|

Decision | Structured decision record |

Artifact | Signed representation of a decision |

Proof | Merkle inclusion proof |

clear
Bundle | Portable verification container |



---



\# 4 Protocol Invariant



The protocol guarantees:



artifact + proof + verifier = truth



Verification must be possible offline.



---



\# 5 Architecture Boundary



The system is divided into two independent layers.



\## Documentation Engine



Responsibilities:



\- generate decision artifacts

\- perform canonicalization

\- sign artifacts

\- generate proofs

\- produce bundles



Reference implementation:



dip-cli



\## Decision Ledger



Responsibilities:



\- append artifact hashes

\- maintain Merkle tree

\- produce inclusion proofs



Reference implementation:



dip-registry



These layers must remain separate.



---



\# 6 Verification Independence



Verification must not require:



\- the decision system

\- the artifact producer

\- the ledger operator



Verification requires only:



artifact + proof + verifier



---



\# 7 Survivability Principle



No single platform must be able to terminate the protocol.



The protocol must remain verifiable even if:



\- GitHub disappears

\- the original authors disappear

\- the registry disappears



Verification depends only on artifacts and proofs.



---



\# 8 Protocol Stability



Once DIP v1 is published, the following must remain stable:



artifact structure  

proof structure  

verification algorithm  



Changes require protocol versioning.



---



\# 9 Governance



Protocol evolution occurs through proposals.



Example:



DIP-0001



All changes must preserve the core invariants.



---



\# 10 Founder Rule



When making design decisions:



Prefer minimal protocol surface.



Prefer deterministic verification.



Prefer long-term survivability over convenience.

