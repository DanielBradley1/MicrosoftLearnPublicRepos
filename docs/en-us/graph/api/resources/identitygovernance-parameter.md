<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-parameter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# parameter resource type

Namespace: microsoft.graph.identityGovernance

Represents the allowed arguments that are defined in the **parameters** property of the [taskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) resource for built-in lifecycle workflow tasks.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the parameter. |
| values | String collection | The values of the parameter. |
| valueType | microsoft.graph.identityGovernance.valueType | The value type of the parameter. The possible values are: `enum`, `string`, `int`, `bool`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.parameter",
  "name": "String",
  "values": [
    "String"
  ],
  "valueType": "String"
}
```
