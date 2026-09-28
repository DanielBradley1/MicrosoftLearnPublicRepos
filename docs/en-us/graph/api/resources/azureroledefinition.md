<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureroledefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# azureRoleDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents an Azure role in an Azure authorization system.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystem-list-roledefinitions?view=graph-rest-beta) | [azureRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/azureroledefinition?view=graph-rest-beta) collection | Get a list of the [azureRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/azureroledefinition?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/azureroledefinition-get?view=graph-rest-beta) | [azureRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/azureroledefinition?view=graph-rest-beta) | Read the properties and relationships of an [azureRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/azureroledefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignableScopes | String collection | Scopes at which the Azure role can be assigned. For more information about common patterns, see [Understand Azure role definitions: AssignableScopes](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-definitions#assignablescopes). Supports `$filter` \(`eq`\). |
| azureRoleDefinitionType | azureRoleDefinitionType | Type of Azure role. The possible values are: `system`, `custom`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| displayName | String | Name of the Azure role. Supports `$filter` \(`eq`, `contains`\). |
| externalId | String | Identifier of an Azure role defined by Microsoft Azure. Alternate key. Supports `$filter` \(`eq`\). |
| id | String | The identifier of the Azure role in Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureRoleDefinition",
  "id": "String (identifier)",
  "externalId": "String",
  "displayName": "String",
  "azureRoleDefinitionType": "String",
  "assignableScopes": [
    "String"
  ]
}
```
