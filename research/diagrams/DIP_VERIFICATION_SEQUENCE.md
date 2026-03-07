\# DIP Verification Sequence



Verifier performs the following steps.





Verifier

│

│ parse artifact

│

│ canonicalize artifact

│

│ verify signature

│

│ compute artifact hash

│

│ validate Merkle proof

│

│ compare ledger root

│

▼



Verification Result





\## Validation Rules



| Step | Check |

|----|------|

Parse | valid JSON |

Canonicalize | deterministic encoding |

Signature | Ed25519 verification |

Artifact hash | SHA256 match |

Merkle proof | path validation |

Root | ledger root match |



If all checks succeed → artifact valid.

