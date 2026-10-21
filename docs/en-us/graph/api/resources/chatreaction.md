<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatreaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# chatReaction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **reactions** property of the [chatMessageProperties](https://learn.microsoft.com/en-us/graph/api/resources/chatmessageproperties?view=graph-rest-beta) resource uses this type.

A reaction \(for example, an emoji\) applied by one or more users to a [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| key | String | Identifier of the reaction \(for example, an emoji key\). |
| users | [creationTimestamp](https://learn.microsoft.com/en-us/graph/api/resources/creationtimestamp?view=graph-rest-beta) collection | Users who applied the reaction, and when. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chatReaction",
  "key": "String",
  "users": [
    {
      "@odata.type": "microsoft.graph.creationTimestamp"
    }
  ]
}
```
