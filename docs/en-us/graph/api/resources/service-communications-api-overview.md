<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/service-communications-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-13 -->

# Working with service communications API in Microsoft Graph

The service communications API provides service health and message center posts pertaining to the Microsoft cloud services subscribed by your tenant. You can get current and historical health data of a Microsoft service \(for example, the Exchange Online service is down\). You can check the service health to determine if an issue is tracked and a resolution is in progress before calling support or spending time troubleshooting. Message center posts let you keep track of upcoming changes, including new features, updates, and other important announcements \(for example, Exchange Online is getting a new feature\).

## Authorization

Microsoft Graph enables applications get authorized access to health and change communications about a Microsoft cloud service subscribed by a tenant. With the appropriate delegated or application [permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#service-communications-permissions), your app can access the communications data on behalf of a signed-in user, or without any signed-in user in the tenant. Both delegated and application types of these permissions are granted by only an administrator.

For more information about access tokens, app registration, and delegated and application permissions, see [Authentication and authorization basics](https://learn.microsoft.com/en-us/graph/auth/auth-concepts).

### Access service communications API on behalf of signed-in user

Delegated permissions are needed to access the service communications API on behalf of a signed-in user. Customer-facing canvas applications, such as the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage) \(accessible only to admin roles\), can call the service communications API to get the service health and service announcements data for the signed-in user's tenant, *on behalf of the signed-in user*. Users can find out whether their subscribed servies are healthy or have issues. They can also learn about any current service issues affecting their tenants.

#### Role-based access control for delegation access

Service communications API also apply the role-based access control \(RBAC\) to identify whether the signed-in user who is on-behalf has required Microsoft Entra role. The signed-in user who is on-behalf of must have at least one of the admin roles.

For more information about the Microsoft Entra administrator roles, see:

- [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles)
- [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json)
- [Roles in Microsoft 365, including Microsoft Entra ID, service-specific and cross-service roles](https://learn.microsoft.com/en-us/azure/active-directory/roles/concept-understand-roles#how-azure-ad-roles-are-different-from-other-microsoft-365-roles)

### Access service communications API without user

Application permissions are needed to access the service communications API without a signed-in user. Applications that run as backend services, such as monitoring or alert services, can call the service communications API with their own identity and not on behalf of a user. These backend services can build custom monitoring/alert pipelines and call the service communications API to get service health and service announcements data.

## Common use cases and required permissions

| Use cases | API requests | Required permissions | Supported permission types |
| :--- | :--- | :--- | :--- |
| List health overviews for tenant | [List healthOverviews](https://learn.microsoft.com/en-us/graph/api/serviceannouncement-list-healthoverviews?view=graph-rest-1.0&preserve-view=true) | *ServiceHealth.Read.All* | Delegated and application |
| Get specific service health information for tenant | [Get serviceHealth](https://learn.microsoft.com/en-us/graph/api/servicehealth-get?view=graph-rest-1.0&preserve-view=true) | *ServiceHealth.Read.All* | Delegated and application |
| List all service issues for tenant | [List issues](https://learn.microsoft.com/en-us/graph/api/serviceannouncement-list-issues?view=graph-rest-1.0&preserve-view=true) | *ServiceHealth.Read.All* | Delegated and application |
| Get a specific service issue for tenant | [Get issue](https://learn.microsoft.com/en-us/graph/api/servicehealthissue-get?view=graph-rest-1.0&preserve-view=true) | *ServiceHealth.Read.All* | Delegated and application |
| Get a post-incident review report for tenant | [Get incident report](https://learn.microsoft.com/en-us/graph/api/servicehealthissue-incidentreport?view=graph-rest-1.0&preserve-view=true) | *ServiceHealth.Read.All* | Delegated and application |
| List all service messages for tenant | [List messages](https://learn.microsoft.com/en-us/graph/api/serviceannouncement-list-messages?view=graph-rest-1.0&preserve-view=true) | *ServiceMessage.Read.All* | Delegated and application |
| Get a specific service message for tenant | [Get message](https://learn.microsoft.com/en-us/graph/api/serviceupdatemessage-get?view=graph-rest-1.0&preserve-view=true) | *ServiceMessage.Read.All* | Delegated and application |
| Update service message status for signed in user | For a list of status operations, see [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0&preserve-view=true). | *ServiceMessageViewpoint.Write* | Delegated |

## Microsoft Graph national cloud availability

The service communications API is available on Microsoft Graph national clouds. You can get service health and communications data for your national clouds tenants.

| National clouds | API URL \(partial\) |
| :--- | :--- |
| Microsoft Graph global service | `https://graph.microsoft.com/v1.0/admin/serviceAnnouncement/\|` |
| Microsoft Graph for US Government L4 \(GccHigh\) | https://graph.microsoft.us/v1.0/admin/serviceAnnouncement/ |
| Microsoft Graph for US Government L5 \(DoD\) | https://dod-graph.microsoft.us/v1.0/admin/serviceAnnouncement/ |
| Microsoft Graph China operated by 21Vianet | https://microsoftgraph.chinacloudapi.cn/v1.0/admin/serviceAnnouncement/ |

For details about national cloud availability, see [Microsoft Graph national clouds](https://learn.microsoft.com/en-us/graph/deployments).

## Service communications limits

To guarantee the service performance, the service communications API has throttling limits for the requests per tenant per application. For details about the limits, see [throttling limits for the service communications service](https://learn.microsoft.com/en-us/graph/throttling#service-communications-service-limits).

## Next steps

The service communications API can open up new ways for you to engage with users. For more information, see the following:

- [Overview for accessing service health and communications in Microsoft Graph](https://learn.microsoft.com/en-us/graph/service-communications-concept-overview)
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
