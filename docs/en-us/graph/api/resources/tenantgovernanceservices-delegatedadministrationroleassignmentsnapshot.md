<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-delegatedadministrationroleassignmentsnapshot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# delegatedAdministrationRoleAssignmentSnapshot resource type

Namespace: microsoft.graph

Represents a snapshot of a delegated administration role assignment configuration that was captured when a [governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-1.0) or [governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) was created. This preserves the role assignment configuration as it was defined at that point in time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupDisplayName | String | The display name of the security group identified by **groupId** at the time the snapshot was created. Read-only. |
| groupId | String | The object ID of the role-assignable security group in the governing tenant that will be assigned the specified roles. |
| roleTemplates | [microsoft.graph.roleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-roletemplate?view=graph-rest-1.0) collection | The collection of role templates that define the Microsoft Entra roles to be assigned. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdministrationRoleAssignmentSnapshot",
  "groupDisplayName": "String",
  "groupId": "String",
  "roleTemplates": [
    {
      "@odata.type": "microsoft.graph.roleTemplate"
    }
  ]
}
```
