<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcscopedpermission?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# cloudPcScopedPermission resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a scoped permission and related scope IDs.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| permission | String | The operations allowed on scoped resources for the authenticated user. Example permission is `Microsoft.CloudPC/ProvisioningPolicies/Create`. |
| scopeIds | String collection | The scope IDs of corresponding permission. Currently, it's Intune scope tag ID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcScopedPermission",
  "permission": "String",
  "scopeIds": ["String"]
}
```
