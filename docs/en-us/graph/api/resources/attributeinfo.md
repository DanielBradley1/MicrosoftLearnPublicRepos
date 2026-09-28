<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attributeinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# attributeInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an attribute name-value pair used as an anchor or matching property during [identity correlation](https://learn.microsoft.com/en-us/graph/api/resources/identityinfo?view=graph-rest-beta). This object is configured in the **anchor** and **matchingProperty** properties of [identityInfo](https://learn.microsoft.com/en-us/graph/api/resources/identityinfo?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the attribute. |
| value | String | The value of the attribute. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attributeInfo",
  "name": "String",
  "value": "String"
}
```
