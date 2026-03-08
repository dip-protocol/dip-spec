DIP Protocol v1 Test Vector



Files:



artifact.json

&nbsp;   Signed decision artifact.



proof.json

&nbsp;   Merkle inclusion proof produced by dip-registry.



merkle-root.txt

&nbsp;   Expected Merkle root of the registry.



Verification procedure:



1\. Compute artifact\_id = SHA256(canonical(decision))

2\. Verify Ed25519 signature on the artifact.

3\. Recompute the Merkle root using artifact\_id and proof.json.

4\. The computed root must match merkle-root.txt.



If all checks pass:



artifact + proof + verifier = truth

