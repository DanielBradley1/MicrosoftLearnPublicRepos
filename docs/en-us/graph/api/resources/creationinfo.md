<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/creationinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# creationInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **creationInfo** property of the [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) resource uses this type. The **creationInfo** property of the [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) resource uses this type. The **creationInfo** property of the [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) resource uses this type. The **creationInfo** property of the [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) resource uses this type.

Read-only creation metadata for a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta), [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta), [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta), or [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) that created the entity. |
| createdDateTime | DateTimeOffset | Date and time the entity was created. |
| externalId | String | Identifier of the entity in an external system, if it originated outside Planner. |
| externalUrl | String | URL of the entity in the external system, if applicable. |
| externalVersion | String | Version of the entity in the external system, if applicable. |
| scenarioId | String | Identifier of the scenario or workflow that created the entity. |
| scope | String | Scope the entity was created in. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.creationInfo",
  "scenarioId": "String",
  "scope": "String",
  "externalId": "String",
  "externalVersion": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "externalUrl": "String"
}
```
