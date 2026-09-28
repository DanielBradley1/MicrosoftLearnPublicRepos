<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcauditproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# cloudPcAuditProperty resource type

Namespace: microsoft.graph

Represents the audit property. This shows the edited property name, the old value, and the new value.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name for this property. |
| newValue | String | The new value for this property. |
| oldValue | String | The old value for this property. |

## Relationships

None.

## JSON Representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAuditProperty",
  "displayName": "String",
  "newValue": "String",
  "oldValue": "String"
}
```
