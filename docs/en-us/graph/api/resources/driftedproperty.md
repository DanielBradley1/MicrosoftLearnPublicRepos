<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driftedproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# driftedProperty resource type

Namespace: microsoft.graph

Represents properties of the monitored resource that drift from their [desired configuration](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0), providing details about the current and desired values to help admins resolve configuration issues. Defined in a [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0) object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| currentValue | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json?view=graph-rest-1.0) | The current value of the property. |
| desiredValue | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json?view=graph-rest-1.0) | The desired value of the property as specified by admins in the baseline of the monitor body. |
| propertyName | String | The name of the property. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driftedProperty",
  "currentValue": {"@odata.type": "microsoft.graph.Json"},
  "desiredValue": {"@odata.type": "microsoft.graph.Json"},
  "propertyName": "String"
}
```
