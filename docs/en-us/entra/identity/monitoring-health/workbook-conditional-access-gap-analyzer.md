<!-- Source: https://learn.microsoft.com/en-us/entra/identity/monitoring-health/workbook-conditional-access-gap-analyzer -->
<!-- Sitemap-Last-Modified: 2024-11-04 -->

# Conditional Access gap analyzer workbook

In Microsoft Entra ID, you can protect access to your resources by configuring Conditional Access policies. As an IT administrator, you want to ensure that your Conditional Access policies work as expected to ensure that your resources are properly protected. With the Conditional Access gap analyzer workbook, you can detect gaps in your Conditional Access implementation.

This article provides you with an overview of the **Conditional Access gap analyzer** workbook.

## Prerequisites

To use Azure Workbooks for Microsoft Entra ID, you need:

- A Microsoft Entra tenant with a [Premium P1 license](https://learn.microsoft.com/en-us/entra/fundamentals/get-started-premium)
- A Log Analytics workspace *and* access to that workspace
- The appropriate roles for Azure Monitor *and* Microsoft Entra ID

### Log Analytics workspace

You must create a [Log Analytics workspace](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/quick-create-workspace) *before* you can use Microsoft Entra Workbooks. several factors determine access to Log Analytics workspaces. You need the right roles for the workspace *and* the resources sending the data.

For more information, see [Manage access to Log Analytics workspaces](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/manage-access).

### Azure Monitor roles

Azure Monitor provides [two built-in roles](https://learn.microsoft.com/en-us/azure/azure-monitor/roles-permissions-security#monitoring-reader) for viewing monitoring data and editing monitoring settings. Azure role-based access control \(RBAC\) also provides two Log Analytics built-in roles that grant similar access.

- **View**:

  - Monitoring Reader
  - Log Analytics Reader

- **View and modify settings**:

  - Monitoring Contributor
  - Log Analytics Contributor

### Microsoft Entra roles

Read only access allows you to view Microsoft Entra ID log data inside a workbook, query data from Log Analytics, or read logs in the Microsoft Entra admin center. Update access adds the ability to create and edit diagnostic settings to send Microsoft Entra data to a Log Analytics workspace.

- **Read**:

  - Reports Reader
  - Security Reader
  - Global Reader

- **Update**:

  - Security Administrator

For more information on Microsoft Entra built-in roles, see [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

For more information on the Log Analytics RBAC roles, see [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#log-analytics-contributor).

## Description

![Workbook category](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/workbook-conditional-access-gap-analyzer/workbook-category.png)

As an IT administrator, you want to make sure that only the right people can access your resources. Microsoft Entra Conditional Access helps you to accomplish this goal.

The Conditional Access gap analyzer workbook helps you to verify that your Conditional Access policies work as expected.

**This workbook:**

- Highlights user sign-ins that have no Conditional Access policies applied to them.
- Allows you to ensure that there are no users, applications, or locations that were unintentionally excluded from Conditional Access policies.

## How to access the workbook

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) using the appropriate combination of roles.
2. Browse to **Entra ID** > **Monitoring & health** > **Workbooks**.
3. Select the **Conditional Access Gap Analyzer** workbook from the **Conditional Access** section.

## Workbook sections

The workbook has four sections:

- Users signing in using legacy authentication
- Number of sign-ins by applications that aren't impacted by Conditional Access policies
- High risk sign-in events bypassing Conditional Access policies
- Number of sign-ins by location that weren't affected by Conditional Access policies

![Conditional Access coverage by location](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/workbook-conditional-access-gap-analyzer/conditianal-access-by-location.png)

Each of these trends offers a breakdown of sign-ins to the user level, so that you can see which users per scenario are bypassing Conditional Access.

## Filters

This workbook supports setting a time range filter.

![Time range filter](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/workbook-conditional-access-gap-analyzer/time-range.png)

## Best practices

Use this workbook to ensure that your tenant is configured to the following Conditional Access best practices:

- Block all legacy authentication sign-ins
- Apply at least one Conditional Access Policy to every application
- Block all high risk sign-ins
- Block sign-ins from untrusted locations

## Related content

- [How to use the identity workbooks](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-use-workbooks)
- [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
