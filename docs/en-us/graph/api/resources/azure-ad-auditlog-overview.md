<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azure-ad-auditlog-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# Microsoft Entra audit logs API overview

Namespace: microsoft.graph

Microsoft Entra provides an audit trail of all user and app activity in your tenant to help you track all activities in your tenant and also be compliant. These logs include both app and user sign in activity, as well as changes to the directory.

The availability of these audit logs is governed by the [Microsoft Entra data retention policies](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/reference-reports-data-retention#how-long-does-azure-ad-store-the-data).

## Available audit logs

Note

[Custom security attribute audit logs](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributeaudit) and [provisioning logs](https://learn.microsoft.com/en-us/graph/api/resources/provisioningobjectsummary) are currently available only on the `beta` endpoint.

### Directory audit logs

The [directory audit logs](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-1.0) provide you with access to the history of every task performed in your tenant, either by a user or a service. Amongst others, the provided data enables you to address common scenarios such as:

- Who granted admin group access to a directory user?
- Which users are signing in to a recently acquired app?
- How many passwords resets were made within the directory?

### Sign-ins

The [sign-in logs](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-1.0) help you determine who or what performed the tasks reported by directory audit logs. The logs include interactive user sign-ins, non-interactive user sign-ins, service principal sign-ins, and managed identity sign-ins.

The sign-ins report helps you answer questions like:

- What is the sign in pattern of a user?
- How many users have signed in during the last week?
- What's the status of these sign-ins?

## What can I do with activity reports in Microsoft Graph?

Here are popular requests for working with report data:

| Operation | URL |
| --- | --- |
| GET tenant user activities | [https://graph.microsoft.com/v1.0/auditLogs/directoryAudits](https://developer.microsoft.com/graph/graph-explorer?request=auditLogs/directoryAudits&version=v1.0) |
| GET custom security attribute audit logs | [https://graph.microsoft.com/v1.0/auditLogs/customSecurityAttributeAudits](https://developer.microsoft.com/graph/graph-explorer?request=auditLogs/customSecurityAttributeAudits&version=v1.0) |
| GET tenant sign-ins | [https://graph.microsoft.com/v1.0/auditLogs/signIns](https://developer.microsoft.com/graph/graph-explorer?request=auditLogs/signIns&version=v1.0) |

## License requirements

Activity reports are available for features that you've licensed. If you have a license for a specific feature, you also have access to the reports. For more information about license requirements for the different activity reports, see [Microsoft Entra audit logs: License and role requirements](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-audit-logs#license-and-role-requirements).

## Related content

- [Microsoft Entra audit logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-audit-logs)
