<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-cloudappdiscovery-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-19 -->

# Use the Microsoft Defender for Cloud apps API in Microsoft Graph \(preview\)

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Use the Microsoft Defender for Cloud apps API in Microsoft Graph to get data and insights across the discovered SaaS apps ecosystem. The discovered cloud app API in Microsoft Graph provides an efficient and reliable way to query information about discovered apps. This makes it easier for you to analyze the risks associated with those apps.

The discovered cloud app API enables you to do the following:

- Programmatically analyze the risk profile of all discovered apps.
- Programmatically filter discovered apps by using multiple parameters and filter options.
- Search asynchronously with support for automation, which is accessible to both users and applications.

The discovered cloud app API is defined in the OData subnamespace `microsoft.graph.security`.

## Discovered cloud app API use cases

Customers can get all the data available on the discovered apps page via the Microsoft Graph API. The following are some key user scenarios the API supports.

### List all users who use a specific risky SaaS app

Identify and list all users who access a particular SaaS application that's deemed risky. Make informed decisions about SaaS apps by gaining comprehensive insights about risky users and taking proactive steps to safeguard the data of your organization. For more information, see [List users](https://learn.microsoft.com/en-us/graph/api/security-discoveredcloudappdetail-list-users?view=graph-rest-beta).

### List all apps that access a specific domain

Discover the complete list of SaaS applications that access a specific domain. Gain clarity and control over your digital ecosystem effortlessly by keeping tabs on apps, users, and devices that access risky domains. For more information, see [cloudAppDiscoveryReport: aggregatedAppsDetails](https://learn.microsoft.com/en-us/graph/api/security-cloudappdiscoveryreport-aggregatedappsdetails?view=graph-rest-beta).

### Access the cloud app catalog information for a specific discovered SaaS app

Access detailed information from the cloud app catalog for a specific discovered SaaS application. Get access to specific insights into app usage and security risks, enabling effective monitoring and management. Enhance the security and compliance posture of your organization by using comprehensive data about app compliance. For more information, see [Get discoveredCloudAppInfo](https://learn.microsoft.com/en-us/graph/api/security-discoveredcloudappinfo-get?view=graph-rest-beta).

## Next steps

Use the Microsoft Graph discovered cloud app API to get data and insights from the discovered SaaS apps ecosystem. To learn more:

- Explore the resources and methods that are most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
