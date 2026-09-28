<!-- Source: https://learn.microsoft.com/en-us/entra/security-copilot/conditional-access-agent-optimization-logs-metrics -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# View logs and metrics for the Conditional Access Optimization Agent

The Conditional Access Optimization Agent helps organizations improve their security posture by automatically analyzing sign-in patterns and suggesting policy optimizations. This Microsoft Security Copilot agent identifies unprotected users and applications, recommends policy improvements, and helps consolidate redundant policies.

To ensure transparency and maintain control over automated recommendations, Microsoft Entra ID provides comprehensive logging and metrics for all agent activities. This article explains how to monitor agent performance, review audit logs, and understand the metrics that help you measure the agent's effect on your security environment.

## Prerequisites

- To view the Microsoft Entra audit logs, you need at least the [Reports reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#reports-reader) role.
- [Global Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-reader) and [Security Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-reader) roles can view the agent and any suggestions, but can't take any actions.
- [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator), [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator), and [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator) roles can view the agent and take action on the suggestions.

  - For more information on roles for the Conditional Access Optimization Agent, see [Assign Security Copilot access](https://learn.microsoft.com/en-us/copilot/security/authentication#assign-security-copilot-access)

- Review [Privacy and data security in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/privacy-data-security)

## Agent summary

The **Agent summary** at the top of the Conditional Access Optimization Agent page provides a quick summary of what the agent discovered in the last 30 days. The total number of [security compute units \(SCU\)](https://learn.microsoft.com/en-us/copilot/security/manage-usage) consumed by the agent is also provided.

[![Screenshot of the agent summary tile.](https://learn.microsoft.com/en-us/entra/security-copilot/media/conditional-access-agent-optimization-logs-metrics/agent-summary-tile.png)](https://learn.microsoft.com/en-us/entra/security-copilot/media/conditional-access-agent-optimization-logs-metrics/agent-summary-tile.png#lightbox)

- **Unprotected users discovered**: The number of users identified by the agent and protected by a policy suggested by the agent.
- **Unprotected apps discovered**: The number of applications identified by the agent and protected by a policy suggested by the agent.
- **Sign-ins protected**: The number of sign-ins protected by a policy suggested by the agent.
- **Security compute units consumed**: The total number of SCUs consumed by the agent in the last 30 days.

The values in the agent summary reflect the activity after suggestions are applied. If you run the agent and don't apply any suggestions, the values in the agent summary won't change.

## Insights dashboard \(Preview\)

The Conditional Access Optimization Agent includes an insights dashboard that provides data visualizations of the improvements made by applying agent suggestions. The dashboard is a great way to share progress with your leadership to demonstrate the value of Zero Trust investments without building custom reports.

[![Screenshot of the insights dashboard.](https://learn.microsoft.com/en-us/entra/security-copilot/media/conditional-access-agent-optimization-logs-metrics/insights-dashboard.png)](https://learn.microsoft.com/en-us/entra/security-copilot/media/conditional-access-agent-optimization-logs-metrics/insights-dashboard.png#lightbox)

The insights dashboard provides the following metrics:

- **Objects with improved coverage**: Users, applications, or agent identities with critical policy gaps identified by the agent and are now covered by at least one new control in the past 30 days.
- **Objects missing coverage**: Users, applications, or agent identities currently missing coverage from one or more critical policies.

The dashboard provides links to drill down into specific metrics and an option to download the report as a CSV.

## Audit logs

Activity associated with Security Copilot agents in Microsoft Entra appears in the Microsoft Entra audit logs and the Security Copilot audit logs in Microsoft Purview. Each service provides different information about the agent's activity.

The Microsoft Purview logs include tenant-level administrative actions and user interactions within the Security Copilot platform. For more information, see [Access the Security Copilot audit logs](https://learn.microsoft.com/en-us/copilot/security/audit-log).

The Microsoft Entra audit logs include changes made by an agent to Microsoft Entra resources, such as Conditional Access policies. Policies created or modified by the agent are tagged with **Conditional Access Optimization Agent** in the Conditional Access policies pane.

[![Screenshot of Agent summary tile at the top of the agent page.](https://learn.microsoft.com/en-us/entra/security-copilot/media/conditional-access-agent-optimization-logs-metrics/created-by-conditional-access-optimization-agent.png)](https://learn.microsoft.com/en-us/entra/security-copilot/media/conditional-access-agent-optimization-logs-metrics/created-by-conditional-access-optimization-agent-expanded.png#lightbox)

In the **Audit logs** the **Initiated by \(actor\)** field show the name of the user who started the agent. To quickly see agent activity, filter to **Service: Conditional Access**.

[![Screenshot of audit logs filtered to Conditional Access.](https://learn.microsoft.com/en-us/entra/security-copilot/media/conditional-access-agent-optimization-logs-metrics/audit-logs.png)](https://learn.microsoft.com/en-us/entra/security-copilot/media/conditional-access-agent-optimization-logs-metrics/audit-logs.png#lightbox)
