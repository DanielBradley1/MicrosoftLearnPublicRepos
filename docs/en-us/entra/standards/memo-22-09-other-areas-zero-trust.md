<!-- Source: https://learn.microsoft.com/en-us/entra/standards/memo-22-09-other-areas-zero-trust -->
<!-- Sitemap-Last-Modified: 2025-02-10 -->

# Other areas of Zero Trust addressed in Memo 22-09

The other articles in this guidance address the identity pillar of Zero Trust principles, as described in the US Office of Management and Budget \(OMB\) [Memo 22-09, Memorandum for the Heads of Executive Departments and Agencies](https://bidenwhitehouse.archives.gov/wp-content/uploads/2022/01/M-22-09.pdf). This article covers Zero Trust maturity model areas beyond the identity pillar, and it addresses the following themes:

- Visibility
- Analytics
- Automation and orchestration
- Governance

## Visibility

It's important to monitor your Microsoft Entra tenant. Assume a breach mindset and meet compliance standards in memorandum 22-09 and 21-31, Improving the Federal Governments Investigative and Remediation Capabilities Related to Cybersecurity Incidents. Three primary log types are used for security analysis and ingestion:

- **Azure audit logs** to monitor operational activities of the directory, such as creating, deleting, updating objects like users or groups

  - Use also to make changes to Microsoft Entra configurations, like modifications to a Conditional Access policy
  - See, [Audit logs in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-audit-logs)

- **Provisioning logs** have information about objects synchronized from Microsoft Entra ID to applications like Service Now with Microsoft Identity Manager

  - See, [Provisioning logs in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs)

- **Microsoft Entra sign-in logs** to monitor sign-in activities associated with users, applications, and service principals.

  - Sign-in logs have categories for differentiation
  - Interactive sign-ins show successful and failed sign-ins, policies applied, and other metadata
  - Non-interactive user sign-ins show no interaction during sign-in: clients signing in on behalf of the user, such as mobile applications or email clients
  - Service principal sign-ins show service principal or application sign-in: services or applications accessing services, applications, or the Microsoft Entra directory through the REST API
  - Managed identities for Azure resource sign-in: Azure resources or applications accessing Azure resources, such as a web application service authenticating to an Azure SQL back end.
  - See, [Sign-in logs in Microsoft Entra ID \(preview\)](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins)

In Microsoft Entra ID Free tenants, log entries are stored for seven days. Tenants with a Microsoft Entra ID P1 or P2 license retain log entries for 30 days.

Ensure a security information and event management \(SIEM\) tool ingests logs. Use sign-in and audit events to correlate with application, infrastructure, data, device, and network logs.

We recommend you integrate Microsoft Entra logs with Microsoft Sentinel. Configure a connector to ingest Microsoft Entra tenant logs.

Learn more:

- [What is Microsoft Sentinel?](https://learn.microsoft.com/en-us/azure/sentinel/overview)
- [Connect Microsoft Entra ID to Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-azure-active-directory)

For the Microsoft Entra tenant, you can configure the diagnostic settings to send the data to an Azure Storage account, Azure Event Hubs, or a Log Analytics workspace. Use these storage options to integrate other SIEM tools to collect data.

Learn more:

- [What is Microsoft Entra monitoring?](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/overview-monitoring-health)
- [Microsoft Entra reporting and monitoring deployment dependencies](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/plan-monitoring-and-reporting)

## Analytics

You can use analytics in the following tools to aggregate information from Microsoft Entra ID and show trends in your security posture in comparison to your baseline. You can also use analytics to assess and look for patterns or threats across Microsoft Entra ID.

- **Microsoft Entra ID Protection** analyzes sign-ins and other telemetry sources for risky behavior

  - ID Protection assigns a risk score to sign-in events
  - Prevent sign-ins, or force a step-up authentication, to access a resource or application based on risk score
  - See, [What is ID Protection?](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)

- **Microsoft Entra usage and insights reports** have information similar to Azure Sentinel workbooks, including applications with highest usage or sign-in trends.

  - Use reports to understand aggregate trends that might indicate an attack or other events
  - See, [Usage and insights in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-usage-insights-report)

- **Microsoft Sentinel** analyze information from Microsoft Entra ID:

  - Microsoft Sentinel User and Entity Behavior Analytics \(UEBA\) delivers intelligence on potential threats from user, host, IP address, and application entities.
  - Use analytics rule templates to hunt for threats and alerts in your Microsoft Entra logs. Your security or operation analyst can triage and remediate threats.
  - Microsoft Sentinel workbooks help visualize Microsoft Entra data sources. See sign-ins by country/region or applications.
  - See, [Commonly used Microsoft Sentinel workbooks](https://learn.microsoft.com/en-us/azure/sentinel/top-workbooks)
  - See, [Visualize collected data](https://learn.microsoft.com/en-us/azure/sentinel/get-visibility)
  - See, [Identify advanced threats with UEBA in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/identify-threats-with-entity-behavior-analytics)

## Automation and orchestration

Automation in Zero Trust helps remediate alerts due to threats or security changes. In Microsoft Entra ID, automation integrations help clarify actions to improve your security posture. Automation is based on information received from monitoring and analytics.

Use Microsoft Graph API REST calls to access Microsoft Entra ID programmatically. This access requires a Microsoft Entra identity with authorizations and scope. With the Graph API, integrate other tools.

We recommend you set up an Azure function or an Azure logic app to use a system-assigned managed identity. The logic app or function has steps or code to automate actions. Assign permissions to the managed identity to grant the service principal directory permissions to perform actions. Grant managed identities minimum rights.

Learn more: [What are managed identities for Azure resources?](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)

Another automation integration point is Microsoft Graph PowerShell modules. Use Microsoft Graph PowerShell to perform common tasks or configurations in Microsoft Entra ID, or incorporate into Azure functions or Azure Automation runbooks.

## Governance

Document your processes for operating the Microsoft Entra environment. Use Microsoft Entra features for governance functionality applied to scopes in Microsoft Entra ID.

Learn more:

- [Microsoft Entra ID Governance operations reference guide](https://learn.microsoft.com/en-us/entra/architecture/ops-guide-govern)
- [Microsoft Entra security operations guide](https://learn.microsoft.com/en-us/entra/architecture/security-operations-introduction)
- [What is Microsoft Entra ID Governance?](https://learn.microsoft.com/en-us/entra/id-governance/identity-governance-overview)
- [Meet authorization requirements of memorandum 22-09](https://learn.microsoft.com/en-us/entra/standards/memo-22-09-authorization).

## Next steps

- [Meet identity requirements of memorandum 22-09 with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/standards/memo-22-09-meet-identity-requirements)
- [Enterprise-wide identity management system](https://learn.microsoft.com/en-us/entra/standards/memo-22-09-enterprise-wide-identity-management-system)
- [Meet multifactor authentication requirements of memorandum 22-09](https://learn.microsoft.com/en-us/entra/standards/memo-22-09-multi-factor-authentication)
- [Meet authorization requirements of memorandum 22-09](https://learn.microsoft.com/en-us/entra/standards/memo-22-09-authorization)
- [Securing identity with Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/deploy/identity)
