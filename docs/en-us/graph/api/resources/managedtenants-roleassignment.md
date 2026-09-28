<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-roleassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-16 -->

# roleAssignment resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the role assignment to a signed-in user for a [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentType | delegatedPrivilegeStatus | The type of the admin relationship\(s\) associated with the role assignment. The possible values are: `none`, `delegatedAdminPrivileges`, `unknownFutureValue`, `granularDelegatedAdminPrivileges`, `delegatedAndGranularDelegetedAdminPrivileges`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `granularDelegatedAdminPrivileges` , `delegatedAndGranularDelegetedAdminPrivileges`. |
| roles | [microsoft.graph.managedTenants.roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-roledefinition?view=graph-rest-beta) collection | The collection of roles assigned. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.roleAssignment",
  "assignmentType": "String",
  "roles": [
    {
      "@odata.type": "microsoft.graph.managedTenants.roleDefinition"
    }
  ]
}
```
