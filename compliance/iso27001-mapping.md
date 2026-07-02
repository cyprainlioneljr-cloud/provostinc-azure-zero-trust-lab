# Provost Inc — ISO/IEC 27001:2022 Control Mapping

This maps the technical controls implemented across the lab to ISO 27001 
Annex A controls, demonstrating the environment satisfies recognized 
information-security governance requirements.

| Annex A Control | Provost Inc Implementation | Sprint |
|-----------------|---------------------------|--------|
| A.5.7 Threat intelligence | Threat intelligence connector in Sentinel | 4 |
| A.5.15 Access control | RBAC, custom least-privilege roles | 3 |
| A.5.16 Identity management | Entra ID users, groups, lifecycle (J/M/L) | 2, 3 |
| A.5.17 Authentication information | MFA enforced via Conditional Access | 2 |
| A.5.18 Access rights | Access Reviews, PIM eligible roles | 2, 8 |
| A.5.25 Assessment of security events | Incident investigation, SOAR playbooks | 6, 7 |
| A.8.2 Privileged access rights | PIM just-in-time activation | 2 |
| A.8.5 Secure authentication | MFA, risk-based Conditional Access (CA02) | 2, 5 |
| A.8.7 Protection against malware | Microsoft Defender for Cloud | 3 |
| A.8.15 Logging | Log Analytics, Sentinel data connectors | 4 |
| A.8.16 Monitoring activities | Analytics rules, UEBA, detection engineering | 5 |
| A.8.20 Network security | NSGs, RDP restriction | 3 |
| A.8.23 Web/resource filtering | NSG inbound controls | 3 |
| A.8.28 Secure coding | (Documented as future enhancement) | — |

## Why This Matters
This mapping reframes hands-on Azure work as implementation of an 
internationally recognized security framework — demonstrating not just 
technical ability, but the governance literacy to connect controls to 
standards. This is what turns a lab into audit-ready evidence.
