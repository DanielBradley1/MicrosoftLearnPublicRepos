<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-20 -->

# sharePointIdentityMapping resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base identity mapping for cross-organization \(tenant-to-tenant\) migration scenarios. This abstract type serves as the parent for specific identity mapping types for users and groups.

Base type of [sharePointUserIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) and [sharePointGroupIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deleted | [deleted](https://learn.microsoft.com/en-us/graph/api/resources/deleted?view=graph-rest-beta) | Indicates that an identity mapping was deleted successfully. |
| id | String | Unique identifier for the identity mapping. Base64-encoded String. Generated automatically. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| sourceOrganizationId | Guid | The unique identifier of the source organization in the migration. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointIdentityMapping",
  "deleted": {"@odata.type": "microsoft.graph.deleted"},
  "id": "String (identifier)",
  "sourceOrganizationId": "Guid"
}
```
