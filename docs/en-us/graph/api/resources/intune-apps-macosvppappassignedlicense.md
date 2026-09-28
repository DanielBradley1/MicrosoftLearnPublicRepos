<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macOsVppAppAssignedLicense resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MacOS Volume Purchase Program license assignment. This class does not support Create, Delete, or Update.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOsVppAppAssignedLicenses](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppappassignedlicense-list?view=graph-rest-beta) | [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta) collection | List properties and relationships of the [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta) objects. |
| [Get macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppappassignedlicense-get?view=graph-rest-beta) | [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta) | Read properties and relationships of the [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta) object. |
| [Create macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppappassignedlicense-create?view=graph-rest-beta) | [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta) | Create a new [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta) object. |
| [Delete macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppappassignedlicense-delete?view=graph-rest-beta) | None | Deletes a [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta). |
| [Update macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppappassignedlicense-update?view=graph-rest-beta) | [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta) | Update the properties of a [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta) object. |

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
  "@odata.type": "#microsoft.graph.macOsVppAppAssignedLicense",
  "id": "String (identifier)",
  "userEmailAddress": "String",
  "userId": "String",
  "userName": "String",
  "userPrincipalName": "String"
}
```
