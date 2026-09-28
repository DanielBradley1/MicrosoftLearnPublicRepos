<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegeescalation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# privilegeEscalation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

A container for privilege escalation events.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | Edm.String | A detailed description of the privilege escalation. |
| displayName | Edm.String | The name of the policy that defines the escalation |
| id | Edm.String | the ID of the privilege escalation. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| actions | [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta) collection | The list of actions that the identity could perform. |
| resources | [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) collection | The list of resources that the identity could perform actions on. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegeEscalation",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String"
}
```
