\# Decision Integrity Protocol Specification (DIP)



The \*\*Decision Integrity Protocol (DIP)\*\* defines a minimal standard for producing \*\*verifiable automated decision artifacts\*\*.



A DIP artifact contains:



\* Decision inputs and outputs

\* Deterministic artifact hash

\* Cryptographic signature

\* Optional transparency log inclusion proof



Artifacts created using the protocol can be verified \*\*independently and offline\*\*.



---



\# Protocol Goals



DIP is designed to ensure that automated decisions can be:



\* Verified independently

\* Audited deterministically

\* Preserved for long-term verification

\* Implemented across multiple languages



---



\# Core Protocol Concepts



\## Decision Artifact



The primary protocol object is the \*\*decision artifact\*\*.



It contains:



```

artifact\_version

artifact\_id

decision

signature

```



The artifact hash is defined as:



```

artifact\_id = SHA256(canonical artifact)

```



---



\# Canonicalization



Artifacts must be serialized using \*\*deterministic canonical JSON\*\*.



Rules:



\* Object keys sorted lexicographically

\* No extra whitespace

\* UTF-8 encoding



Canonicalization ensures artifacts produce \*\*stable hashes and signatures\*\*.



---



\# Cryptographic Signing



Artifacts are signed using:



```

Ed25519

```



Signing procedure:



```

artifact (without signature)

&nbsp;   ↓

canonicalization

&nbsp;   ↓

SHA256 hash

&nbsp;   ↓

Ed25519 signature

```



---



\# Verification



Artifacts can be verified independently using any DIP-compatible verifier.



Verification process:



```

artifact

&nbsp;  ↓

remove signature

&nbsp;  ↓

canonicalize artifact

&nbsp;  ↓

recompute artifact\_id

&nbsp;  ↓

verify signature

```



---



\# Protocol Architecture



```

dip-spec

&nbsp;   protocol specification



dip-cli

&nbsp;   artifact creation



dip-registry

&nbsp;   transparency log



dip-go-verifier

&nbsp;   Go artifact verifier



dip-js-verifier

&nbsp;   JavaScript verifier

```



---



\# License



Apache License 2.0



