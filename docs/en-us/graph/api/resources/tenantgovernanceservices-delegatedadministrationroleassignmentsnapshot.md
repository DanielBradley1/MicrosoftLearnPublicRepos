<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-delegatedadministrationroleassignmentsnapshot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# delegatedAdministrationRoleAssignmentSnapshot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a snapshot of a delegated administration role assignment configuration that was captured when a [governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-beta) or [governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) was created. This preserves the role assignment configuration as it was defined at that point in time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupDisplayName | String | The display name of the security group identified by **groupId** at the time the snapshot was created. Read-only. |
| groupId | String | The object ID of the role-assignable security group in the governing tenant that will be assigned the specified roles. |
| roleTemplates | [microsoft.graph.roleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-roletemplate?view=graph-rest-beta) collection | The collection of role templates that define the Microsoft Entra roles to be assigned. |

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
