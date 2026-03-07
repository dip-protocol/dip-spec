\# DIP Artifact Lifecycle



A DIP artifact progresses through the following lifecycle.



\## 1 Creation



A decision record is produced by an automated system.





decision.json





\## 2 Artifact Generation



The decision is signed.





dip sign decision.json





Output:





artifact.json





\## 3 Ledger Inclusion



The artifact is appended to the decision ledger.





dip proof artifact.json





Output:





proof.json





\## 4 Bundle Creation



The artifact and proof are packaged.





dip bundle artifact.json proof.json





Output:





decision.dip





\## 5 Verification



The artifact is verified independently.





dip verify decision.dip





Verification ensures:



\- signature validity

\- artifact integrity

\- ledger inclusion

