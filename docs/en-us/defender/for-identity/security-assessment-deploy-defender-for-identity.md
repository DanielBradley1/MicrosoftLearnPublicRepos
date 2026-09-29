<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/security-assessment-deploy-defender-for-identity -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Security assessment: Start your Defender for Identity deployment

This article describes the **Start your Defender for Identity deployment** security assessment, which encourages you to install sensors on domain controllers and other eligible servers. This assessment identifies servers in your environment that lack a Defender for Identity sensor and helps you understand the security risks of incomplete deployment. Use this guide to review the assessment findings in Microsoft Secure Score and take action to deploy sensors across your infrastructure.

## Why is not having Defender for Identity deployed considered a risk?

If you've obtained a Defender for Identity license, but haven't yet deployed Defender for Identity sensors, not only are you not yet using your purchased services, but you may be missing advanced threats in your identity infrastructure.

Defender for Identity uses your on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.

Defender for Identity is also part of monitoring for Zero Trust. You may also want to use [advanced hunting queries in Microsoft Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-overview) to look for threats in identities, devices, and cloud apps.

For more information, see:

- [What is Microsoft Defender for Identity?](https://learn.microsoft.com/en-us/defender-for-identity/what-is)
- [Zero Trust with Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/zero-trust)

## How do I use this security assessment?

Use the following steps to review this assessment and remediate it.

1. Review the recommended action at [https://security.microsoft.com/securescore?viewid=actions](https://security.microsoft.com/securescore?viewid=actions) to be alerted if you have a Defender for Identity license, but don't have Defender for Identity deployed.
2. Take appropriate action by deploying Defender for Identity. For more information, see [Deploy Microsoft Defender for Identity with Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-for-identity/deploy-defender-identity).

Note

While assessments are updated in near real time, scores and statuses are updated every 24 hours. While the list of impacted entities is updated within a few minutes of your implementing the recommendations, the status may still take time until it's marked as **Completed**.

## Related content

- [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score)
- [Microsoft Defender for Identity community forum](https://aka.ms/MDIcommunity)
