<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/alert-classification-playbooks -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Alert classification playbooks for Microsoft Defender XDR

## Overview

Alert classification playbooks allow you to methodically review and quickly classify the alerts for well-known attacks and take recommended actions to remediate the attack and protect your network. Alert classification will also help in properly classifying the overall incident.

As a security researcher or security operations center \(SOC\) analyst, you must have access to the Microsoft Defender portal so that you can:

- Assess and review the generated alerts and associated incidents. See [investigate alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts).
- Search your tenant's security signal data and check for potential threats and suspicious activities. See [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview).

Note

You can provide feedback to Microsoft about true positive and false positives alerts, not only at the end of the investigation, but also during the investigation process. This can help Microsoft with future analysis and classification of security events.

## Alert classification for Microsoft Defender for Office 365

[Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about) safeguards your organization against malicious threats posed by email messages, links \(URLs\), and collaboration tools. Defender for Office 365 includes:

- Threat protection policies

  Define threat-protection policies to set the appropriate level of protection for your organization.
- Reports

  View real-time reports to monitor Defender for Office 365 performance in your organization.
- Threat investigation and response capabilities

  Use leading-edge tools to investigate, understand, simulate, and prevent threats.
- Automated investigation and response capabilities

  Save time and effort investigating and mitigating threats.

Defender for Office 365 alerts can be classified as:

- True positive \(TP\) for confirmed malicious activity.
- False positive \(FP\) for confirmed non-malicious activity.

Note

Microsoft Defender portal \([Microsoft Defender portal](https://security.microsoft.com)\) brings together functionality from existing Microsoft security portals. The Microsoft Defender portal emphasizes quick access to information, simpler layouts, and bringing related information together for easier use.

## Alert classification for Microsoft Defender for Cloud Apps

[Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps) is a Cloud Access Security Broker \(CASB\) that supports various deployment modes including log collection, API connectors, and reverse proxy. It provides rich visibility, control over data travel, and sophisticated analytics to identify and combat cyberthreats across all your Microsoft and third-party cloud services.

Defender for Cloud Apps natively integrates with leading Microsoft solutions and is designed with security professionals in mind. It provides simple deployment, centralized management, and innovative automation capabilities.

The Defender for Cloud Apps framework includes the capability to protect your network against cyberthreats and anomalies, detects unusual behavior across cloud apps to identify ransomware, compromised users or rogue applications. It enables the analysis of high-risk usage and can remediate automatically to limit the risk to your organization.

Defender for Cloud Apps alerts can be classified as:

- TP for confirmed malicious activity.
- Benign true positive \(B-TP\) for suspicious but not malicious activity, such as a penetration test or other authorized suspicious action.
- FP for confirmed non-malicious activity.

## Available alert classification playbooks

See these playbooks for steps to more quickly classify alerts for the following threats:

- [Suspicious email forwarding activity](https://learn.microsoft.com/en-us/defender-xdr/alert-grading-playbook-email-forwarding)
- [Suspicious inbox manipulation rules](https://learn.microsoft.com/en-us/defender-xdr/alert-grading-playbook-inbox-manipulation-rules)
- [Suspicious inbox forwarding rules](https://learn.microsoft.com/en-us/defender-xdr/alert-grading-playbook-inbox-forwarding-rules)
- [Suspicious IP addresses related to password spray activity](https://learn.microsoft.com/en-us/defender-xdr/alert-classification-suspicious-ip-password-spray)
- [Password spray attacks](https://learn.microsoft.com/en-us/defender-xdr/alert-classification-password-spray-attack)
- [Malicious Exchange connectors](https://learn.microsoft.com/en-us/defender-xdr/alert-classification-malicious-exchange-connectors)

See [Investigate alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts) for information on how to examine alerts with the Microsoft Defender portal.

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
