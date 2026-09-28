<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-networkadapter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-05 -->

# networkAdapter resource type

Namespace: microsoft.graph.security

Represents the network adapter from which the Microsoft Defender for Identity sensor analyzes network traffic.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A unique identifier that represents the network adapter. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Indicates whether the network adapter is selected for capturing and analyzing network traffic. |
| name | String | The name of the network adapter. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.networkAdapter",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "name": "String"
}
```
