<!-- Source: https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-protection-scenarios -->
<!-- Sitemap-Last-Modified: 2025-10-03 -->

# Microsoft Security Copilot scenarios in Microsoft Entra ID Protection

Microsoft Security Copilot enhances Microsoft Entra ID Protection capabilities by providing AI-powered insights for identity risk investigation and remediation. This article describes how to use Microsoft Security Copilot with Microsoft Entra ID Protection to streamline identity risk management and improve your organization's security posture. Using this feature requires a tenant with Microsoft Security Copilot enabled.

## Microsoft Entra ID Protection scenarios supported by Microsoft Security Copilot

Security Copilot is integrated into the Microsoft Entra admin center and works seamlessly with Microsoft Entra ID Protection features. The following list provides an overview of the scenarios supported by Security Copilot:

| Scenario | Role\(s\) | License | Tenant |
| --- | --- | --- | --- |
| [Risky users](#risky-users) | [Identity Governance Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#identity-governance-administrator) | [Microsoft Entra ID P2 license](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection#license-requirements) | Any |
| [Application risk](#application-risk) | [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)  <br>[Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) | Workload Identity Premium or [Microsoft Entra ID P2 license](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection#license-requirements) | Any with Risky Service Principal prompts |

### Risky users

Microsoft Entra ID Protection applies the capabilities of Security Copilot to [summarize a user's risk level](https://learn.microsoft.com/en-us/entra/security-copilot/entra-risky-user-summarization), provide insights relevant to the incident at hand, and provide recommendations for rapid mitigation. Identity risk investigation is a crucial step to defend an organization. Security Copilot helps reduce the time to resolution by providing IT admins and security operations center \(SOC\) analysts the right context to investigate and remediate identity risk and identity-based incidents. Risky user summarization provides admins and responders quick access to the most critical information in context to aid their investigation.

You can add your own prompts in the Copilot window for the following use cases;

- [List or Identify Users Based on Risk](https://learn.microsoft.com/en-us/entra/security-copilot/entra-risky-user-summarization#list-or-identify-users-based-on-risk)
- [User-Specific Risk Information](https://learn.microsoft.com/en-us/entra/security-copilot/entra-risky-user-summarization#user-specific-risk-information)
- [User Risk History](https://learn.microsoft.com/en-us/entra/security-copilot/entra-risky-user-summarization#user-risk-history)

![Screenshot that shows the ID Protection risky user summarization details.](https://learn.microsoft.com/en-us/entra/security-copilot/media/copilot-entra-risky-user-summarization/risky-user-details.png)

### Application risk

Identity administrators and security analysts can use Microsoft Security Copilot to quickly assess the risk level of applications from workload identities. By using natural language queries, you can easily discover the granted permissions, unused apps in your tenant, and the risk level of applications. This allows admins to take appropriate actions to mitigate risks and ensure the security of your organization's applications.

Refer to the prompts and examples in [Assess application risks using Microsoft Security Copilot in Microsoft Entra](https://learn.microsoft.com/en-us/entra/security-copilot/entra-investigate-risky-apps) to learn how to use Microsoft Security Copilot to assess application risk for the following use-cases;

- [Explore Microsoft Entra risky service principals](https://learn.microsoft.com/en-us/entra/security-copilot/entra-investigate-risky-apps#explore-microsoft-entra-risky-service-principals)
- [Explore Microsoft Entra service principals](https://learn.microsoft.com/en-us/entra/security-copilot/entra-investigate-risky-apps#explore-microsoft-entra-service-principals)
- [Explore Microsoft Entra applications](https://learn.microsoft.com/en-us/entra/security-copilot/entra-investigate-risky-apps#explore-microsoft-entra-applications)
- [View the permissions granted on a Microsoft Entra service principal](https://learn.microsoft.com/en-us/entra/security-copilot/entra-investigate-risky-apps#explore-microsoft-entra-risky-service-principals)
- [Explore unused Microsoft Entra applications](https://learn.microsoft.com/en-us/entra/security-copilot/entra-investigate-risky-apps#explore-unused-microsoft-entra-applications)
- [Explore Microsoft Entra Applications outside my tenant](https://learn.microsoft.com/en-us/entra/security-copilot/entra-investigate-risky-apps#explore-microsoft-entra-applications-outside-my-tenant)

## See also

- [Get started with Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/get-started-security-copilot)
- [Respond to identity threats using risky user summarization](https://learn.microsoft.com/en-us/entra/security-copilot/entra-risky-user-summarization)
- [Assess application risks using Security Copilot in Microsoft Entra](https://learn.microsoft.com/en-us/entra/security-copilot/entra-investigate-risky-apps)
- [Microsoft Security Copilot experiences](https://learn.microsoft.com/en-us/copilot/security/experiences-security-copilot)
