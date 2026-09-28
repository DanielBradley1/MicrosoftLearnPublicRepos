<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/m365-monitoring-api-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-03 -->

# Working with Microsoft 365 monitoring APIs in Microsoft Graph

The Microsoft 365 monitoring API provides the telemetry data to monitor the health of various Microsoft services within a Microsoft 365 subscription for your organization. This capability began with Exchange Online and expanded to other Microsoft services such as Microsoft Teams and Microsoft 365 Apps. Microsoft 365 monitoring increases observability and minimizes downtime by delivering near real-time user telemetry data.

## Authorization

Microsoft Graph enables applications to get authorized access to telemetry data about a Microsoft service subscribed by a tenant. With the appropriate delegated or application [permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#serviceactivity-exchangereadall), your app can access the telemetry data on behalf of a signed-in user, or without any signed-in user in the tenant. Only an administrator can grant both delegated and application types of these permissions.

For more information about access tokens, app registration, and delegated and application permissions, see [Authentication and authorization basics](https://learn.microsoft.com/en-us/graph/auth/auth-concepts).

### Access Microsoft 365 monitoring APIs on behalf of a signed-in user

Delegated permissions are needed to access the Microsoft 365 monitoring API on behalf of a signed-in user. Customer-facing canvas applications, such as the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage) \(accessible only to admin roles\), can call the Microsoft 365 monitoring API to get the telemetry data for the signed-in user's tenant, *on behalf of the signed-in user*.

#### Role-based access control for delegation access

The Microsoft 365 monitoring API applies role-based access control \(RBAC\) to identify whether the signed-in user who is on-behalf of has a required Microsoft Entra role. The signed-in user who is on-behalf of must have at least one of the admin roles.

For more information about the Microsoft Entra administrator roles, see:

- [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles)
- [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference)
- [Roles in Microsoft 365, including Microsoft Entra ID, service-specific roles, and cross-service roles](https://learn.microsoft.com/en-us/azure/active-directory/roles/concept-understand-roles#how-azure-ad-roles-are-different-from-other-microsoft-365-roles)

### Access Microsoft 365 monitoring API without a user

Application permissions are needed to access the Microsoft 365 monitoring API without a signed-in user. Applications that run as backend services, such as monitoring or alert services, can call the Microsoft 365 monitoring API with their own identity and not on behalf of a user. Backend services can use the Microsoft 365 monitoring API to retrieve telemetry data, which enables them to build custom dashboards that analyze trends, monitor performance, and detect anomalies in real-time.

## Availability in national clouds

The Microsoft 365 monitoring API is available in the following Microsoft national cloud deployments. For details, see [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| National clouds | API URL \(partial\) |
| :--- | :--- |
| Microsoft Graph global service | `https://graph.microsoft.com/beta/reports/serviceActivity/\|` |
| Microsoft Graph for US Government L4 \(GccHigh\) | Not supported. |
| Microsoft Graph for US Government L5 \(DoD\) | Not supported. |
| Microsoft Graph China operated by 21Vianet | Not supported. |

## Common use cases

The following table lists common use cases for the Microsoft 365 monitoring APIs.

| Use case | Related content |
| :--- | :--- |
| [Exchange Online monitoring](https://learn.microsoft.com/en-us/graph/api/resources/serviceactivity?view=graph-rest-beta#exchange-online-monitoring) | [Exchange Online monitoring for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-exchange-monitoring) |
| [Microsoft 365 Teams monitoring](https://learn.microsoft.com/en-us/graph/api/resources/serviceactivity?view=graph-rest-beta#microsoft-365-teams-monitoring) | [Microsoft 365 Teams monitoring](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-teams-monitoring) |
| [Microsoft 365 Apps monitoring](https://learn.microsoft.com/en-us/graph/api/resources/serviceactivity?view=graph-rest-beta#microsoft-365-apps-monitoring) | [Microsoft 365 Apps monitoring](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-apps-monitoring) |
| [Microsoft Entra](https://learn.microsoft.com/en-us/graph/api/resources/serviceactivity?view=graph-rest-beta#microsoft-entra) |  |

## Next steps

The Microsoft 365 monitoring API can open up new ways for you to engage with users.

- To learn more about the Microsoft 365 monitoring APIs available, see the [serviceActivity](https://learn.microsoft.com/en-us/graph/api/resources/serviceactivity?view=graph-rest-beta) resource.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
