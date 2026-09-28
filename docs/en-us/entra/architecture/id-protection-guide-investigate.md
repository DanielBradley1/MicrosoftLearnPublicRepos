<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-investigate -->
<!-- Sitemap-Last-Modified: 2025-11-02 -->

# Microsoft Entra ID Protection scenario: Identity risk-related telemetry in security investigations

The proof-of-concept \(PoC\) guidance in this series of articles helps you to learn, deploy, and test Microsoft Entra ID Protection to detect, investigate, and remediate identity-based risks.

An overview of the guidance begins with [Introduction to Microsoft Entra ID Protection proof-of-concept guidance](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-introduction).

Detailed guidance continues with these scenarios:

- [Use real-time risk detection to grant access to protected resources](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-detect)
- [Master risk analysis for effective remediation](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-analyze)
- [Allow users to self-remediate identity risk for enterprise-managed resources](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-remediate)

This article helps Security Operations Center \(SOC\) administrators to bring identity risk-related telemetry into security investigations.

Configure the following features for identity risk-related telemetry with Microsoft Entra ID Protection:

- [Investigate identity-based incidents](#investigate-identity-based-incidents)
- [Investigate with Microsoft Security Copilot](#investigate-with-microsoft-security-copilot-in-microsoft-entra)
- [Remediate and respond](#remediate-and-respond)
- [Review for audit and compliance](#review-for-audit-and-compliance)
- [Configure access in multitenant environments](#configure-access-in-multitenant-environments)

## Investigate identity-based incidents

Detect and investigate identity threats in the Microsoft Entra admin center or with Microsoft Graph APIs:

1. [Risky sign-ins](https://learn.microsoft.com/en-us/entra/id-protection/concept-risk-reports#risky-sign-ins) such as [impossible travel](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk#atypical-travel-detections), [anonymous IPs, and malware-linked IPs](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk#malicious-ip-address-detections).
2. [Risky users](https://learn.microsoft.com/en-us/entra/id-protection/concept-risk-reports#risky-users) such as accounts with [leaked credentials](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk#leaked-credentials-detections) and [suspicious behavior](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk#password-spray-detections).
3. [Risk detections](https://learn.microsoft.com/en-us/entra/id-protection/concept-risk-reports#risk-detections) such as [token replay](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk#anomalous-token-and-token-issuer-anomaly-detections) and unfamiliar sign-in properties.

## Investigate with Microsoft Security Copilot in Microsoft Entra

Microsoft Security in Microsoft Entra brings together the power of artificial intelligence \(AI\) and human expertise to help admins and security teams to respond to threats and attacks faster. Through the embedded experience, you can investigate and resolve identity risks, assess identities, and quickly access complete complex tasks.

Use natural language prompts in [Microsoft Security Copilot](https://learn.microsoft.com/en-us/entra/security-copilot/entra-investigate-incident):

- Summarize why a user is risky.
- Retrieve sign-in logs, audit trails, and group memberships.
- Get remediation recommendations and links to documentation.

Learn more about [Microsoft Security Copilot scenarios](https://learn.microsoft.com/en-us/entra/security-copilot/entra-security-scenarios) in Microsoft Entra.

## Remediate and respond

After you confirm a threat:

1. Track that [risk-based Conditional Access](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-policies) was triggered to block or challenge access.
2. Manually dismiss or confirm compromise to [remediate risks and unblock users](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-remediate-unblock#administrator-manual-remediation).
3. [Initiate secure password resets or MFA re-registration](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-user-experience).
4. Use response playbooks to guide next steps.

## Review for audit and compliance

Log and audit all SOC actions in Microsoft Entra to perform the following steps:

1. Review logs in the Microsoft Entra admin center.
2. For correlation and storage, export logs to [Azure Monitor Log Analytics](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-analyze-activity-logs-log-analytics), [Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/overview?tabs=defender-portal), or your dedicated security information and event management \(SIEM\) system.
3. Generate alerts for specific actions such as policy changes, user unblocks.

## Configure access in multitenant environments

For [multitenant environments](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/defender-xdr-microsoft-entra-mto):

1. Configure [cross-tenant access policies](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-overview).
2. To limit scope, use [role-based access control](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-overview) \(such as Security Reader, Security Operator\).
3. Automate deployment with [PowerShell or Microsoft Graph APIs](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-graph-api).

## Next steps

- [Introduction to Microsoft Entra ID Protection proof-of-concept guidance](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-introduction)
- [Use real-time risk detection to grant access to protected resources](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-detect)
- [Master risk analysis for effective remediation](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-analyze)
- Bring identity risk-related telemetry into security investigations
- [Allow users to self-remediate identity risk for enterprise-managed resources](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-remediate)
