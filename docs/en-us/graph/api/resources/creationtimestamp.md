<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/creationtimestamp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# creationTimestamp resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **users** property of the [chatReaction](https://learn.microsoft.com/en-us/graph/api/resources/chatreaction?view=graph-rest-beta) resource uses this type.

Identifies who performed an action and when, reused across Planner V4 types that need a lightweight actor-plus-timestamp pair \(for example, a [chatReaction](https://learn.microsoft.com/en-us/graph/api/resources/chatreaction?view=graph-rest-beta) author\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) associated with the action. |
| createdDateTime | DateTimeOffset | Date and time the action occurred. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.creationTimestamp",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)"
}
```
