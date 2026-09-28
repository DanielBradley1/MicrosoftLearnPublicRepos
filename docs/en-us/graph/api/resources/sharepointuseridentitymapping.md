<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-20 -->

# sharePointUserIdentityMapping resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a cross-organization identity mapping for a user during a tenant-to-tenant \(cross-tenant\) migration. This resource defines the relationship between a source user in the originating organization and its corresponding target user in the destination organization. It includes source and target user identities, migration metadata, and user type information.

Inherits from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/sharepointuseridentitymapping-get?view=graph-rest-beta) | [sharePointUserIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) | Retrieve a specific [user identity mapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) by the source user principal name \(UPN\). |
| [Update](https://learn.microsoft.com/en-us/graph/api/sharepointuseridentitymapping-update?view=graph-rest-beta) | [sharePointUserIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) | Perform delta patch operations on [user identity mappings](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) for cross-organization migration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deleted | [deleted](https://learn.microsoft.com/en-us/graph/api/resources/deleted?view=graph-rest-beta) | Indicates that an identity mapping was deleted successfully. Inherited from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta). |
| id | String | Unique identifier for the user identity mapping. Base64-encoded String. Generated automatically. Inherited from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta). |
| sourceOrganizationId | Guid | The unique identifier of the source organization in the migration. Inherited from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta). |
| sourceUserIdentity | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) | The identity information of the source user in the originating organization. Contains the source user's principal name. |
| targetUserIdentity | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) | The identity information of the target user in the destination organization. Contains the target user's principal name. |
| targetUserMigrationData | [sharePointIdentityMappingUserMigrationData](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymappingusermigrationdata?view=graph-rest-beta) | Additional migration-specific data for the target user. Contains the email address for the user in the destination organization. |
| userType | sharePointIdentityMappingUserType | Indicates the type of user. The possible values are: `none`, `regularUser`, `adminUser`, `guestUser`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointUserIdentityMapping",
  "deleted": {"@odata.type": "microsoft.graph.deleted"},
  "id": "String (identifier)",
  "sourceOrganizationId": "Guid",
  "sourceUserIdentity": {"@odata.type": "microsoft.graph.userIdentity"},
  "targetUserIdentity": {"@odata.type": "microsoft.graph.userIdentity"},
  "targetUserMigrationData": {"@odata.type": "microsoft.graph.sharePointIdentityMappingUserMigrationData"},
  "userType": "String"
}
```
