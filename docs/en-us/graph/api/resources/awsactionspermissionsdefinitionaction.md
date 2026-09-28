<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsactionspermissionsdefinitionaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsActionsPermissionsDefinitionAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents permissions for an AWS action.

Inherits from [awsPermissionsDefinitionAction](https://learn.microsoft.com/en-us/graph/api/resources/awspermissionsdefinitionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignToRoleId | String | Defines AWS statements. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| statements | [awsStatement](https://learn.microsoft.com/en-us/graph/api/resources/awsstatement?view=graph-rest-beta) collection | Role to assign to. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsActionsPermissionsDefinitionAction",
  "assignToRoleId": "String"
}
```
