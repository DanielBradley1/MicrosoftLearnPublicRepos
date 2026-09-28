<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerarchivalinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-03 -->

# plannerArchivalInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the identity of the user or app who archived or unarchived a [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta), [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta) or [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-beta) and why. Properties of **plannerArchivalInfo** are only set when a plan is [archived](https://learn.microsoft.com/en-us/graph/api/plannerplan-archive?view=graph-rest-beta) or [unarchived](https://learn.microsoft.com/en-us/graph/api/plannerplan-unarchive?view=graph-rest-beta).

An archived entity is read-only.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| justification | String | Read-only. Reason why the entity was archived or unarchived. |
| statusChangedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Read-only. Identity of the user who archived or unarchived the entity |
| statusChangedDateTime | DateTimeOffset | Read-only. Date and time at which the entity's archive status changed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerArchivalInfo",
  "justification": "String",
  "statusChangedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "statusChangedDateTime": "String (timestamp)"
}
```
