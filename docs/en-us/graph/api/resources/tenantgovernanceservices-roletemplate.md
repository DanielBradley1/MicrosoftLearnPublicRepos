<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-roletemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# roleTemplate resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [Microsoft Entra role template definition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) used in [delegated administration role assignments](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-delegatedadministrationroleassignmentsnapshot?view=graph-rest-beta). The role template specifies which Microsoft Entra role should be assigned.

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
