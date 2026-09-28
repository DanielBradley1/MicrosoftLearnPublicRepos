<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/browser-edge-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# Use the Edge API in Microsoft Graph

The Edge API in Microsoft Graph lets apps manage administrator tasks for organizations. With proper authorization, an app can get access to an organization's browser site lists for Internet Explorer \(IE\) mode that reside in the cloud, allowing administrators to manage the same data available in the [Microsoft 365 admin center](https://admin.microsoft.com/). After configuring the appropriate permissions, your app can create browser site lists, add browser sites and shared cookies, and publish the site lists for Microsoft Edge to download.

## Authorization

To call the Edge API in Microsoft Graph, your app needs to acquire an access token. For details about access tokens, see [Get access tokens to call Microsoft Graph](https://learn.microsoft.com/en-us/graph/auth/). Your app also needs the appropriate permissions. For more information, see [Browser management permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#browser-management-permissions).

## Common use cases

The Edge API provides methods and actions that support some administrator's tasks in the Microsoft 365 admin center. The following describes common use cases of the API that manages site lists for IE mode.

| Use cases | REST resources | See also |
| :--- | :--- | :--- |
| Create, read, update, delete, and publish browser site lists. | [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) | [Methods of browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0#methods) |
| Modify the browser sites on a browser site list. | [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) | [Methods of browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0#methods) |
| Modify the browser shared cookies on a browser site list. | [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) | [Methods of browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0#methods) |

## Next steps

The Edge API in Microsoft Graph can streamline the way you manage your site lists for IE mode. To learn more:

- Drill down on the methods and properties of the resources most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
