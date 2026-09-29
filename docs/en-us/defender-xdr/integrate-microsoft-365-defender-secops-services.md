<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/integrate-microsoft-365-defender-secops-services -->
<!-- Sitemap-Last-Modified: 2026-08-07 -->

# Step 3. Plan for Microsoft Defender XDR integration with your SOC catalog of services

**Applies to:**

- Microsoft Defender XDR

## SOC services and Microsoft Defender XDR components

This section lists common SOC service areas and introduces the Microsoft Defender XDR components that map to those functions, so your team can plan integration and assign responsibilities.

An established Security Operations Center \(SOC\) should have a catalog of services that might include:

- Intrusion & malware analysis
- Attribution & reverse engineering
- Threat intelligence
- Analytics
- Hunting investigation
- Forensics
- Incident response
- Computer Security Incident Response Team \(CSIRT\) \(that may be segregated from SOC\)
- Compliance testing
- Insider threat & fraud monitoring
- Security incident & event monitoring
- Vulnerability scanning
- Extended Detection and Response \(XDR\)/Security Orchestration, Automation, and Response \(SOAR\)
- Phishing
- Data loss prevention
- Brand monitoring

The components of Microsoft Defender XDR are:

- **Microsoft Defender for Identity** \(formerly Azure Advanced Threat Protection, also known as Azure ATP\) is a cloud-based security solution that uses Active Directory Domain Services \(AD DS\) signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at organizations.
- **Microsoft Defender for Endpoint** is a holistic, cloud delivered endpoint security solution for devices that includes risk-based vulnerability management and assessment, attack surface reduction, behavioral based and cloud-powered next generation protection, endpoint detection and response \(EDR\), automatic investigation and remediation, managed hunting services, rich APIs, and unified security management.
- **Microsoft Defender for Office 365** is a cloud-based email filtering service that helps protect organizations against unknown malware and viruses by providing robust zero-day protection and includes features to safeguard organizations from harmful links in real time. It also offers a comprehensive slate of investigation and hunting, response and remediation, awareness and training, and secure posture features.
- **Microsoft Defender for Cloud Apps** is a cloud access security broker \(CASB\) that supports various deployment modes including log collection, API connectors, and reverse proxy. It provides rich visibility, control over data travel, and sophisticated analytics to identify and combat cyberthreats across all Microsoft and third-party cloud services.

Because Microsoft Defender XDR components and technologies span various functions, your SOC team will need to determine which roles and responsibilities are best suited to manage each component of Microsoft Defender XDR and align to service function.

To integrate the capabilities of Microsoft Defender XDR, you will need to refine your SOC catalog of services. For more information about the capabilities of Microsoft Defender XDR, see the following articles:

- [What is Microsoft Defender for Endpoint?](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [What is Microsoft Defender for Identity?](https://learn.microsoft.com/en-us/defender-for-identity/what-is)
- [What is Defender for Office 365?](https://learn.microsoft.com/en-us/defender-office-365/mdo-about)
- [What is Microsoft Defender for Cloud Apps?](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps)

## Next step

[Next: Define Microsoft Defender XDR roles, responsibilities, and oversight](https://learn.microsoft.com/en-us/defender-xdr/integrate-microsoft-365-defender-secops-roles)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
