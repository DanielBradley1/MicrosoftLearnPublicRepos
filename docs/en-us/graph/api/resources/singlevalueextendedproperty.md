<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/singlevalueextendedproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# singleValueExtendedProperty resource type

Namespace: microsoft.graph

Represents an extended property that contains a single value.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for a **singleValueExtendedProperty** object. For the list of permitted ID formats, see [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0). |
| value | String | The value of the property. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.singleValueExtendedProperty",
  "id": "String (identifier)",
  "value": "String"
}
```
