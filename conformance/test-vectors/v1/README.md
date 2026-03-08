\# DIP v1 Test Vectors



This directory contains reference artifacts used to verify independent DIP implementations.



Files:



artifact.json

&nbsp;   Canonical DIP artifact.



proof.json

&nbsp;   Merkle inclusion proof for the artifact.



merkle-root.txt

&nbsp;   Expected Merkle root of the registry log.



\## Verification Procedure



An implementation must verify:



1\. Artifact canonicalization

2\. Artifact ID correctness

3\. Signature validity

4\. Merkle proof inclusion

5\. Merkle root consistency



If all checks pass, the artifact is considered valid under DIP v1.



Protocol invariant:



artifact + proof + verifier = truth

