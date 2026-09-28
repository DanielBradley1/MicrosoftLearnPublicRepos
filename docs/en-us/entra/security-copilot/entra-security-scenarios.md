<!-- Source: https://learn.microsoft.com/en-us/entra/security-copilot/entra-security-scenarios -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# Microsoft Security Copilot scenarios in Microsoft Entra overview

Microsoft Security Copilot is a powerful tool that can help you manage and secure your Microsoft Entra identity environment. This article outlines the different capabilities in Microsoft Entra that you can investigate using natural language queries. These capabilities are available across different Microsoft Entra products to enhance your identity protection efforts. To use Security Copilot in Microsoft Entra, ensure that you have a tenant with Security Copilot enabled.

## Microsoft Security Copilot integration with Microsoft Entra

Security Copilot is a part of the Microsoft Entra admin center, and you can use it to create your own prompts. Security Copilot is launched from a globally available button in the menu bar. Choose from a set of starter prompts that appear at the top of the Security Copilot window or enter your own in the prompt bar to get started. Suggested prompts can appear after a response, which are predefined prompts that Security Copilot selects based on the prior response.

![Screenshot that shows Security Copilot in the Microsoft Entra admin center.](https://learn.microsoft.com/en-us/entra/security-copilot/media/copilot-security-entra/security-copilot-entra-admin-center.png)

### Data exploration using Microsoft Security Copilot \(preview\)

Microsoft Security Copilot supports data exploration when prompts return datasets with more than 10 items. This feature is in preview and available for select Microsoft Entra scenarios. From the Copilot chat response, select **Open list** to access a comprehensive data grid. This allows you to explore large datasets with complete and accurate results, enabling more efficient decision-making. Each data grid displays the underlying Microsoft Graph URL, helping you verify query accuracy and build confidence in the results.

Note

This functionality is currently in preview and limited to simple, single-step prompts \(for example *"Provide a list of users in the Sales department"*\). Tasks that require multi-step prompting and cross scenario functionality \(for example *"Which risky apps have high privileged permissions?"*\) are not currently supported by this feature. Copilot will still provide chat-based summaries for all prompts.

[![Screenshot that shows Data Exploration in Security Copilot for Microsoft Entra.](https://learn.microsoft.com/en-us/entra/security-copilot/media/copilot-security-entra/data-explorer.png)](https://learn.microsoft.com/en-us/entra/security-copilot/media/copilot-security-entra/data-explorer.png#lightbox)

## Security Copilot scenarios in Microsoft Entra

There's a large selection of Security Copilot scenarios available in Microsoft Entra. Use the following table to learn more about each scenario by product area, their use cases, license and role requirements.

| Microsoft Entra product | Security Copilot scenarios | Data Exploration Enabled |
| --- | --- | :---: |
| **Microsoft Entra ID** | [Tenants](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#tenants)  <br>[Users](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#users)  <br>[Groups](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#groups)  <br>[Domains](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#domains)  <br>[Licenses](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#licenses)  <br>[Sign-in logs](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#sign-in-logs)  <br>[Audit logs](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#audit-logs)  <br>[Provisioning logs](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#provisioning-logs)  <br>[Recommendations](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#recommendations)  <br>[Health monitoring alerts](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#health-monitoring-alerts)  <br>[Service Level Agreement](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#service-level-agreement)  <br>[Roles and administrators](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#roles-and-administrators)  <br>[Devices](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#devices)  <br>[Conditional Access](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#conditional-access)  <br>[Authentication](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios#authentication) | ![Tenants data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Users data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Groups data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Domains data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Licenses data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-no.png)  <br>![Sign in logs data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Audit logs data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Provisioning logs data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-no.png)  <br>![Recommendations data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Health monitoring alerts data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Service Level Agreement data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Role and administrators data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Devices data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Conditional access data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Authentication data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png) |
| **Microsoft Entra ID Protection** | [Risky users](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-protection-scenarios#risky-users)  <br>[Application risk](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-protection-scenarios#application-risk) | ![Risky users data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Application risk data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png) |
| **Microsoft Entra ID Governance** | [Access reviews](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-governance-scenarios#access-reviews)  <br>[Entitlement management](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-governance-scenarios#entitlement-management)  <br>[Privileged Identity Management \(PIM\)](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-governance-scenarios#privileged-identity-management-pim)  <br>[PIM write actions](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-governance-scenarios#privileged-identity-management-pim-write-actions)  <br>[Lifecycle workflows](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-governance-scenarios#lifecycle-workflows) | ![Access reviews data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Entitlement management data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Privileged Identity Management \(PIM\) data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png)  <br>![Privileged Identity Management \(PIM\) write actions data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-no.png)  <br>![Lifecycle workflows data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png) |
| **Microsoft Entra Internet Access**  <br>**Microsoft Entra Private Access** | [Global Secure Access](https://learn.microsoft.com/en-us/entra/security-copilot/entra-internet-access-private-access-scenarios#global-secure-access) | ![Global Secure Access data exploration enabled](https://learn.microsoft.com/en-us/entra/media/common/applies-to-yes.png) |

## Microsoft Entra ID scenarios

Microsoft Entra ID is the foundational production of Microsoft Entra, and provides the essential identity, authentication, policy, and protection to secure users, devices, apps, and resources. Security Copilot enhances these capabilities across multiple areas:

- **Enterprise user management**: Quickly retrieve user, group, domain and license information
- **Authentication**: Discover enabled authentication methods, registration status, and overall authentication strategy
- **Role based access control \(RBAC\)**: Investigate role assignments within a directory
- **Conditional Access**: Understand and evaluate conditional access policies
- **Device identity**: Explore device details and compliance status

## Microsoft Entra ID Protection scenarios

Microsoft Entra ID Protection focuses on identity risk detection and remediation. Security Copilot provides AI-powered insights for:

- **Risky user investigation**: Summarize user risk levels and provide remediation recommendations
- **Application risk assessment**: Analyze workload identities and application permissions

## Microsoft Entra ID Governance scenarios

Microsoft Entra ID Governance helps you manage identity lifecycle and access governance at scale. Security Copilot enhances these capabilities for:

- **Access reviews**: Analyze access review data and decision patterns
- **Entitlement management**: Manage access packages and connected organizations
- **Privileged Identity Management**: Monitor privileged access and role assignments
- **Lifecycle workflows**: Configure and troubleshoot employee lifecycle automation

## Related content

- [Microsoft Security Copilot scenarios in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-scenarios)
- [Microsoft Security Copilot scenarios in Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-protection-scenarios)
- [Microsoft Security Copilot scenarios in Microsoft Entra ID Governance](https://learn.microsoft.com/en-us/entra/security-copilot/entra-id-governance-scenarios)
- [Get started with Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/get-started-security-copilot)
