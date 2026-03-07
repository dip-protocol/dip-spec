\## Abstract



Decision ledgers provide append-only evidence for automated systems.



Unlike financial ledgers, decision ledgers record cryptographic

artifacts representing system decisions.



\## Ledger Structure



The DIP decision ledger stores artifact hashes in a Merkle tree.



Properties:



append-only  

tamper-evident  

efficient inclusion proofs



\## Ledger Verification



Inclusion proofs allow independent verification that a decision

artifact was recorded in the ledger.



Verification requires only:



artifact  

proof  

verifier

