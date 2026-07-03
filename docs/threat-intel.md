# Provost Inc Threat Intelligence Integration

## Objective
Enrich detections with known-bad indicators (malicious IPs, domains, hashes) 
so activity in the SOC can be matched against current threat data.

## Configuration
- Threat Intelligence solution installed from Content Hub
- Connector framework in place for ingesting indicators (TAXII / Defender TI)

## Why This Matters
When the end-phase honeypot logs an attacker IP, threat-intel matching lets 
Sentinel automatically flag whether that IP is a known malicious actor
turning raw logs into context-rich, production-grade detections.

## Status
Connector framework configured; specific feed to be finalized alongside 
detection engineering in Sprint 5.
