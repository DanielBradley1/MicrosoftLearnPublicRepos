<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

An abstract type that represents information about the permissions request, such as the authorization system, the identities making the request, and the actions for which the identities need the permissions.

This resource type is inherited by the following objects:

- [awsPermissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/awspermissionsdefinition?view=graph-rest-beta) resource type
- [singleResourceAzurePermissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/singleresourceazurepermissionsdefinition?view=graph-rest-beta) resource type
- [singleResourceGcpPermissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/singleresourcegcppermissionsdefinition?view=graph-rest-beta) resource type

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authorizationSystemInfo | [permissionsDefinitionAuthorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionauthorizationsystem?view=graph-rest-beta) | Information relating to the authorization system and permissions assigned. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identityInfo | [permissionsDefinitionAuthorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionauthorizationsystemidentity?view=graph-rest-beta) | The identity receiving the actionInfo. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsDefinition",
  "authorizationSystemInfo": {
    "@odata.type": "microsoft.graph.permissionsDefinitionAuthorizationSystem"
  }
}
```
