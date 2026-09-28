<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-20 -->

# sharePointGroupIdentityMapping resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a cross-organization identity mapping for a group during a tenant-to-tenant \(cross-tenant\) migration. This resource defines the relationship between a source group in the originating organization and its corresponding target group in the destination organization. It includes source and target group identities, migration metadata, and group type information.

Inherits from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/sharepointgroupidentitymapping-get?view=graph-rest-beta) | [sharePointGroupIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) | Retrieve a specific cross-organization [group identity mapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) based on the Microsoft Entra ID object ID of the source group. |
| [Update](https://learn.microsoft.com/en-us/graph/api/sharepointgroupidentitymapping-update?view=graph-rest-beta) | [sharePointGroupIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) | Perform delta patch operations on [group identity mappings](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) for cross-organization migration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deleted | [deleted](https://learn.microsoft.com/en-us/graph/api/resources/deleted?view=graph-rest-beta) | Indicates that an identity mapping was deleted successfully. Inherited from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta). |
| groupType | sharePointIdentityMappingGroupType | Indicates the type of group. The possible values are: `none`, `regularGroup`, `m365Group`, `unknownFutureValue`. |
| id | String | Unique identifier for the group identity mapping. Base64-encoded String. Generated automatically. Inherited from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta). |
| sourceGroupIdentity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The identity information of the source group in the originating organization. Contains the ID of the source group. |
| sourceOrganizationId | Guid | The unique identifier of the source organization in the migration. Inherited from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta). |
| targetGroupIdentity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The identity information of the target group in the destination organization. Contains the ID of the target group. |
| targetGroupMigrationData | [sharePointIdentityMappingGroupMigrationData](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymappinggroupmigrationdata?view=graph-rest-beta) | Additional migration-specific data for the target group. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointGroupIdentityMapping",
  "deleted": {"@odata.type": "microsoft.graph.deleted"},
  "groupType": "String",
  "id": "String (identifier)",
  "sourceGroupIdentity": {"@odata.type": "microsoft.graph.identity"},
  "sourceOrganizationId": "Guid",
  "targetGroupIdentity": {"@odata.type": "microsoft.graph.identity"},
  "targetGroupMigrationData": {"@odata.type": "microsoft.graph.sharePointIdentityMappingGroupMigrationData"}
}
```
