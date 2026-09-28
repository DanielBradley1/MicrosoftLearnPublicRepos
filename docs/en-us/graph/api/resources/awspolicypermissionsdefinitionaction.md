<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awspolicypermissionsdefinitionaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsPolicyPermissionsDefinitionAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents permissions for an AWS policy.

Inherits from [awsPermissionsDefinitionAction](https://learn.microsoft.com/en-us/graph/api/resources/awspermissionsdefinitionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignToRoleId | String | ID for the role. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policies | [permissionsDefinitionAwsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionawspolicy?view=graph-rest-beta) collection | Permissions defined in the AWS policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsPolicyPermissionsDefinitionAction",
  "assignToRoleId": "String"
}
```
