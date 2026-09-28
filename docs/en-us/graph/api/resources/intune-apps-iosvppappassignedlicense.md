<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosVppAppAssignedLicense resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

iOS Volume Purchase Program license assignment. This class does not support Create, Delete, or Update.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosVppAppAssignedLicenses](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassignedlicense-list?view=graph-rest-beta) | [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) collection | List properties and relationships of the [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) objects. |
| [Get iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassignedlicense-get?view=graph-rest-beta) | [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) | Read properties and relationships of the [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) object. |
| [Create iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassignedlicense-create?view=graph-rest-beta) | [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) | Create a new [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) object. |
| [Delete iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassignedlicense-delete?view=graph-rest-beta) | None | Deletes a [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta). |
| [Update iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassignedlicense-update?view=graph-rest-beta) | [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) | Update the properties of a [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. |
| userEmailAddress | String | The user email address. |
| userId | String | The user ID. |
| userName | String | The user name. |
| userPrincipalName | String | The user principal name. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosVppAppAssignedLicense",
  "id": "String (identifier)",
  "userEmailAddress": "String",
  "userId": "String",
  "userName": "String",
  "userPrincipalName": "String"
}
```
