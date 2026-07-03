# Provost Inc , Detection Engineering

## Objective
Transform raw log data into actionable detections using KQL hunting queries, 
scheduled analytics rules, and visualization workbooks.

## The Detection Pipeline
\```
Log ingested (SigninLogs/AuditLogs)
   → KQL query identifies suspicious pattern
   → Scheduled analytics rule runs the query on a timer
   → Alert generated when threshold met
   → Incident created (Defender XDR correlation engine)
   → Analyst investigates via mapped entities
\```

## What Was Built
- **KQL hunting library** : sign-in and audit-log queries (see /kql-queries)
- **Custom analytics rule** : "Provost - Multiple Failed Sign-Ins" (brute-force detection)
- **Template rules** : installed and studied Microsoft's pre-built scheduled 
  rules (e.g. "Brute force attack against Azure Portal") to learn detection patterns
- **Workbook** : Entra ID sign-in dashboard for visual monitoring

## Tools and Locations
- **Advanced hunting** (Defender portal) : for running raw KQL
- **Microsoft Sentinel → Configuration → Analytics** : for analytics rules
- **Microsoft Sentinel → Threat management → Workbooks** : for dashboards

## Why This Matters
Detection engineering is the core of SOC operations. Collecting logs is 
passive; detection engineering is where raw telemetry becomes the ability 
to actually catch and respond to threats.
