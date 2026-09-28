<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/singlevalueextendedproperty?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-29 -->

# singleValueExtendedProperty resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an extended property that contains a single value.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for a **singleValueExtendedProperty** object. For the list of permitted ID formats, see [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-beta). |
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
