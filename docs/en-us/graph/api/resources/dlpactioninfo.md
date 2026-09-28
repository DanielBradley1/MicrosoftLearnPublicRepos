<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# dlpActionInfo resource type

Namespace: microsoft.graph

Base type for actions defined within a Data Loss Prevention \(DLP\) rule.

Specific actions like [restrictAccessActionBase](https://learn.microsoft.com/en-us/graph/api/resources/restrictaccessactionbase?view=graph-rest-1.0) inherit from this type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.security.dlpAction | The type of DLP action. Possible value is `restrictAccessAction`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.dlpActionInfo",
  "action": "String"
}
```
