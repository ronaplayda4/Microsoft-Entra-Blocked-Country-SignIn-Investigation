# Microsoft Entra Blocked Country Sign-In Investigation

### Microsoft Sentinel | Microsoft Defender XDR | Microsoft Entra ID

## Project Overview

This project documents a SOC investigation of a Microsoft 365 sign-in attempt from Switzerland that was blocked by Microsoft Entra Conditional Access.

The activity was generated during an authorized security simulation to evaluate geographic access restrictions, Microsoft Sentinel detection capabilities, and incident response procedures.

**Incident ID:** 477  
**Severity:** Medium  
**Detection:** Blocked Country Sign-In - Conditional Access  
**Final Status:** Resolved  
**Classification:** Informational, expected activity — Security testing

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

A test account attempted to access One Outlook Web using a Switzerland VPN connection.

Microsoft Entra ID identified the source location as Switzerland and blocked the sign-in under the configured Conditional Access policy.

The sign-in generated error **53003**, indicating that token issuance was blocked.

A Microsoft Sentinel scheduled analytics rule detected the event and generated an alert in Microsoft Defender XDR under Incident 477.

Additional IP reputation analysis identified VPN/proxy characteristics. VirusTotal reported 2 detections out of 92 security vendors. These indicators alone did not establish malicious activity.

## Investigation Workflow

1. Simulated a Microsoft 365 sign-in from Switzerland using an authorized test account.
2. Reviewed Microsoft Entra sign-in logs and confirmed Conditional Access error 53003.
3. Investigated the Microsoft Sentinel detection and associated Defender XDR incident.
4. Analyzed the source IP using VirusTotal and WHOIS.
5. Documented findings and confirmed the investigated sign-in was blocked.
6. Resolved Incident 477 and its associated alert as expected security testing activity.

## Outcome

The configured Conditional Access policy successfully blocked the investigated sign-in. Microsoft Sentinel generated the expected detection, and the associated Microsoft Defender XDR incident was investigated and resolved.

No unauthorized access was established from the investigated attempt. Other sessions were not exhaustively assessed.

**Final disposition:** Informational, expected activity — Security testing.

## Key Takeaways

This investigation provided hands-on experience with identity security monitoring, geographic access restrictions, KQL-based detection, threat intelligence analysis, and SOC incident documentation.

It demonstrates how Microsoft Entra ID, Microsoft Sentinel, and Microsoft Defender XDR can work together to detect and investigate identity-related security events.

## Disclaimer

This project was conducted in an authorized Microsoft 365 security lab. All activity was performed for educational and defensive security testing purposes. Sensitive account and tenant information should be redacted from publicly shared evidence.
