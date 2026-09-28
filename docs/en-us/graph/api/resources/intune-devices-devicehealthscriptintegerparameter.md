<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptintegerparameter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceHealthScriptIntegerParameter resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Properties of the Integer script parameter.

Inherits from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the param Inherited from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) |
| description | String | The description of the param Inherited from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) |
| isRequired | Boolean | Whether the param is required Inherited from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) |
| applyDefaultValueWhenNotAssigned | Boolean | Whether Apply DefaultValue When Not Assigned Inherited from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) |
| defaultValue | Int32 | The default value of Integer param. Valid values -2147483648 to 2147483647 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceHealthScriptIntegerParameter",
  "name": "String",
  "description": "String",
  "isRequired": true,
  "applyDefaultValueWhenNotAssigned": true,
  "defaultValue": 1024
}
```
