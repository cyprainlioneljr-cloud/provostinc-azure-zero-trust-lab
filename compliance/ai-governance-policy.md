# Provost Inc Responsible AI Usage Policy

## Purpose
Govern the responsible use of AI/ML within Provost Inc's security operations, 
consistent with ISO/IEC 42001.

## Principles
1. **Human judgment is primary.** AI assists security operations; it does not 
   replace human decision-making.
2. **Human review before destructive action.** Any AI/automation-flagged 
   incident receives human review before an account is disabled, a host is 
   isolated, or access is revoked.
3. **Auditability.** All AI-influenced decisions must be traceable to the 
   underlying data (logs, events) that informed them.
4. **Continuous oversight.** Human oversight is maintained throughout the 
   incident lifecycle ; detection, triage, response, and closure.
5. **Validation over trust.** AI detections are validated against raw 
   telemetry rather than accepted at face value.

## Scope
Applies to all AI/ML-powered security tooling in the Provost Inc environment, 
including Sentinel UEBA, Defender ML detections, and automated playbooks.
