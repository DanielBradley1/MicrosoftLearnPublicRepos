<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-remediate -->
<!-- Sitemap-Last-Modified: 2025-11-02 -->

# Microsoft Entra ID Protection scenario: User identity risk self-remediation for enterprise-managed resources

The proof-of-concept \(PoC\) guidance in this series of articles helps you to learn, deploy, and test Microsoft Entra ID Protection to detect, investigate, and remediate identity-based risks.

An overview of the guidance begins with [Introduction to Microsoft Entra ID Protection proof-of-concept guidance](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-introduction).

Detailed guidance continues with these scenarios:

- [Use real-time risk detection to grant access to protected resources](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-detect)
- [Master risk analysis for effective remediation](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-analyze)
- [Bring identity risk-related telemetry into security investigations](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-investigate)

This article helps administrators to identify and remediate identity risks for users accessing enterprise-managed resources, including Microsoft 365. Use real-time and offline risk detections to evaluate sign-ins and user behavior. Apply automated responses such as multifactor authentication \(MFA\), password resets, or block access based on risk levels. Risk-based conditional access policies that scale across large environments enforce these protections.

Configure the following features for user self-remediation of identity risk for enterprise-managed resources with Microsoft Entra ID Protection:

- [Configure risky sign-in self-remediation](#configure-risky-sign-in-self-remediation)
- [Configure password reset protection and self-service](#configure-password-reset-protection-and-self-service)
- [Enforce Conditional Access](#enforce-conditional-access)
- [Configure visibility into account health](#configure-visibility-into-account-health)
- [Integrate with Microsoft Defender for incident correlation and investigation](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview)

## Configure risky sign-in self-remediation

Prompt Microsoft 365 users that you enroll in Microsoft Entra ID Protection to complete multifactor authentication \(MFA\) upon [risky sign-in detection](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-remediate-unblock).

## Configure password reset protection and self-service

Configure password protection features, especially in large Microsoft 365 environments where password hygiene and autonomy are critical.

1. Configure [password protection policies](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-password-ban-bad) that block weak or banned passwords.
2. To allow users to securely recover access with multiple authentication methods, configure [self-service password reset \(SSPR\)](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies#user-risk-policy-in-conditional-access).
3. [Move to phishing-resistant passwordless authentication.](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-plan-prerequisites-phishing-resistant-passwordless-authentication)

## Enforce Conditional Access

Configure Conditional Access policies for users with dynamic enforcement based on:

1. [Sign-in risk](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-risks) such as from an unfamiliar location or device.
2. [User risk](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-risks#user-risk-detections) such as leaked credentials or suspicious behavior.

Require users to verify their identity or restrict access to sensitive apps until after risk mitigation.

## Configure visibility into account health

Configure user alerts and notifications for the following scenarios:

1. Suspicious activity on their account.
2. Required actions to maintain access such as reauthentication or device compliance.

## Next steps

- [Introduction to Microsoft Entra ID Protection proof-of-concept guidance](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-introduction)
- [Use real-time risk detection to grant access to protected resources](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-detect)
- [Master risk analysis for effective remediation](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-analyze)
- [Bring identity risk-related telemetry into security investigations](https://learn.microsoft.com/en-us/entra/architecture/id-protection-guide-investigate)
- Allow users to self-remediate identity risk for enterprise-managed resources
