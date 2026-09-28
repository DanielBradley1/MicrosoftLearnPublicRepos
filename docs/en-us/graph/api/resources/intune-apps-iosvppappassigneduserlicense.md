<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosVppAppAssignedUserLicense resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

iOS Volume Purchase Program user license assignment. This class does not support Create, Delete, or Update.

Inherits from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosVppAppAssignedUserLicenses](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneduserlicense-list?view=graph-rest-beta) | [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) collection | List properties and relationships of the [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) objects. |
| [Get iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneduserlicense-get?view=graph-rest-beta) | [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) | Read properties and relationships of the [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) object. |
| [Create iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneduserlicense-create?view=graph-rest-beta) | [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) | Create a new [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) object. |
| [Delete iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneduserlicense-delete?view=graph-rest-beta) | None | Deletes a [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta). |
| [Update iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneduserlicense-update?view=graph-rest-beta) | [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) | Update the properties of a [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userEmailAddress | String | The user email address. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userId | String | The user ID. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userName | String | The user name. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userPrincipalName | String | The user principal name. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosVppAppAssignedUserLicense",
  "id": "String (identifier)",
  "userEmailAddress": "String",
  "userId": "String",
  "userName": "String",
  "userPrincipalName": "String"
}
```
