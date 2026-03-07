\# DIP Quickstart



This guide shows how to create and verify a decision artifact

using the Decision Integrity Protocol.



\## 1 Create a Decision Record



Create a file named `decision.json`.



Example:



```json

{

&nbsp; "decision\_id": "deploy-001",

&nbsp; "timestamp": "2026-03-07T10:00:00Z",

&nbsp; "inputs": {

&nbsp;   "environment": "production"

&nbsp; },

&nbsp; "outputs": {

&nbsp;   "approved": true

&nbsp; }

}

2 Generate an Artifact



Run:



dip sign decision.json



Output:



artifact.json

3 Generate a Proof



Run:



dip proof artifact.json



Output:



proof.json

4 Create a Bundle



Run:



dip bundle artifact.json proof.json



Output:



decision.dip

5 Verify the Artifact



Run:



dip verify decision.dip



Output:



DIP bundle verification: VALID

Protocol Guarantee



Verification requires only:



artifact + proof + verifier = truth



No access to the original system is required.

