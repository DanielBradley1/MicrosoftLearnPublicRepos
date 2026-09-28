<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppStatus resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents app protection and configuration status for the organization.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAppStatuses](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappstatus-list?view=graph-rest-1.0) | [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0) collection | List properties and relationships of the [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0) objects. |
| [Get managedAppStatus](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappstatus-get?view=graph-rest-1.0) | [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0) | Read properties and relationships of the [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Friendly name of the status report. |
| id | String | Key of the entity. |
| version | String | Version of the entity. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppStatus",
  "displayName": "String",
  "id": "String (identifier)",
  "version": "String"
}
```
