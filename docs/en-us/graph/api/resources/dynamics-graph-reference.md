<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-graph-reference?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-04 -->

# Working with the Dynamics 365 Business Central API in Microsoft Graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

You can use Microsoft Graph to connect and integrate your web service or SaaS solution with Microsoft Dynamics 365 Business Central. With Microsoft Graph, you can build apps that get authorized access to and integrate seamlessly with Microsoft Dynamics 365 Business Central data.

## Authorization

Use the Azure AD v2.0 endpoint to authenticate Dynamics 365 Business Central APIs. All APIs require the `Authorization: Bearer {access-token}` request header. For more information about authorization, see [Get access tokens to call Microsoft Graph](https://learn.microsoft.com/en-us/graph/auth/).

## Common Dynamics 365 Business Central scenarios

The Dynamics 365 Business Central API allows you to read and modify business data through apps that are connected and integrated through a single endpoint. Use the API to, for example, get access to [customer](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-customer?view=graph-rest-beta) and [vendor](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-vendor?view=graph-rest-beta) information, or [view overdue payments](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-agedaccountspayable?view=graph-rest-beta).

## Environment

To enable the Dynamics 365 Business Central API, you must ensure that the **Environment Name** in the Business Central Admin Center is **Production**.

![Business Central Admin Center setup](https://learn.microsoft.com/en-us/graph/beta/images/dynamics-tenant-admin-environment.png?view=graph-rest-beta)

## Next steps

The Dynamics 365 Business Central API can open up new ways for you to engage with users. To learn more, see the following:

- [Dynamics 365 Business Central Overview](https://learn.microsoft.com/en-us/graph/dynamics-business-central-concept-overview)
- Try [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
