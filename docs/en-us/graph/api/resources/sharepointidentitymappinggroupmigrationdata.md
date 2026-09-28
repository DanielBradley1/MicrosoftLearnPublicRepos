<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymappinggroupmigrationdata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# sharePointIdentityMappingGroupMigrationData resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains additional migration-related data for a group identity mapping in a cross-organization \(tenant-to-tenant\) migration.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mailNickname | String | The email alias \(mail nickname\) for the target group in the destination organization. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointIdentityMappingGroupMigrationData",
  "mailNickname": "String"
}
```
