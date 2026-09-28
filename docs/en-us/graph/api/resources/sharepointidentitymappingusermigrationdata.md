<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymappingusermigrationdata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# sharePointIdentityMappingUserMigrationData resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains additional migration-related data for a user identity mapping in a cross-organization \(tenant-to-tenant\) migration.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| email | String | The target email address for the user in the destination organization. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointIdentityMappingUserMigrationData",
  "email": "String"
}
```
