<!-- Source: https://learn.microsoft.com/en-us/graph/deployments -->
<!-- Sitemap-Last-Modified: 2025-01-30 -->

# Microsoft Graph national cloud deployments

This article provides information about the different Microsoft Graph national cloud deployments and the capabilities that are available to developers within each.

In addition to a global network of datacenters, Microsoft cloud services are available in two separate national clouds. These national cloud versions are physical and logical network-isolated instances of Microsoft enterprise cloud services that are confined within the geographic borders of specific countries/regions and operated by local personnel.

Current national clouds include:

- Microsoft Cloud for US Government
- Microsoft Azure and Microsoft 365 operated by 21Vianet in China

Each national cloud environment is unique and different than the Microsoft global environment. It's important to be aware of some of these key differences when you develop applications for national cloud environments; for example, registering applications, acquiring tokens, and calling the Microsoft Graph API can be different.

Note

[Microsoft Graph Data Connect](https://learn.microsoft.com/en-us/graph/data-connect-concept-overview) does not support any of the national cloud deployments.

<iframe src="https://www.youtube-nocookie.com/embed/R_3E0IVypRM" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## App registration and token service root endpoints

Before calling the Microsoft Graph APIs, you should first register your application and acquire a token. The following table lists the base URLs for the endpoints to register your application and acquire tokens for each national cloud.

| National cloud | Azure portal endpoint | Microsoft Entra ID endpoint |
| --- | --- | --- |
| Azure global service | `https://portal.azure.com` | `https://login.microsoftonline.com` |
| Azure US Government | `https://portal.azure.us` | `https://login.microsoftonline.us` |
| Azure China operated by 21Vianet | `https://portal.azure.cn` | `https://login.chinacloudapi.cn` |

To learn more about access tokens and Microsoft Graph, see [authentication basics](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). For authentication scenarios, see [Microsoft identity platform authentication basics](https://learn.microsoft.com/en-us/azure/active-directory/develop/authentication-scenarios).

## Microsoft Graph and Graph Explorer service root endpoints

The following table shows the service root endpoints for Microsoft Graph and [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) for each national cloud.

| National Cloud | Microsoft Graph | Graph Explorer |
| --- | --- | --- |
| Microsoft Graph global service | `https://graph.microsoft.com` | [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer) |
| Microsoft Graph for US Government L4 \(GCC High\) | `https://graph.microsoft.us` | Not supported. |
| Microsoft Graph for US Government L5 \(DOD\) | `https://dod-graph.microsoft.us` | Not supported. |
| Microsoft Graph China operated by 21Vianet | `https://microsoftgraph.chinacloudapi.cn` | Not supported. |

Important

For a software application working in US Government context, use the following root endpoints for the Azure portal and Microsoft Graph respectively.

- If you're working in a Microsoft 365 GCC environment, continue using the worldwide endpoints: `https://portal.azure.com` and `https://graph.microsoft.com`.
- If you're working in a Microsoft 365 GCC High environment, use `https://portal.azure.us` and `https://graph.microsoft.us`.
- If you're working in a Microsoft 365 DoD environment, use `https://portal.azure.us` and `https://dod-graph.microsoft.us`.

Note

Apps can only access organizational data through the national cloud endpoints. This means that apps can only access data in tenants that are registered in the specific national cloud. Apps that are trying to access consumer data associated with Microsoft personal accounts through Microsoft Graph should use the global service `https://graph.microsoft.com`. Access tokens acquired for a national cloud deployment are not interchangeable with those acquired for the global service or any other national cloud.

## Service API support in national clouds

For details about API support for Microsoft Graph services in national clouds, see the [API beta reference](https://learn.microsoft.com/en-us/graph/api/overview?view=graph-rest-beta&preserve-view=true) and [API v1.0 reference](https://learn.microsoft.com/en-us/graph/api/overview?view=graph-rest-1.0&preserve-view=true).

Important

Certain services and features that are in specific regions of the global service might not be available in all national clouds. To find out what services are available, see [Product Availability by Region](https://azure.microsoft.com/explore/global-infrastructure/products-by-region/table).

## Related content

To learn more about national clouds, see the following articles:

- [Microsoft National Clouds](https://www.microsoft.com/TrustCenter/CloudServices/NationalCloud)
- [Microsoft 365 for US Government](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government)
- [Microsoft 365 operated by 21Vianet](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet)
- [Azure Government](https://azure.microsoft.com/explore/global-infrastructure/government/)
- [Azure China 21Vianet](https://learn.microsoft.com/en-us/azure/china/)

Explore samples for authenticating and working with Azure and Microsoft 365 in National cloud deployments:

- [Access national cloud deployments with the Microsoft Graph SDKs](https://learn.microsoft.com/en-us/graph/sdks/national-clouds)
- [Work with Azure through Microsoft Graph for US Government](https://github.com/SteveWinward/Azure-Samples/blob/master/AAD/SampleAadToken_AzureForGovernment.ps1)
- [Connect to US Government O365 environments \(GCC, GCC High and GCC DoD\) using Microsoft Graph PowerShell](https://github.com/microsoft/Federal-Business-Applications/tree/main/demos/powershell-gov-samples#microsoft-graph-powershell)
