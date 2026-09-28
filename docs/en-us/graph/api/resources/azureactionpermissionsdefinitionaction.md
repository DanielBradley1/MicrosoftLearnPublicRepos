<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureactionpermissionsdefinitionaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# azureActionPermissionsDefinitionAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents actions under Azure permissions.

Inherits from [permissionsDefinitionAction](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionaction?view=graph-rest-beta). The following resource types inherit from this resource:

- [azureActionPermissionsDefinitionAction](https://learn.microsoft.com/en-us/graph/api/resources/azureactionpermissionsdefinitionaction?view=graph-rest-beta) resource type
- [azureRolePermissionsDefinitionAction](https://learn.microsoft.com/en-us/graph/api/resources/azurerolepermissionsdefinitionaction?view=graph-rest-beta) resource type

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actions | String collection | List of actions relating to the Azure permission. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureActionPermissionsDefinitionAction",
  "actions": [
    "String"
  ]
}
```
