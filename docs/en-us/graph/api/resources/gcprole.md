<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/gcprole?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# gcpRole resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a GCP role in a GCP authorization system.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystem-list-roles?view=graph-rest-beta) | [gcpRole](https://learn.microsoft.com/en-us/graph/api/resources/gcprole?view=graph-rest-beta) collection | Get a list of the [gcpRole](https://learn.microsoft.com/en-us/graph/api/resources/gcprole?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/gcprole-get?view=graph-rest-beta) | [gcpRole](https://learn.microsoft.com/en-us/graph/api/resources/gcprole?view=graph-rest-beta) | Read the properties and relationships of a [gcpRole](https://learn.microsoft.com/en-us/graph/api/resources/gcprole?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the GCP role. Supports `$filter` and \(`eq`,`contains`\). |
| externalId | String | The ID of the GCP role as defined by GCP. Alternate key. |
| gcpRoleType | gcpRoleType | The type of GCP role. The possible values are: `system`, `custom`, `unknownFutureValue`. Supports `$filter` and \(`eq`\). |
| id | String | The ID for the GCP role in Permissions Management. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| scopes | [gcpScope](https://learn.microsoft.com/en-us/graph/api/resources/gcpscope?view=graph-rest-beta) collection | Resources that an identity assigned this GCP role can perform actions on. Supports `$filter` and \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.gcpRole",
  "id": "String (identifier)",
  "externalId": "String",
  "displayName": "String",
  "gcpRoleType": "String",
  "scopes": [
    {
      "@odata.type": "microsoft.graph.gcpScope"
    }
  ]
}
```
