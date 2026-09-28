<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awspermissionsdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsPermissionsDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

AWS-specific permissions request details.

Inherits from [permissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinition?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionInfo | [awsPermissionsDefinitionAction](https://learn.microsoft.com/en-us/graph/api/resources/awspermissionsdefinitionaction?view=graph-rest-beta) | The actions the identity will have as part of the permission. |
| authorizationSystemInfo | [permissionsDefinitionAuthorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionauthorizationsystem?view=graph-rest-beta) | Information about the authorization system to assign permissions on. Inherited from [permissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinition?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identityInfo | [permissionsDefinitionAuthorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionauthorizationsystemidentity?view=graph-rest-beta) | The identity that's requesting permissions, either directly or indirectly. Inherited from [microsoft.graph.permissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinition?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsPermissionsDefinition",
  "authorizationSystemInfo": {
    "@odata.type": "microsoft.graph.permissionsDefinitionAuthorizationSystem"
  },
  "actionInfo": {
    "@odata.type": "microsoft.graph.awsPermissionsDefinitionAction"
  }
}
```
