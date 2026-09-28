<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# configurationDrift resource type

Namespace: microsoft.graph

Represents the information and properties of a [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0) object. This resource allows admins to get granular details about all active drifts across all existing monitors.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/configurationmanagement-list-configurationdrifts?view=graph-rest-1.0) | [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0) collection | Get a list of the [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/configurationdrift-get?view=graph-rest-1.0) | [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0) | Get the properties and relationships of a [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| baselineResourceDisplayName | String | Resource instance for which the drift is detected.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `startsWith`\) and `$orderby`. |
| driftedProperties | [driftedProperty](https://learn.microsoft.com/en-us/graph/api/resources/driftedproperty?view=graph-rest-1.0) collection | Properties within one or more resource instances in which drift is detected.  <br>  <br>Requires `$select` to retrieve. |
| firstReportedDateTime | DateTimeOffset | The date and time at which drift is first detected. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `ge`, `le`\) and `$orderby`. |
| id | String | Globally unique identifier \(GUID\) of the drift. System-generated. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderby`. |
| monitorId | String | Globally unique identifier \(GUID\) of the monitor. System-generated.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |
| resourceInstanceIdentifier | [openComplexDictionaryType](https://learn.microsoft.com/en-us/graph/api/resources/opencomplexdictionarytype?view=graph-rest-1.0) | An identifier that allows users to understand exactly where the drift is.  <br>  <br>Requires `$select` to retrieve. |
| resourceType | String | Resource for which the drift is detected.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `startsWith`\). |
| status | driftStatus | Status of the drift. The possible values are: `active`, `fixed`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderby`. |
| tenantId | String | Globally unique identifier \(GUID\) of the tenant for which the monitor runs. Fetched automatically by the system.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.configurationDrift",
  "baselineResourceDisplayName": "String",
  "driftedProperties": [{"@odata.type": "microsoft.graph.driftedProperty"}],
  "firstReportedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "monitorId": "String",
  "resourceInstanceIdentifier": {"@odata.type": "microsoft.graph.openComplexDictionaryType"},
  "resourceType": "String",
  "status": "String",
  "tenantId": "String"
}
```
