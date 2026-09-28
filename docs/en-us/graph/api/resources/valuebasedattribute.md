<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/valuebasedattribute?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# valueBasedAttribute resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an attribute backed by a static value.

Inherits from [customClaimAttributeBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimattributebase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | The static value to be used an the attribute. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.valueBasedAttribute",
  "value": "String"
}
```
