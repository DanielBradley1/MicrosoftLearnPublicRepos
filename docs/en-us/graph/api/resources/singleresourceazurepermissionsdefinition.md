<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/singleresourceazurepermissionsdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# singleResourceAzurePermissionsDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents permissions for an Azure resource.

Inherits from [permissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinition?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionInfo | [azurePermissionsDefinitionAction](https://learn.microsoft.com/en-us/graph/api/resources/azurepermissionsdefinitionaction?view=graph-rest-beta) | Information relating to actions defined in the permissions. |
| authorizationSystemInfo | [permissionsDefinitionAuthorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionauthorizationsystem?view=graph-rest-beta) | Information relating to permissions defined in the authorization system. Inherited from [permissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinition?view=graph-rest-beta). |
| resourceId | String | Identifier for the resource. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identityInfo | [permissionsDefinitionAuthorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionauthorizationsystemidentity?view=graph-rest-beta) | Information relating to permissions defined for identities in the authorization system. Inherited from [permissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinition?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.singleResourceAzurePermissionsDefinition",
  "authorizationSystemInfo": {
    "@odata.type": "microsoft.graph.permissionsDefinitionAuthorizationSystem"
  },
  "actionInfo": {
    "@odata.type": "microsoft.graph.azurePermissionsDefinitionAction"
  },
  "resourceId": "String"
}
```
