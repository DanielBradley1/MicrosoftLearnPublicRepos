<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/baselineparameter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# baselineParameter resource type

Namespace: microsoft.graph

Represents the information and properties of a [baselineParameter](https://learn.microsoft.com/en-us/graph/api/resources/baselineparameter?view=graph-rest-1.0) object.

Parameterization is the practice of abstracting tenant-specific values into parameters that are provided during tenant monitoring. Using parameters in a [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) allows administrators to create one baseline object that can be used to monitor multiple tenants.

Users are responsible for parameterizing their **configurationBaseline** objects if they want to use the baseline on multiple tenants. They must also define the necessary parameters themselves. Multiple parameters can be defined in a **configurationBaseline**. However, if baseline parameters aren't used within the **configurationBaseline**, those parameters are considered invalid, and users should avoid defining unused parameters.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | User-friendly description of the parameter. |
| displayName | String | Parameter names such as `FQDN` and `Tenant ID`. |
| parameterType | baselineParameterType | The type of the **baselineParameter**. The possible values are: `string`, `integer`, `boolean`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.baselineParameter",
  "description": "String",
  "displayName": "String",
  "parameterType": "String"
}
```
