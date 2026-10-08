# Microsoft Entra Blocked Country Sign-In Investigation

### Microsoft Sentinel | Microsoft Defender XDR | Microsoft Entra ID

## Project Overview

This project documents a Security Operations Center (SOC) investigation of a Microsoft 365 sign-in attempt from Switzerland that was blocked by Microsoft Entra Conditional Access.

The activity was conducted as part of an authorized security simulation to evaluate geographic access restrictions, Microsoft Sentinel detection capabilities, and incident response procedures.

## Incident Overview

| Field | Details |
|---|---|
| Incident ID | 477 |
| Severity | Medium |
| Alert | Blocked Country Sign-In - Conditional Access |
| Source Location | Switzerland (CH) |
| Application | One Outlook Web |
| Error Code | 53003 |
| Detection Source | Microsoft Sentinel |
| Incident Status | Resolved |
| Classification | Informational, expected activity — Security testing |

## Tools Used

- Microsoft Entra ID
- Microsoft Entra Conditional Access
- Microsoft Sentinel
- Microsoft Defender XDR
- Kusto Query Language (KQL)
- VirusTotal
- WHOIS
- Proton VPN

## Investigation Summary

During an authorized security simulation, a test account attempted to access Microsoft 365 through One Outlook Web using a Switzerland VPN connection.

Microsoft Entra ID evaluated the sign-in against the configured Conditional Access policy and blocked token issuance, returning error code **53003**.

Microsoft Sentinel detected the blocked sign-in through a scheduled analytics rule and generated an alert in Microsoft Defender XDR under Incident 477.

Threat intelligence analysis using VirusTotal identified VPN/proxy indicators, with 2 out of 92 security vendors flagging the source IP. WHOIS information associated the IP with M247 Europe SRL (AS9009). These findings alone did not establish malicious activity.

## Investigation Workflow

1. **Sign-In Simulation:** Attempted Microsoft 365 authentication through an authorized Switzerland VPN connection.
2. **Sign-In Log Analysis:** Reviewed Microsoft Entra sign-in logs and confirmed Conditional Access error 53003.
3. **Detection Analysis:** Investigated the Microsoft Sentinel scheduled analytics rule and its generated alert.
4. **Incident Investigation:** Examined Microsoft Defender XDR Incident 477 and the associated sign-in activity.
5. **Threat Intelligence:** Analyzed the source IP using VirusTotal and WHOIS.
6. **Resolution:** Documented findings and resolved the incident and associated alert as expected security testing activity.

## Investigation Findings

The configured Conditional Access policy successfully blocked the investigated sign-in attempt from Switzerland.

Microsoft Sentinel generated the expected detection, and Microsoft Defender XDR created Incident 477 for investigation.

The investigated sign-in did not result in token issuance. No unauthorized access was established from the reviewed attempt, although other account sessions were not exhaustively assessed.

## Remediation and Resolution

The existing Conditional Access policy successfully prevented access. No additional containment was required for this authorized simulation.

The incident and associated alert were resolved with the classification:

**Informational, expected activity — Security testing.**

## Key Takeaways

This investigation provided practical experience with:

- Identity security monitoring and geographic access restrictions
- Microsoft Entra sign-in log analysis
- KQL-based detection and Microsoft Sentinel analytics
- Microsoft Defender XDR incident investigation
- Threat intelligence enrichment
- SOC documentation and incident resolution

## Full Investigation Report

The complete investigation report contains the Findings, Investigation, WHO/WHAT/WHEN/WHERE/WHY/HOW analysis, Recommendations, and supporting evidence screenshots.

[View Full SOC Investigation Report](SOC_Incident_477_Blocked_Country_SignIn_Investigation.docx)

## Disclaimer

This investigation was conducted in an authorized Microsoft 365 security lab for educational and defensive security testing purposes. Sensitive account and tenant information should be redacted before public sharing.
