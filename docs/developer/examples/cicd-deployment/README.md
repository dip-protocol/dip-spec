\# CI/CD Deployment Decision Example



This example demonstrates recording a deployment decision using DIP.



\## Workflow



Generate artifact:



dip sign decision.json



Generate proof:



dip proof artifact.json



Create bundle:



dip bundle artifact.json proof.json



Verify decision:



dip verify decision.dip



\## Use Case



Deployment pipelines can produce verifiable decision artifacts for

production releases.

