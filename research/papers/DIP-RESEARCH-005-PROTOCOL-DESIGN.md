\# Protocol Design of DIP



\## Goals



The protocol is designed with the following goals:



minimalism  

deterministic verification  

implementation independence  

survivability



\## Minimal Surface



DIP intentionally defines only a small set of primitives:



decision  

artifact  

proof  

bundle



This minimal design allows implementations in many environments.



\## Survivability Principle



The protocol must survive the disappearance of any single platform.



Verification requires only:



artifact + proof + verifier

