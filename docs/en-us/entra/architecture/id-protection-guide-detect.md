<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-detect -->
<!-- Sitemap-Last-Modified: 2025-11-02 -->

# Microsoft Entra ID Protection scenario: Real-time risk detection for protected resources

The proof-of-concept \(PoC\) guidance in this series of articles helps you to learn, deploy, and test Microsoft Entra ID Protection to detect, investigate, and remediate identity-based risks.

An overview of the guidance begins with [Introduction to Microsoft Entra ID Protection proof-of-concept guidance](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-introduction).

Detailed guidance continues with these scenarios:

- [Master risk analysis for effective remediation](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-analyze)
- [Bring identity risk-related telemetry into security investigations](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-investigate)
- [Allow users to self-remediate identity risk for enterprise-managed resources](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-remediate)

This article helps identity administrators use real-time risk detection features in Microsoft Entra ID Protection to grant user access to protected resources. To set up your PoC for this scenario, begin with [Introduction to Microsoft Entra ID Protection proof-of-concept guidance](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-introduction). Then follow the detailed guidance in this article.

Perform the following steps for real-time risk detection with Microsoft Entra ID Protection:

1. [Configure risk policies](#configure-risk-policies).
2. [Investigate and remediate risks](#investigate-and-remediate-risks).
3. [Monitor and tune policies](#monitor-and-tune-policies).

## Configure risk policies

To [configure and enable risk policies](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies), factor Sign-in risk and User [risk policies](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-policies) in Microsoft Entra Conditional Access. If you enabled legacy risk policies in Microsoft Entra ID Protection, plan to [migrate them to Conditional Access](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies#migrate-to-conditional-access).

1. Set up the following key foundational policies.

   - [User risk policy](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies): Trigger actions such as require a secure password change for high-risk users.
   - [Sign-in risk policy](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies#sign-in-risk-policy-in-conditional-access): Evaluate each sign-in attempt and enforce controls such as multifactor authentication \(MFA\) or block access.
   - [MFA registration policy](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-mfa-policy): Ensure user enrollment in MFA before they become risky.

2. Test policies with nonadmin test users before you fully deploy your solution.
3. Automate your solution with Conditional Access and Microsoft-managed Conditional Access policies. Automation is critical for scaling protection across large environments.
4. Risk signals from Microsoft Entra ID Protection feed into [Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-mfa-strength) and [Microsoft-managed Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/managed-policies). Consider these options for your scenario:

   - Require [MFA](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-azure-mfa) for sign-in risk or secure password reset for user risk [based on risk level](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-risk-based-sspr-mfa).
   - To prevent lockouts, [exclude emergency access accounts](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access).
   - [Apply policies to workload identities](https://learn.microsoft.com/en-us/entra/identity/conditional-access/workload-identity) like service principals.

## Investigate and remediate risks

To [investigate and remediate risks](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-remediate-unblock), use the Microsoft Entra ID Protection dashboards and reports.

1. Review reports for [risky users](https://learn.microsoft.com/en-us/entra/id-protection/concept-risk-reports#risky-users), [risky sign-ins](https://learn.microsoft.com/en-us/entra/id-protection/concept-risk-reports#risky-sign-ins), and [risk detections](https://learn.microsoft.com/en-us/entra/id-protection/concept-risk-reports#risk-detections).
2. To immediately view impact in sign-in logs, use the [Impact analysis of risk-based access policies workbook](https://learn.microsoft.com/en-us/entra/id-protection/workbook-risk-based-policy-impact). It helps you understand your environment before you enable policies that might block your users from signing in, require MFA, or perform a secure password change. It also provides you with a breakdown for the date range of the sign-ins that you select.
3. Begin [initial triage](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk#initial-triage) of your findings. Take manual actions such as dismissing false positives or confirming compromise.
4. Make decisions based on the [investigation and risk remediation framework](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk#investigation-and-risk-remediation-framework).
5. Use [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-graph-api) or APIs for bulk actions.

For deeper analysis, [export risk data](https://learn.microsoft.com/en-us/entra/id-protection/howto-export-risk-data) to security information and event management \(SIEM\) tools such as Microsoft Sentinel or [Log Analytics](https://learn.microsoft.com/en-us/entra/id-protection/howto-export-risk-data#log-analytics).

## Monitor and tune policies

Monitor the impact of policies using these features:

1. Use the [Impact analysis of risk-based access policies workbook](https://learn.microsoft.com/en-us/entra/id-protection/workbook-risk-based-policy-impact) for trend analysis.
2. To simulate policy effects, enable [report-only mode in Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only).
3. To manage user risk and risk detections, configure automated [Microsoft Entra ID Protection notifications](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-notifications), such as the users at risk detected email or weekly digest email.
4. To reduce false positives and improve the accuracy of Microsoft Entra ID Protection risk calculations for a specific tenant, configure named locations such as VPN IP ranges.

## Next steps

- [Introduction to Microsoft Entra ID Protection proof-of-concept guidance](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-introduction)
- Use real-time risk detection to grant access to protected resources
- [Master risk analysis for effective remediation](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-analyze)
- [Bring identity risk-related telemetry into security investigations](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-investigate)
- [Allow users to self-remediate identity risk for enterprise-managed resources](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-remediate)
