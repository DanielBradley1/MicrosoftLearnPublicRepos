<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrole?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# unifiedRole resource type

Namespace: microsoft.graph

The directory roles that can be assigned to a Microsoft partner through a delegated admin relationship.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| roleDefinitionId | String | The unified role definition ID of the directory role. Refer to [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) resource. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRole",
  "roleDefinitionId": "String"
}
```
