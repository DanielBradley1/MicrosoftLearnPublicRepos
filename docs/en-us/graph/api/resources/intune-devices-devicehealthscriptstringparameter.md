<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptstringparameter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceHealthScriptStringParameter resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Properties of the String script parameter.

Inherits from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the param Inherited from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) |
| description | String | The description of the param Inherited from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) |
| isRequired | Boolean | Whether the param is required Inherited from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) |
| applyDefaultValueWhenNotAssigned | Boolean | Whether Apply DefaultValue When Not Assigned Inherited from [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) |
| defaultValue | String | The default value of string param |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceHealthScriptStringParameter",
  "name": "String",
  "description": "String",
  "isRequired": true,
  "applyDefaultValueWhenNotAssigned": true,
  "defaultValue": "String"
}
```
