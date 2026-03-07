\# DIP Protocol Pipeline





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





\## Pipeline Stages



| Stage | Component |

|------|-----------|

Decision creation | external system |

Artifact generation | dip-cli |

Ledger append | dip-registry |

Proof generation | dip-cli |

Bundle creation | dip-cli |

Verification | dip-go-verifier |



\## Key Property



artifact + proof + verifier = truth

