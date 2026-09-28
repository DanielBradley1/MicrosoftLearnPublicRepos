<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/securely-integrating-with-external-systems -->
<!-- Sitemap-Last-Modified: 2026-05-27 -->

# Securely integrating Employee Self-Service with external systems

This article explains how Employee Self-Service authenticates with external HR and IT systems, why user-delegated access is the recommended model for employee scenarios, and what Microsoft supports.

Important

Employee Self-Service is designed around user-delegated access for all employee-facing scenarios. If your organization chooses to use system accounts for employee-facing operations instead, that configuration is outside what Microsoft supports. Microsoft isn't able to help troubleshoot or debug issues that arise from unsupported configurations.

## Overview

Employee Self-Service is built around the principle that every request to an external system should carry the employee's own delegated credentials. When an integration authenticates with a shared system credential instead of the employee's own identity, a single compromised credential can expose every record that account's role can reach, turning a localized issue into an enterprise-wide incident. Employee Self-Service avoids this outcome by design: every request to an external system carries the employee's own delegated credentials.

Employee Self-Service authenticates using the OAuth 2.0 authorization code flow. The employee signs in through Microsoft Entra, and the resulting access token carries only the scopes their role requires. Employee Self-Service doesn't cache or elevate tokens beyond the role requirement, so the external system sees a real user identity on every call and can apply its own role-based access control accordingly.

User-delegated calls also inherit Conditional Access policies, MFA challenges, sign-in risk evaluations, and session controls from the employee's Microsoft 365 sign-in. System accounts bypass all of these controls by design. Once provisioned, every call is implicitly trusted regardless of device posture, location, or risk.

Important

Your organization owns its authentication and authorization configuration end to end. You're responsible for evaluating your deployment's security posture, applying controls that align with your organizational policies, and mitigating any risks associated with your chosen access patterns.

### Who needs to be involved

- **HR system admin** \(Workday or ServiceNow\): registers the OAuth client and configures user-facing security policies in the external system
- **M365 tenant admin**: approves the app registration and consent grant in Microsoft Entra
- **Identity admin**: verifies that Conditional Access policies, MFA requirements, and user consent settings align with organizational security policy

For system-specific setup steps, see the connector documentation linked in [Related content](#related-content).

## How Employee Self-Service authenticates

### Scope verification

Employee Self-Service doesn't request broad administrative scopes. The OAuth scope set is limited to what the employee's role requires. You can verify the exact scopes granted to the Employee Self-Service application through the enterprise applications consent view in Microsoft Entra.

### Audit trail

Every action is tied to the employee's real identity. The following table shows where audit records appear:

| Event type | System that records it | What to look for |
| --- | --- | --- |
| Data read/write on behalf of the employee | External system \(Workday audit trail, ServiceNow sys\_audit / transaction log\) | Action attributed to the employee's external-system identity |
| Authentication and token issuance | Microsoft Entra sign-in logs | Sign-in event, Conditional Access evaluation result, MFA status |
| Consent grant or revocation | Microsoft Entra audit logs | Application consent events for the Employee Self-Service app registration |

Consult your external system's audit log documentation for retention policies and access controls. Microsoft Entra sign-in logs are retained for 30 days by default \(up to 365 days with Microsoft Entra ID P1/P2\).

## When to use each access pattern

Warning

Using a system account for employee actions is a form of privileged access and is a well-established anti-pattern for user-facing scenarios. A compromised credential exposes every record its role can reach. Even when privileged access is necessary, it should follow rigorous controls: time-bounded sessions, just-in-time provisioning, and continuous monitoring. For employee-facing operations, user-delegated access avoids the need for these controls entirely.

### User-delegated access for employee-facing scenarios

User-delegated access is the only supported model for employee-facing scenarios in Employee Self-Service. This covers self-service HR and IT workflows, personal data access, and any operation where audit traceability matters.

**Workday examples**

| Scenario | Recommended access |
| --- | --- |
| View payslip | User-delegated |
| Update personal details | User-delegated |
| Submit leave request | User-delegated |
| View time-off balance | User-delegated |
| Request time off | User-delegated |
| View benefits elections | User-delegated |
| Update emergency contacts | User-delegated |
| View compensation details | User-delegated |

**ServiceNow examples**

| Scenario | Recommended access |
| --- | --- |
| Create or update tickets | User-delegated |
| View personal requests | User-delegated |
| Interact with HR or IT workflows | User-delegated |
| Check ticket status | User-delegated |
| Add comments or attachments to a case | User-delegated |
| View knowledge articles \(user-scoped\) | User-delegated |
| Submit onboarding or offboarding requests | User-delegated |

### System-level access for non-employee-specific operations

System accounts are appropriate for a narrow set of read-only, non-employee-specific backend operations:

- Synchronizing organizational data \(org charts, cost centers\)
- Fetching catalog or reference data \(service catalogs, knowledge articles\)
- Running scheduled backend jobs \(data reconciliation, provisioning\)

These operations are typically ingestion scenarios where the consuming service applies its own role-based access control \(RBAC\) layer on top of the imported data, providing another security boundary beyond the source system's access controls.

These identities remain useful when applied intentionally to the scenarios in this section. They aren't recommended as an alternative for employee-facing operations.

## Summary

Employee Self-Service recommends authenticating as the employee on every call to an external system. This configuration ensures that the external system's native access control enforces authorization, audit logs reflect the real user, and Conditional Access policies apply to every session.

## Related content

- [Employee Self-Service overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/overview)
- [Integrate Workday with your Employee Self-Service deployment](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday)
- [Integrate ServiceNow with your Employee Self-Service deployment](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/servicenow)
