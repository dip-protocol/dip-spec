\# DIP v1.0 Protocol Release



Release Date: 2026-03-07



This document announces the first stable release of the

Decision Integrity Protocol (DIP).



---



\# Overview



DIP defines a minimal protocol for producing cryptographically

verifiable records of automated decisions.



The protocol enables independent verification of decision integrity.



---



\# Protocol Components



DIP v1.0 defines the following primitives.



| Primitive | Description |

|---|---|

Decision | Structured decision record |

Artifact | Signed representation of the decision |

Proof | Merkle inclusion proof |

Bundle | Portable verification container |



---



\# Protocol Pipeline



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



Verification Result



---



\# Protocol Guarantees



The protocol guarantees:



artifact + proof + verifier = truth



Verification must be possible offline.



---



\# Reference Implementations



The following reference implementations exist.



| Repository | Role |

|---|---|

dip-cli | Documentation Engine |

dip-registry | Decision Ledger |

dip-go-verifier | Independent verifier |



---



\# Specification



Canonical protocol specification:



spec/v1/dip.md



---



\# Schemas



The following schemas define protocol structures.



artifact.schema.json  

decision.schema.json  

proof.schema.json  



---



\# Conformance



Protocol conformance tests exist in:



conformance/



---



\# Security Model



DIP v1.0 uses:



SHA256 hashing  

Ed25519 signatures  

Merkle inclusion proofs  



Threat model:



docs/DIP\_THREAT\_MODEL.md



---



\# Governance



Protocol evolution occurs through

DIP Improvement Proposals.



Example:



DIP-0001



---



\# Stability



DIP v1.0 defines the stable protocol core.



The following elements are considered stable:



artifact format  

proof format  

verification algorithm  



Changes require a new protocol version.



---



\# Conclusion



DIP v1.0 introduces a minimal protocol for verifiable

automated decision records.



The protocol enables independent verification of decisions

across systems and organizations.

