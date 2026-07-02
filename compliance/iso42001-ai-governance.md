# Provost Inc — ISO/IEC 42001 AI Governance

ISO 42001 is the AI Management System standard. Provost Inc uses AI/ML-powered 
security tooling; this documents responsible governance of that AI use.

## AI System Inventory
| AI System | Purpose | Risk Level | Human Oversight |
|-----------|---------|-----------|-----------------|
| Sentinel UEBA | Behavioral anomaly detection | Medium | Analyst reviews anomalies before action |
| Defender ML detections | Threat detection | Medium | Alerts triaged by human before response |
| Automated playbooks | Incident response | Medium-High | Notification auto; destructive actions require human approval |

## AI Risk Register
| Risk | Description | Mitigation |
|------|-------------|-----------|
| False positives | AI flags legitimate activity as malicious | Human-in-the-loop before any destructive action |
| Automation overreach | Playbook disables a legitimate user | Destructive playbooks manual-approval only, never auto-triggered |
| Model opacity | Cannot explain an AI verdict | Analyst investigates underlying logs, not just the AI output |
| Over-reliance | Team trusts AI without verification | Detections validated against raw telemetry (demonstrated in Sprint 7) |

## Human Oversight Evidence
The Sprint 7 investigation demonstrates ISO 42001 principles in practice: 
an AI/rule-based detection was not blindly trusted — the analyst investigated 
the raw SecurityEvent data, identified a detection gap, and refined the 
detection. Automated response was limited to notification; no destructive 
action occurs without human decision.

## Why This Matters
ISO 42001 is emerging as the key standard for governing enterprise AI. 
Demonstrating responsible-AI controls — inventory, risk assessment, and 
maintained human oversight — positions this portfolio ahead of the curve, 
directly aligned with the AI-security focus of newer certifications (e.g. SC-500).
