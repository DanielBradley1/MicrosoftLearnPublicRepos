<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-roletemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# roleTemplate resource type

Namespace: microsoft.graph

Represents a [Microsoft Entra role template definition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) used in [delegated administration role assignments](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-delegatedadministrationroleassignmentsnapshot?view=graph-rest-1.0). The role template specifies which Microsoft Entra role should be assigned.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The template ID of the Microsoft Entra role \(e.g., `62e90394-69f5-4237-9190-012177145e10` for Global Administrator\). |
| name | String | The display name of the role \(e.g., "Global Administrator", "Helpdesk Administrator"\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.roleTemplate",
  "id": "String",
  "name": "String"
}
```
