<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-getbysourcesiteurl?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# sharePointMigrationTask: getBySourceSiteUrl

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that was previously created for a regular site, using the source site URL. The returned **sharePointMigrationTask** object includes the source and target site URLs, migration status, optional timestamps \(**startedDateTime** and **finishedDateTime**\), and error details about issues during processing.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SharePointCrossTenantMigration.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SharePointCrossTenantMigration.Read.All | Not available. |

## HTTP request

```http
GET /solutions/sharePoint/migrations/crossOrganizationMigrationTasks/getBySourceSiteUrl(sourceSiteUrl='{sourceSiteUrl}')
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| sourceSiteUrl | String | Source site URL. |

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. You can use `$select` to choose specific properties such as **id**, **status**, or **startedDateTime**. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationMigrationTasks/getBySourceSiteUrl(sourceSiteUrl='https://contoso.sharepoint.com/sites/IT')
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sharePointMigrationTask = await client.api('/solutions/sharePoint/migrations/crossOrganizationMigrationTasks/getBySourceSiteUrl(sourceSiteUrl='https://contoso.sharepoint.com/sites/IT')')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "3ed6d46d-13a3-4995-b6ea-a74a20b1fac0",
  "status": "completed",
  "startedDateTime": "2025-7-18T09:08:04.451Z",
  "lastUpdatedDateTime": "2025-7-18T09:13:46.028Z",
  "finishedDateTime": "2025-7-18T09:13:46.028Z",
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointSiteMigrationTaskParameters",
    "targetOrganizationId": "3ef4e46d-13a3-4895-b6ea-a74a20hu728h",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceSiteUrl": "https://contoso.sharepoint.com/sites/IT",
    "targetSiteUrl": "https://fabrico.sharepoint.com/sites/IT"
  }
}
```
