<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppOperation resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an operation applied against an app registration.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAppOperations](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappoperation-list?view=graph-rest-1.0) | [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) collection | List properties and relationships of the [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) objects. |
| [Get managedAppOperation](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappoperation-get?view=graph-rest-1.0) | [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) | Read properties and relationships of the [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) object. |
| [Create managedAppOperation](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappoperation-create?view=graph-rest-1.0) | [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) | Create a new [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) object. |
| [Delete managedAppOperation](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappoperation-delete?view=graph-rest-1.0) | None | Deletes a [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0). |
| [Update managedAppOperation](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappoperation-update?view=graph-rest-1.0) | [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) | Update the properties of a [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The operation name. |
| lastModifiedDateTime | DateTimeOffset | The last time the app operation was modified. |
| state | String | The current state of the operation |
| id | String | Key of the entity. |
| version | String | Version of the entity. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppOperation",
  "displayName": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "state": "String",
  "id": "String (identifier)",
  "version": "String"
}
```
