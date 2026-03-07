---



\# 1️⃣ Protocol Overview



Start the spec with:



```markdown

\# Decision Integrity Protocol (DIP)



The Decision Integrity Protocol (DIP) is an open protocol for creating, recording, and verifying automated decisions.



DIP provides cryptographic artifacts and inclusion proofs that allow any party to independently verify that a decision occurred and has not been altered.



Verification requires only:



artifact.json

proof.json

a DIP verifier



No registry or centralized service is required.

```



---



\# 2️⃣ Core Protocol Objects



DIP defines \*\*two core objects\*\*.



```text

Artifact

Proof

```



Everything in the protocol revolves around them.



---



\# 3️⃣ Artifact Format



Add this section:



````markdown

\## Artifact



A DIP artifact represents a canonical decision record.



\### Format



```json

{

&nbsp; "artifact\_version": "1.0",

&nbsp; "artifact\_id": "string",

&nbsp; "decision": { ... },

&nbsp; "signature": {

&nbsp;   "algorithm": "ed25519",

&nbsp;   "public\_key": "bytes",

&nbsp;   "value": "bytes"

&nbsp; }

}

````



````



---



\# 4️⃣ Artifact ID Rule



Add this rule:



```markdown

\### Artifact ID



artifact\_id MUST equal:



SHA256(canonical\_decision\_json)

````



Where canonicalization means:



```text

JSON parsed

re-encoded without whitespace variation

deterministic key ordering

```



This ensures \*\*deterministic artifact generation\*\*.



---



\# 5️⃣ Proof Format



Add:



````markdown

\## Proof



A proof demonstrates that an artifact was included in a decision ledger.



\### Format



```json

{

&nbsp; "artifact\_hash": "string",

&nbsp; "proof\_path": \["string"],

&nbsp; "root": "string"

}

````



````



---



\# 6️⃣ Merkle Tree Rules



Add:



```markdown

\### Merkle Tree Construction



The decision ledger constructs a Merkle tree using artifact hashes.



Rules:



1\. Leaves MUST be sorted lexicographically.

2\. Each node hash is computed as:



SHA256(left || right)



3\. If a level has an odd number of nodes, the final node is duplicated.

````



This ensures \*\*deterministic tree construction\*\*.



---



\# 7️⃣ Verification Algorithm



Add:



```markdown

\## Verification



To verify an artifact:



Inputs:



artifact.json

proof.json



Steps:



1\. Extract artifact\_id from artifact.json

2\. Verify artifact signature

3\. Compute artifact hash

4\. Reconstruct the Merkle path using proof\_path

5\. Compare computed root with proof.root



If equal:



VALID



Otherwise:



INVALID

```



---



\# 8️⃣ Protocol Invariant



Add this section:



```markdown

\## Protocol Invariant



A DIP artifact MUST be independently verifiable.



Verification requires only:



artifact.json

proof.json

verifier



No registry or centralized infrastructure is required.

```



---



\# 9️⃣ Reference Implementations



Add:



```markdown

\## Reference Implementations



The following repositories provide reference implementations of the protocol:



dip-cli

dip-registry

dip-go-verifier

```



---



\# 🔟 Protocol Philosophy



Add your core idea:



```markdown

\## Protocol Philosophy



DIP maintains a minimal immutable core.



Core primitives:



Artifact

Proof

Verification



All other components such as ledgers, registries, or tooling are implementation layers built on top of the protocol.

```



---



