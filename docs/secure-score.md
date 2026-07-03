# Provost Inc  Defender for Cloud Secure Score

## Objective
Establish a measurable security posture baseline using Microsoft Defender 
for Cloud's free Foundational CSPM tier, then improve it through remediation.

## Cost Control
- Only the free Foundational CSPM tier is used (Secure Score + recommendations)
- All paid Defender plans confirmed OFF to avoid per-resource auto-charges 
  after the 30-day free window

## Baseline
- Initial secure score captured shortly after resource deployment
- Note: Defender assessments populate over several hours to a day; the 
  earliest score showed items "not evaluated" and is therefore a preliminary 
  baseline. A matured score and full recommendation set were captured after 
  assessments completed.

## Remediation
- Reviewed recommendations and remediated at least one item
- Example: restricting RDP exposure (see network-security.md) addresses the 
  "management ports should be restricted" recommendation
- Re-checked score to confirm improvement (before/after evidence captured)

## Why This Matters
Secure Score turns security posture into a measurable, trackable metric. 
Demonstrating a before/after improvement proves not just deployment, but 
active hardening the difference between standing up resources and 
securing them.
