<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/zero-trust -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# Zero Trust with Defender for Identity

[Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview) is a security strategy for designing and implementing the following sets of security principles:

| Verify explicitly | Use least privilege access | Assume breach |
| --- | --- | --- |
| Always authenticate and authorize based on all available data points. | Limit user access with Just-In-Time and Just-Enough-Access \(JIT/JEA\), risk-based adaptive policies, and data protection. | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. |

Defender for Identity is a primary component of a Zero Trust strategy and your deployment with Microsoft Defender. Defender for Identity uses Active Directory signals to detect sudden account changes like privilege escalation or high-risk lateral movement, and reports on easily exploited identity issues like unconstrained Kerberos delegation, for correction by the security team.

## Monitoring for Zero Trust

When monitoring for Zero Trust, make sure review and mitigate open alerts from Defender for Identity together with your other security operations. You may also want to use [advanced hunting queries in Microsoft Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-overview) to look for threats in identities, devices, and cloud apps.

Tip

Ingest your alerts into [Microsoft Sentinel with Microsoft Defender](https://learn.microsoft.com/en-us/azure/sentinel/microsoft-365-defender-sentinel-integration), a cloud-native, security information event management \(SIEM\) and security orchestration automated response \(SOAR\) solution to provide your Security Operations Center \(SOC\) with a single pane of glass for monitoring security events in your enterprise.

## Next steps

Learn more about Zero Trust and how to build an enterprise-scale strategy and architecture with the [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust).

For more information, see:

- [Securing identity with Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/deploy/identity)
- [Deploy your identity infrastructure for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/deploy-identity-solution-overview)
- [Zero Trust deployment plan with Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/security/microsoft-365-zero-trust)
- [Zero Trust with Microsoft Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender/zero-trust-with-microsoft-365-defender)
