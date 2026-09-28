<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcauditresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-19 -->

# cloudPcAuditResource resource type

Namespace: microsoft.graph

Represents the audit resource. This shows the target edited resource entity, with multiple edited properties.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the modified resource entity. |
| modifiedProperties | [cloudPcAuditProperty](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcauditproperty?view=graph-rest-1.0) collection | The list of modified properties. |
| resourceId | String | The unique identifier of the modified resource entity. |

## Relationships

None

## JSON Representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAuditResource",
  "displayName": "String",
  "modifiedProperties": [
    {
      "@odata.type": "microsoft.graph.cloudPcAuditProperty",
      "displayName": "String",
      "oldValue": "String",
      "newValue": "String"
    }
  ],
  "resourceId": "String"
}
```
