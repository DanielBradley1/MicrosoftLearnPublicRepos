<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/origintenantinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# originTenantInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the identifiers of a tenant and a user that are used to identify them in the origin tenant when a user is invited as a guest.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| originTenantId | String | The identifier of the tenant where the user account was originally provisioned. |
| originUserId | String | The identifier of the user in the origin tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.originTenantInfo",
  "originTenantId": "String",
  "originUserId": "String"
}
```
