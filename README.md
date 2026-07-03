# 🛡️ Provost Inc. Azure Zero Trust SOC Lab.

An enterprise grade, fully documented Security Operations Center lab built on 
Microsoft Azure,demonstrating end-to-end SOC engineering, identity 
governance, detection engineering, automated response, and compliance mapping.

## 🎯 What This Project Demonstrates
- **SOC Operations** — Microsoft Sentinel SIEM, KQL detection engineering, incident response
- **Identity & Access** — Entra ID, Conditional Access, MFA, PIM, Access Reviews, lifecycle management
- **Cloud Security** — RBAC, custom roles, Key Vault, NSGs, Defender for Cloud
- **Automation (SOAR)** — Logic Apps playbooks, automated detect→respond pipeline
- **Attack Simulation** — Atomic Red Team, validated detections, real investigation
- **Governance** — ISO 27001 control mapping, ISO 42001 AI governance, audit evidence

## 🎓 Certifications Mapped
CompTIA Security+ · AZ-104 · AZ-500 · SC-200 · SC-300 · ISO 27001 · ISO 42001

## 🏗️ Architecture
| Layer | Technology |
|-------|-----------|
| Cloud | Microsoft Azure |
| SIEM/SOAR | Microsoft Sentinel (Defender portal) |
| Identity | Microsoft Entra ID (P2) |
| Security posture | Microsoft Defender for Cloud |
| Automation | Azure Logic Apps |
| Attack simulation | Atomic Red Team |

## 📁 Repository Guide
| Folder | Contents |
|--------|----------|
| docs/ | Architecture, infrastructure, RBAC, detection engineering |
| identity-access/ | Users, groups, Conditional Access, PIM, SSO, lifecycle |
| kql-queries/ | KQL hunting query library |
| sentinel-rules/ | Analytics rule definitions |
| playbooks/ | SOAR automation playbooks + Graph scripts |
| incident-reports/ | Real investigation writeups |
| compliance/ | ISO 27001 & ISO 42001 evidence |
| cost-tracker/ | Monthly spend & cost management |
| screenshots/ | Visual evidence |

## 🔑 Highlight: End-to-End Detection & Response
Executed a real attack (Atomic Red Team) → identified a detection gap → 
investigated raw telemetry → authored a custom analytics rule → wired an 
automated playbook → validated the full chain: 
**attack → detect → incident → automate → SOC alert.**
See `incident-reports/incident-001-discovery-activity.md`.

## 💰 Cost Management
Built on a controlled budget (<$50/month) using auto-shutdown, VM 
deallocation, free-tier services, and trial licensing — with full spend 
tracking throughout. See `cost-tracker/`.

## 🗺️ Sprint Journey
| # | Sprint | Focus |
|---|--------|-------|
| 1 | Foundation | Azure + GitHub setup |
| 2 | Identity | Entra ID, MFA, Conditional Access, PIM |
| 3 | Hardening | VM, NSG, Key Vault, RBAC, custom roles, lifecycle |
| 4 | SOC Deployment | Sentinel, connectors, threat intel, SSO/federation |
| 5 | Detection Engineering | KQL, analytics rules, UEBA, identity monitoring |
| 6 | Automation | Logic Apps playbooks, SOAR chain |
| 7 | Attack Simulation | Atomic Red Team, detection validation |
| 8 | Governance | Access Reviews, ISO 27001 & 42001 mapping |
| 9 | Portfolio | Graph automation, finalization |

## 📊 Project Status: 9/9 Sprints Complete ✅

---
*A portfolio project demonstrating real-world Azure security engineering and 
SOC analyst capability — from foundation to live operations.*
* Claude AI and Chatgpt was used in some situations.
