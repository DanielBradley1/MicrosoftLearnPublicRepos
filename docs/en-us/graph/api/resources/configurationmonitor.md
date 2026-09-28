<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# configurationMonitor resource type

Namespace: microsoft.graph

Represents monitors for tenant or drift monitoring across all workloads supported by Tenant Configuration Management, enabling periodic detection of deviations from the desired configuration state.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/configurationmanagement-list-configurationmonitors?view=graph-rest-1.0) | [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) collection | Get a list of the [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/configurationmanagement-post-configurationmonitors?view=graph-rest-1.0) | [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) | Create a new [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) object that runs periodically in the background at a scheduled frequency. |
| [Get](https://learn.microsoft.com/en-us/graph/api/configurationmonitor-get?view=graph-rest-1.0) | [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) | Get the properties and relationships of a [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/configurationmonitor-update?view=graph-rest-1.0) | [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) | Update the properties of a [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) object, including the monitor name, description, and baseline. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/configurationmonitor-delete?view=graph-rest-1.0) | None | Delete a [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) object permanently. |
| [Get configuration baseline](https://learn.microsoft.com/en-us/graph/api/configurationbaseline-get?view=graph-rest-1.0) | [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) collection | Read the properties and relationships of a [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) object that is attached to a specific monitor. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user, app, or device that created the monitor.  <br>  <br>Requires `$select` to retrieve. Supports `$filter` \(`eq`\). |
| createdDateTime | DateTimeOffset | The date and time when the monitor was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `ge`, `le`\) and `$orderby`. |
| description | String | User-friendly description of the monitor given by the user.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `startsWith`\) and `$orderby`. |
| displayName | String | User-friendly name given by the user to the monitor.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `startsWith`\) and `$orderby`. |
| id | String | Globally unique identifier \(GUID\) for the monitor. System-generated. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderby`. |
| inactivationReason | String | The reason for the monitor's inactivation.  <br>  <br>Requires `$select` to retrieve. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user, app, or device that last modified the monitor.  <br>  <br>Requires `$select` to retrieve. Supports `$filter` \(`eq`\). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the monitor was last modified. If no modifications are made to the monitor, it's the same as **createdDateTime**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `ge`, `le`\) and `$orderby`. |
| mode | monitorMode | Monitor mode in which the monitor runs. The possible values are: `monitorOnly`, `unknownFutureValue`. The default value is `monitorOnly`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |
| monitorRunFrequencyInHours | Int32 | Frequency at which the monitor runs. The default frequency is six hours. Regardless of when you create or update a monitor, it gets triggered within the next 6 hours. Currently, monitors are picked up at fixed times: 6 AM, 12 PM, 6 PM, and 12 AM \(all in GMT\). For example, if you create a monitor at 9 AM, it gets triggered around 12 PM. If you update a monitor at 4 PM, it gets triggered around 6 PM. |
| parameters | [openComplexDictionaryType](https://learn.microsoft.com/en-us/graph/api/resources/opencomplexdictionarytype?view=graph-rest-1.0) | Key-value pairs that contain parameter values which might be used in the baseline.  <br>  <br>Requires `$select` to retrieve. |
| status | monitorStatus | Status of the monitor. The possible values are: `active`, `inactive`, `unknownFutureValue`. The default value is `active`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderby`. |
| tenantId | String | Globally unique identifier \(GUID\) of the tenant for which the monitor runs. Fetched automatically by the system.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| baseline | [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) | A relationship that contains details of at least one resource and one property associated with the resource to be monitored. Returned only with `$select`. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.configurationMonitor",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "inactivationReason": "String",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "mode": "String",
  "monitorRunFrequencyInHours": "Int32",
  "parameters": {"@odata.type": "microsoft.graph.openComplexDictionaryType"},
  "status": "String",
  "tenantId": "String"
}
```
