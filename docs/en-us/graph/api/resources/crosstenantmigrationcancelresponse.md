<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationcancelresponse?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# crossTenantMigrationCancelResponse resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains cancellation request response details from a request to cancel a CrossTenantMigrationJob.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| status | String | The cancellation request status |
| message | String | The customer facing description of the cancellation request |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantMigrationCancelResponse",
  "status": "String",
  "message": "String"
}
```
