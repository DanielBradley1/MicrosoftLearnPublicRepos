<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# resourceOperation resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Describes the resourceOperation resource \(entity\) of the Microsoft Graph API \(REST\), which supports Intune workflows related to role-based access control \(RBAC\).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List resourceOperations](https://learn.microsoft.com/en-us/graph/api/intune-rbac-resourceoperation-list?view=graph-rest-1.0) | [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) collection | List properties and relationships of the [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) objects. |
| [Get resourceOperation](https://learn.microsoft.com/en-us/graph/api/intune-rbac-resourceoperation-get?view=graph-rest-1.0) | [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) | Read properties and relationships of the [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) object. |
| [Create resourceOperation](https://learn.microsoft.com/en-us/graph/api/intune-rbac-resourceoperation-create?view=graph-rest-1.0) | [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) | Create a new [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) object. |
| [Delete resourceOperation](https://learn.microsoft.com/en-us/graph/api/intune-rbac-resourceoperation-delete?view=graph-rest-1.0) | None | Deletes a [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0). |
| [Update resourceOperation](https://learn.microsoft.com/en-us/graph/api/intune-rbac-resourceoperation-update?view=graph-rest-1.0) | [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) | Update the properties of a [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the Resource Operation. Read-only, automatically generated. |
| resourceName | String | Name of the Resource this operation is performed on. |
| actionName | String | Type of action this operation is going to perform. The actionName should be concise and limited to as few words as possible. |
| description | String | Description of the resource operation. The description is used in mouse-over text for the operation when shown in the Azure Portal. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.resourceOperation",
  "id": "String (identifier)",
  "resourceName": "String",
  "actionName": "String",
  "description": "String"
}
```
