<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatusraw?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppStatusRaw resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an un-typed status report about organizations app protection and configuration.

Inherits from [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAppStatusRaws](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappstatusraw-list?view=graph-rest-1.0) | [managedAppStatusRaw](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatusraw?view=graph-rest-1.0) collection | List properties and relationships of the [managedAppStatusRaw](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatusraw?view=graph-rest-1.0) objects. |
| [Get managedAppStatusRaw](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappstatusraw-get?view=graph-rest-1.0) | [managedAppStatusRaw](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatusraw?view=graph-rest-1.0) | Read properties and relationships of the [managedAppStatusRaw](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatusraw?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Friendly name of the status report. Inherited from [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0) |
| id | String | Key of the entity. Inherited from [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0) |
| version | String | Version of the entity. Inherited from [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0) |
| content | [Json](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-json?view=graph-rest-1.0) | Status report content. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppStatusRaw",
  "displayName": "String",
  "id": "String (identifier)",
  "version": "String",
  "content": {
    "@odata.type": "microsoft.graph.Json"
  }
}
```
