<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-15 -->

# accessPackage resource type

Namespace: microsoft.graph

In [Microsoft Entra Entitlement Management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package defines the collections of resource roles and the policies for how one or more users can get access to those resources.

Each access package is referenced by a single access package catalog, and has links to the resources from that catalog via the resource-specific role scopes that define the access the package provides. An access package also links to the access package assignment policies, each of which define who can request or be assigned an access package assignment.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-accesspackages?view=graph-rest-1.0) | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) collection | Retrieve a list of **accesspackage** objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-accesspackages?view=graph-rest-1.0) | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) | Create a new **accesspackage** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accesspackage-get?view=graph-rest-1.0) | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) | Read properties and relationships of an **accesspackage** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/accesspackage-update?view=graph-rest-1.0) | None | Update the properties of an **accesspackage** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/accesspackage-delete?view=graph-rest-1.0) | None | Delete an **accesspackage**. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/accesspackage-filterbycurrentuser?view=graph-rest-1.0) | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) collection | Retrieve the list of **accessPackage** objects filtered on the signed-in user. |
| [Get applicable policy requirements](https://learn.microsoft.com/en-us/graph/api/accesspackage-getapplicablepolicyrequirements?view=graph-rest-1.0) | [accessPackageAssignmentRequestRequirements](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestrequirements?view=graph-rest-1.0) collection | Retrieve a list of **accessPackageAssignmentRequestRequirement** objects with request requirements. |
| **Incompatible access packages** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/accesspackage-list-incompatibleaccesspackages?view=graph-rest-1.0) | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) collection | Retrieve a list of the incompatible **accesspackage** objects for this access package. |
| [Add to](https://learn.microsoft.com/en-us/graph/api/accesspackage-post-incompatibleaccesspackage?view=graph-rest-1.0) | None | Add a link to indicate another **accesspackage** is incompatible with a specified access package. |
| [Remove from](https://learn.microsoft.com/en-us/graph/api/accesspackage-delete-incompatibleaccesspackage?view=graph-rest-1.0) | None | Remove a link that indicated an **accesspackage** was incompatible. |
| [List incompatible with](https://learn.microsoft.com/en-us/graph/api/accesspackage-list-accesspackagesincompatiblewith?view=graph-rest-1.0) | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) collection | Retrieve a list of the **accesspackage** objects that list this access package as incompatible. |
| **Incompatible groups** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/accesspackage-list-incompatiblegroups?view=graph-rest-1.0) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) collection | Retrieve a list of the incompatible **group** objects for this access package. |
| [Add group to](https://learn.microsoft.com/en-us/graph/api/accesspackage-post-incompatiblegroup?view=graph-rest-1.0) | None | Add a link to indicate membership of a **group** is incompatible with a specified access package. |
| [Remove group from](https://learn.microsoft.com/en-us/graph/api/accesspackage-delete-incompatiblegroup?view=graph-rest-1.0) | None | Remove a link that indicated a **group** membership was incompatible. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| description | String | The description of the access package. |
| displayName | String | Required. The display name of the access package. Supports $filter \(`eq`, `contains`\). |
| id | String | Read-only. |
| isHidden | Boolean | Indicates whether the access package is hidden from the requestor. |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackagesIncompatibleWith | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) collection | The access packages that are incompatible with this package. Read-only. |
| assignmentPolicies | [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) collection | Read-only. Nullable. Supports `$expand`. |
| catalog | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) | Required when creating the access package. Read-only. Nullable. |
| incompatibleAccessPackages | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) collection | The access packages whose assigned users are ineligible to be assigned this access package. |
| incompatibleGroups | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) collection | The groups whose members are ineligible to be assigned this access package. |
| resourceRoleScopes | [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0) collection | The resource roles and scopes in this access package. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackage",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String", 
  "id": "String (identifier)",
  "isHidden": "Boolean",
  "modifiedDateTime": "String (timestamp)"
}
```
